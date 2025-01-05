#Awake 
In Unity, the `Awake()` method is one of the built-in [[MonoBehaviour]] lifecycle [[method]] . It is called the [[script]] instance is being loaded, which is typically when the [[GameObjects]] containing the [[script]] in instantiated or enabled.

# Key Points about Awake() :

- #### 1. When Is it Called?
	-  `Awake()` is called before any `Start()` method or any other [[script]]'s `Awake()` [[method]].
	- It's called <b> once</b> in the lifecycle of a [[GameObjects]], typically when the [[Object]] is first created or when the scene is loaded.
- ### 2. Usage:
	-  `Awake()` is often used to initialize [[Variable]] or set up references that are required for the [[script]] to work properly.
	- It's useful for setup that should occur <b> even if the script is disabled </b>, as it still get called when the object is instantiated.
	- Unlike [[Start()]] , [[Awake()]] runs even if the [[script]] component is initially disabled, which makes it ideal for initialization that doesn't depend on the [[Object]] being active.
- #### 3. Difference from `Start()` :
	- Both `Awake()` and `Start()` are initialization [[method]]s, but `Awake()` is called first, while `Start()` is called only if the [[script]] is enabled, and after `Awake()` has been executed.
	- `Awake()` is mainly used for setups that other components might depend on, while `Start()` is used for logic that can wait until all `Awake()` calls have been made.
- ### 4. Order of Execution:
	- If multiple scripts on different [[GameObjects]] have `Awake()`, their execution order is not guaranteed. However, within the same [[Object]]s , components follow their [[script]] execution order.
```Csharp

public class Player : MonoBehaviour
{
	public int health;

	void Awake()
	{
		// Initialize the player's health when the GaemObject is instantiated
		helth = 100;
		Debug.Log(" Awake called. Player health initialized. " );
	
	}
	void Start() {
		// Further initialization that depends on all objects being setup 
		Debug.Log("Start called");

	}
}
```
In this example: 
	- `Awake()` is initializing the player's health right right when the [[GameObjects]] is created, regardless of whether the script is enabled or not.
	- `Start()` would then handle anything else after all [[Object]]s have been initialized.
### When to Use `Awake()` : 
*  Use `Awake()` when you need to set up essential references or initialize data that other [[script]]s might depend on early in the game's lifecycle.
* For more complex dependencies between [[Object]]s, where initialization order matters, consider `Awake()` for low-level setup and ` Start()` for gameplay-related logic.