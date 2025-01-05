- <b> Purpose : </b>
	- The `OnEnable()` method is called when the object ( or the [[script]] component) is <b> enabled </b>. This can happen when:
		- The [[GameObjects]] is first instantiated and is enabled.
		- The [[GameObjects]] is  re-enabled after being disabled.
		- The [[script]] component itself is enabled after being disabled.
- <b> Use Cases : </b>
	- Initializing or resetting certain variables or subscribing to [[Events]].
	- Restarting timers, [[Coroutines]], or other behaviors when the [[Object]] or [[script]] becomes active again.
	- Useful when you want to execute code every time the [[Object]] is enabled, even if it happens multiple times during the [[Object]]'s lifecycle.
```Csharp.
public class ExampleScript : MonoBehaviour {
		void OnEnable() {
		Debug.Log(" Object or script is enabled. " );
		// Subscribe to events, start actions
	}
		void OnDisable(){
			Debug.Log("Object or script is disabled.");
			//Unscribe from events or stop actions
		}
}
```
- <b> Key Notes on OnEnable()</b>
	- It can be called Multiple times in the [[Object]]'s lifecycle if the [[Object]] or [[script]] is repeatedly enabled/ disabled.
	- It runs before [[Start()]] ,  so if you need something to initialize before [[Start()]], OnEnable() can be a good place for that.
	- Paired with [[OnDisable()]] to handle the reverse logic when the object is disabled ( e.g., unsubscribing from [[Events]] or stopping [[Coroutines]]).
	