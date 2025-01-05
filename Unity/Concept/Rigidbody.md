#Rigidbody 
In Unity, the` Rigidbody` component is used to give physical behavior to [[GameObjects]], enabling them to interact with forces such as gravity and [[Collision]] detection. It is essential for creating realistic [[physics]]-based behavior, such as[[GameObjects]] falling, moving, or colliding with other [[GameObjects]].

## Key Features of `Rigidbody` :
 * <b> 1. Physics Simulation : </b> A [[GameObjects]] with a `Rigidbody` will be affected by [[physics]], meaning it can move, rotate, and respond to forces such as gravity, impulses, and [[Collision]].
 *  <b> 2. Forces and Impulses : </b> You can apply forces to [[GameObjects]]s with Rigidbody,  which simulates realistic physical behavior.
 *  <b> 3. Collision Detection </b> : [[Rigidbody]] works with [[colliders]] between [[GameObjects]] in the scene. Without a Rigidbody, [[Collision]] detection is limited or disabled.
## Common Properties :
* <b> 1. Mass: </b>  Represents the mass of the [[GameObjects]] in kilograms. It influences how much force is needed to move it.
* <b> 2. Drag: </b> Controls how much resistance the object faces when moving. A higher drag makes the [[GameObjects]] slow down faster.
* <b> 3.  Angular Drag </b> : Similar to drag, but affects the object's rotational motion.
* <b> 4. Gravity </b>: by default, a Rigidbody is affected by gravity (`useGravity` property). You can toggle gravity on or off.
* <b> 5. Is Kinematic </b> When set to true, the [[GameObjects]] is no longer affected by [[physics]] forces, [[Collision]]s or gravity, but can still be moved and rotated using [[script]] Useful for [[GameObjects]] that you want to move manually or with [[animations]], but not [[physics]] forces.
* <b> 6. Interpolate : </b> Smooths the [[GameObjects]]'s [[movement]] by [[interpolating ]] between [[physics]] Updates. this can help reduce jittering during [[motion]], particularly at low frame rates.
* <b> 7. Collision Detection : </b> Controls how [[Collision]] are detected. Option include :
	* <b> Discreate (default) :</b> Best for Objects that are not moving too fast.
	* <b>Continuous :</b> For fast-moving objects to prevent them form "[[tunneling]]" through other objects without detecting a [[Collision]].
## Methods to Manipulate a Rigidbody:
* #### 1. AddForce(Vector3 force, ForceMode mode):   
	* Adds a force to the Rigidbody, simulating the effect of an external force pushing pr pulling the object.
		*  ` ForceMode` options:
			* <b> Force : </b> Applies a continuous force over time
			*  Impulse : Applies an instantaneous force.
			*  VelocityChange: Changes the velocity directly without considering mass.
```Csharp
Rigidbody rb = GetComponent<Rigidbody>();
rb.AddForce(vector3.up *10 , ForceMode.Impulse); // Launches object upwards with a quick impulse
```
* #### 2. AddTorque( Vector3 torque, ForceMode mode): 
	*  Applies rotational force to the Rigidbody, causing it to rotate.
* #### 3. MovePosition (Vector3 position):  
	* Moves the Rigidbody to new position. This is useful for character controllers or when you want to directly control position without physics forces.
* #### 4. MoveRotation( [[Quaternion]] rotation) : 
	*  Rotates the Rigidbody to new rotation.
* #### 5. Velocity and Angular Velocity:
	* You can directly modify the velocity and angular velocity of a Rigidbody for more direct control.
```Csharp
rb.velocity = new vector3(5,0,0); // sets the objects's velocity to move along the x axis
```
### Example Use Cases:
Let's say you want to apply a force to a Rigidbody when pressing a key to simulate jumping:
```csharp
public class PlayerJump : MonoBehaviour
{
	[SerializeField] private Rigidbody rb;
	public float jumpForce = 5f;

	void Start()
	{
		rb = GetComponent<RigidBody>();
	}
	void Update()
	{
		if(Input.GetKeyDown(KeyCode.Space))
		{
		rb.AddForce(Vector3.up * jumpForce, ForceMode.Impulse);
		}
	}
}
```
In this example:
	* The Rigidbody is retrieved using`GetComponent<Rigidbody>() .
	* When the spacebar is pressed, a force is applied upwards using `AddForce` , causing the [[GameObjects]] to jump.
### Rigidbody Types:
#### 1. Dynamic : 
Default mode where the object is fully simulated by Unity's [[physics]] engine. It responds to gravity, forces, and [[Collision]].
### 2. Kinematic: 
Used when you want to control the object via [[script]] without being affected by [[physics]] . It will interact with dynamics objects in [[collisions]] but won't respond to forces or gravity.
#### 3. Static : 
[[GameObjects]] without [[Rigidbody]] are considered static. These objects are not moved by [[physics]] and are ideal for stationary objects like walls or the ground.

## Common Rigidbody Usage Scenarios :
* Player Movement: For player-controlled characters that interact with [[physics]] (e.g., jumping, falling).
* Projectiles : [[Rigidbody]] is ideal for [[GameObjects]] like bullets, arrows, or thrown items.
* Physics-Based Puzzles: Simulating objects like rolling balls, levers, or destructible environments.
 