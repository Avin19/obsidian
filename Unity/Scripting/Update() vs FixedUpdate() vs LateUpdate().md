#FixedUpdate #LateUpdate  #Update 
# Comparison Table : Update() vs FixedUpdate() vs LateUpdate()

| Aspect                    | Update()                                                          | FixedUpdate()                                               | LateUpdate()                                                                |
| ------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------- | --------------------------------------------------------------------------- |
| Timing                    | Called once per frame ( frame-rate dependent).                    | Called at fixed intervals ([[physics]] time step).          | Called once per frame, after all [[Update()]] methods.                      |
| Primary Use               | Non-[[physics]] updates: [[input]] handling, [[animations]], etc. | Physics Updates: applying forces, velocity , [[Collision]]. | [[camera]] following, [[Post-processing]], dependent updates.               |
| Best for                  | frame-dependent game logic and [[user interaction]].              | Consistent [[physics]] calculation and [[movement]].        | Actions that rely on the final state of [[GameObjects]] (e.g., [[camera]]). |
| Frame- rate independent ? | No, varies with frame rate.                                       | yes, runs on fixed time intervals.                          | No, but runs after [[Update()]] for dependent actions.                      |
| Common Example            | Player [[movement]], firing, UI updates.                          | Physics-based [[movement]] [[Collision]] detection.         | [[camera]] following [[animations]] adjustments.                            |
```Csharp
public class PlayerController : Monobehaviour {
	[SerializeField] private Transfrom cameraTransfrom;
	[SerializeField] private Rigidbody rb ;

	void Start(){
	rb = GetComponent<Rigidbody>();
	}
	void Update() {
	// handle input , e.g. , jumping
		if(Input.GetKeyDown(KeyCode.Space)) {
			Debug.Log("Jump!");
		}
	}
	void FixedUpdate() {
	// Hanlde physics-based movement
	float move =Input.GetAxis("Vertical");
	rb.AddForce(Vector3.forward * move * 10f);
	}
	void LateUpdate() {
	// Camera follows the player
	cameraTransfomr.position = transfrom.position + new Vector3(0,5,-10);
	}
}
```
In this example :
*  [[Update()]] is used to check for player [[input]] (e.g., pressing the spacebar).
* [[FixedUpdate()]] is used to apply forces to the player's [[Rigidbody]] for physics based [[movement]].
* [[LateUpdate()]] is used to update the [[camera]]'s position after the player's [[movement]] has been processed.
