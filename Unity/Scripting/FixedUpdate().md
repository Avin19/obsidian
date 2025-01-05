#FixedUpdate #Update 
-  <b> Purpose </b> :
	- `FixedUpdate()` is called at <b> fixed time intervals </b> , making it ideal for handling physics-related calculations and movement. It is often used with Unity's [[physics]] system ([[Rigidbody]], [[forces]], [[Collision]] detection).
- <b> Characteristices : </b>
	- Called at <b> fixed intervals </b> ( independent of the frame rate), usually around every 0.02 seconds by default.
	- Consistent in terms of time steps, which makes it perfect for [[physics]] calculations.
	- Any [[physics]]-related functions (like [[Rigidbody]] manipulations ) should be handled here.
* <b> Use Cases : </b>
		- [[physics]]-based [[movement]] and [[force]] (e.g., [[Rigidbody]] velocity and force).
		- Handling [[physics]]-based [[Collision]], impulses, or gravity.
		- Simulating consistent behavior when using [[physics]] regardless of the game's frame rate.
```Csharp
void FixedUpdate(){
	Rigidbody rb = GetComponent<Rigidbody>();
	float move = Input.GetAxis("Vertical");
	rb.AddForce(Vector3.forward * move);
}
```
In this example, forces are applied to a [[Rigidbody]] in `FixedUpdate()` , ensuring that the [[physics]] interactions remain smooth and consistent, regardless of frame rate.
