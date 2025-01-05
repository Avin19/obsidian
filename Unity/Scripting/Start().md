- <b> Purpose </b> :
	- The `Start()` methods is called once when the script is first enabled. It runs before the first frame [[Update()]], but only after [[Awake()]] methods have been called and the scene has been loaded.
- <b> Use Cases : </b>
	- One-time initialization that only needs to happen at the beginning of the [[Object]]'s lifecycle.
	- Loading data, setting up reference, or starting behaviors that are needed once the script is fully initialized. 
	- Typically used for game logic initialization that happens right after the scene has loaded and the object is ready to act.
```Csharp
public class ExampleScript : MonoBehaviour {
	void Start() {
		debug.Log("Start method called once when the object is initialized.");
		// one-time initialization
		}
	void update() {
	 // This is called every frame after Start()
	}
}
```
- <b> Key Notes on </b> `Start()` :
	- It is only called once per [[script]], even if the [[GameObjects]] is disabled and re-enabled later.
	- If a [[GameObjects]] is instantiated in the middle of the game, `Start()` will be called immediately after it is instantiated and enabled.
	- `Start()` is typically used for initial setup that does not need to be repeated when the [[Object]] is disabled and re-enabled.