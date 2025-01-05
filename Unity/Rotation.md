#Rotation #Transform  #EulerAngle

There are several [[method]]s to rotate a [[GameObjects]] int Unity, depending on whether you want to rotate it based on[[physics]], direct manipulation of the [[Transform]], or through [[interpolating]].

Here's an overview of all the possible ways to rotate a [[GameObjects]] :

# 1 Transform .Rotate()  
#Transform #Rotate
The most straight forward [[method]], this rotates the [[GameObjects]] around an [[axis]] by a specified [[angles]].

```csharp 
private float rotationSpeed = 100.0f;

void Update() 
{
	transfrom.Rotate( Vector3.up, rotationSpeed * Time.deltaTime) ;
}
```
Notes: 
- This rotates the object relative to its local coordinate system by default.
- To rotate in world space, you can specify the `Space.World` parameter.
```Csharp
transform.Rotate(Vector3.up, rotationSpeed * Time.deltaTime, Space.World);
```

## 2 . Setting Euler Angles ( transform.eulerAngles)
#EulerAngle #euler 

Euler angles allow you to set the rotation along the X,Y, and X axes directly. This method gives full control over rotation but can lead to[[ gimble lock]] if not used carefully. 

```Csharp 
float roationSpeed = 50.0f;
void Update () {
	Vector3 currentRotation = transform.eulerAngles;
	currentRotation.y += rotationSpeed * Time.deltaTime;
	transfrom.eulerAngles = currentRotation;
	
}
```
Notes: Euler angles are represented in degrees, and changing them directly can cause unexpected behavior due to the way rotations are interpolated (e.g., gimbal lock ).

## 3. Quaternion Rotation ( transform.rotation)
#Quaternion 
Unity internally uses [[quaternions]] for rotation because they avoid gimbal lock and interpolate smoothly. [[quaternions]] rotation in 3D space.

```Csharp
void Update() {
Quaternion targetRotation = Quaternion.Euler(0, 90, 0);
// Rotates 90 degree around y azis 
transfrom.rotation = targetRotation;
}
```
*  <b> Quaternion.RotateTowards() </b>
	This rotates one quaternion towards another at a fixed speed. 
```csharp 
private float rotationSpeed = 100.0f;

void Update() { 
	Quaternion targetRotation = Quaternion.Euler(0,90,0);
	transfrom.rotation = Quaternion.RotateTowards( transfrom.rotation, targetRotation, rotationSpeed * Time.deltaTime);
}

```
* <b> Quaternion.Slerp() </b>

	#Slerp  
	
	Slerp( Spherical Linear Interpolation) provides smooth rotation between two quaternions, useful for gradually rotating an [[GameObjects]].
```Csharp
private float rotationSpeed = 0.1f;

void Update()
{
	Quaternion targetRotation = Quaternion.Euler(0,90,0);
	transfrom.rotation = Quaternion.Slerp(transfrom.rotation ,targetRotation, rotationSpeed);
}
```
Notes: Slerp is often used in [[camera]] movement and smooth transitions for [[GameObjects]] rotations.

## 4. RigidBody-Based Rotation 

#Rigidbody 
if you are working with [[physics]]-based [[GameObjects]], you should rotate the [[GameObjects]] using a [[Rigidbody]]. 
Here are two common ways to rotate physic objects. 

*  <b> a. Rigidbody.AddTorque() </b>
	This method adds torque (rotational force) to a [[GameObjects]], causing it to rotate physically.
```csharp
Rigidbody rb;

void Start()  {
rb = getComponent<Rigidbody>();
}

void FixedUpdaet() {
 float torque = 10.0f;
 rb.AddTorque( Vector3.up * torque);
}
```

Notes: This works well for physical simulation like rotating wheels or spinning objects in a physica-based environment.

<b> b. Rigidbody.MoveRotation() </b>
Moves the `Rigidbody` to a new rotation while maintaining [[Collision]] physics. Use this when you want to directly control the rotation without using torque.
```Csharp
Rigidbody rb;
private float rotationSpeed = 100.0f;
void Start() {
rb = GetComponent<Rigidbody>();
}

void FixedUpdate() {
Quaternion deltaRotation = Quaternion.Euler( new Vector3(0, rotationSpeed *Time.fixedDeltaTime , 0));
rb.MoveRotation(rb.rotation* deltaRotation);
}
```

*  Notes: This is similar to `transform.rotation`, but it respects physics and ensures smooth rotation for rigidbodies.
## 5. LookAt()
#LookAT
This method rotates the[[GameObjects]] so that it faces a target point or another [[Object]].
*  Example:
```Csharp
public Transfrom target;

void Update() {
	 transfrom.LookAt(target);
}
```
* Notes: `LookAt()` is typically used for rotating character, [[camera]], or turrets to face another [[GameObjects]]. It aligns the [[GameObjects]] forward direction to the target.
- <b> LookAt with Axis Constraint </b>
If you want the [[Object]] to rotate only around a certain axis (e.g., Y-axis), you can constrain the axis:
```Csharp 
void Update() {
 Vector3 targetPosition = new Vector3(target.position.x, transform.position.y, transform.position.z );
 
}
```
## 6. Rotating with Mathf.LerpAngle()
#Mathf #Lerp 

This method linearly between two angles and is great for smooth rotation transitions.
```Csharp 
public float tragetAngle = 90.0f;


void Update() {
 float rotationSpeed = 50.0f;
 float currentAngle = transfrom.eulerAngles.y;
 float newAngle = Mathf.LerpAngle(currentAngle, targetAngle, rotationSpeed*Time.deltaTime);
 tarnsfrom.eulerAngles = new Vector3(0, newAngles , 0);
}
```
Notes : `Mathf.LerpAngle()` smoothly interpolates between two angles, which is helpful when dealing with rotations that wrap around (e.g., 350 degrees to 10 degrees).

## 7. Tweening (Using DOTween or iTween)

[[Tweening]] libraries like DOTween or iTween allow for more control over rotations with smooth transitions, ease functions, and timing.

<b> a. DOTween Example (Requires installing DOTween) </b>
```Csharp 
void Start() {
 transfrom.DORotate(new Vector3(0 ,90,0 ), 2.0f); 
 // Rotated to 90 degrees around Y -axis in 2 seconds 
}
```
<b> b. iTween Example ( Another tweening library) </b>
```Csharp
void Start() {
iTween.Rotate(gameObject, new Vector3(0,90,0), 2.0f);
// Rotates to 90 degree around y-axis in 2 second
}
```
- Notes: Tweening libraries allowing for smooth and highly customizable [[animations]], including rotation with ease-in and ease-out effects.
## 8. Coroutines for Smooth Rotations

You can rotate a [[GameObjects]] smoothly over time using a coroutine.
```Csharp
float elapsedTime = 0f;

IEnumerator RotateOverTime(Quaternion targetRotation, float duration)  {

	Quaternion startRotation = transform.rotation;
	while(elapsedTime < duration) {
	transfomr.rotation = Quaternion.Slerp(startRotation , targetRotation , elapsedTime/ duration);
	elapsedTime += Time.deltaTime;
	yield retrun null;
	// Wait for the next frame
	}
	transfrom.rotation = targetRotation;
	//Ensure final rotation is set
}
void Start()   {
	Quaternion targetRotation = Quaternion.Euler(0 ,90 ,0 );
	StartCoroutine( RotateOverTime(targetRotation, 3.0f)); 
	// Rotates to 90 degree over 3 seconds 
}
```

- Notes: [[Coroutines]] provide fine control over how the rotation proceeds, slowing for smooth, time-based transitions.
## 9. Animating Rotation Using Animator

#Animator 

You can create and control rotation animations through Unity's Animator system.
	- Example:
		- 1. Create a rotation animation in the Unity Animation window.
		- 2. Control the animation <b> state </b> using the  `Animator` component.
```Csharp
Animator animator;

void Start()  {
	animator = GetComponent<Animator>();
}

void Update()  {

	if(Input.GetKeyDown(KeyCode.Space))  {
		animator.SetTrigger("Rotate");
	}
}
```
Notes: This is useful when you need pre-defined animations for complex or precise rotational movements.

## 10. Mouse-Based Rotation ( for Cameras and Objects )

#Camera

Mouse input can be used to control rotation ( common in first-person or third-person camera controllers. )

- Example :
```Csharp 
[SerializeField] private float sensitiveity =100f
[SerializeField] private float rotationY = 0f;


void Update()  {
float mouseX = Input.GetAxis("Mouse X") * sensitivity * Time.deltaTime;
rotationY += mouseX;

transfrom.localEulerAngles = new Vector3 (0, rotationY , 0); 

}
```