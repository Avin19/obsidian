#Coroutines #asynchronous #yield 

In Unity, a Coroutine is a [[method]] used to execute code over a period of [[Time]], allowing for [[asynchronous]] operations, [[delays]], and behavior that spans multiple frames. Coroutines are especially useful for scenarios where you want to control the flow of execution without blocking the main game loop, like waiting for [[events]], time actions, or sequences tat should run alongside the game.


# Basic Structure of a Coroutine

A Coroutine is declared as a [[method]] that returns [[IEnumerator]] . within the Coroutine, the [[yield]] statement is used to pause the execution of the [[method]] at certain points.
```Csharp 
	public class CoroutineExample : MonoBehaviour {
	void Start() {
		StartCoroutine(MyCoroutine());
	}
	IEnumerator MyCoroutine() {
		Debug.Log("Coroutine started!");
		// Wait for 2 seconds
		yield retrun new WaitForSeconfds(2f);
		Debug.Log(" 2 seconds later ...");
		// wait for the end of the current frame
		yield retrun null;
		debug.Log("End of frame.");
	}
}
```

# Key Concpets:
- [[StartCoroutine()]] : This function is used to start a Coroutine. You cannot call Coroutines like [[method]]; they need to be initiated using `StartCoroutine()`.
- [[IEnumerator]] : Coroutine return `IEnumerator` , which allows the [[method]] to be paused at certain points using [[yield]] statements.
- [[yield]] return: Pauses the Coroutine at that points and waits for the specified condition (e.g., [[Time]] [[delays]],  next frame, etc.) before resuming.



# Stopping a Coroutine
Coroutines can be stopped before they finish execution using `StopCoroutine()` , or globally stopped using `StopAllCoroutines()`.

```Csharp
public class CoroutineStopExample : MonoBehaviour {
[SerializeField] private Coroutine myCoroutine;

	void Start() {
		myCoroutine = StartCoroutine(MyCorotine());
	}
	IEnumerator MyCoroutine() {
		while(true) {
			Debug.Log("Running ...");
			yield return new WaitForSeconds(1f);
		}
	}
void Update() {
	if(InPut.GetKeyDown(KeyCode.S)) {
		StopCoroutine(myCoroutine); // stops the specific Coroutine
		Debug.Log("Coroutine stopped.");
		
	}
  }
}
```
# Use Cases for Coroutines
- 1. Timed Events :  Performing actions after a delay ( e.g., reloading a weapon, spawning enemies after a countdown).
```csharp
IEnumerator ReloadWeapon() {
Debug.Log(" Reloading ... " );
yield return new WaitForSeconds(2f);
// wait 2 seconds to simulate reload time
Debug.Log("Weapon reload. " );
}
```
- 2. Sequencing Events: Running a series of actions in a timed sequence.
```Csharp 
IEnumerator EventSequence() {
	Debug.lgo(" Start of sequence. ");
	yield return new WaitForSeconds(1f);
	Debug.Log("1 Second Passed. " );
	yield return new WaitForSeconds(2f);
	Debug.Log("3 Seconds passed ");
}
```
- 3 Smooth Transitions : Gradually Changing a value over time (e.g., fading out a UI element, moving an Object smoothly).
```Csharp
IEnumeratpr FadeOut(CanvasGroup canvasGroup, float duration) {
float startAlpha = canvasGroup.alpha;
for( float t =0 ; t< duration; t+= Time.deltaTime) {
	canvasGroup.alpha = Mathf.Lerp(startAlpha, 0, t/ duration);
	yield return null; 
	// Wait for the next frame
}
canvasGroup.aplha = 0;
}
```
* 4. Loading Scenes: Running a loading screen while waiting for another scene to load.
```Csharp
IEnumerator LoadSceneAsync(string sceneName) {
 AsyncOperation asyncLoad = SceneManager.LoadSceneAsync(sceneName);
 while (!asyncLoad.IsDone)
 {
	 yield return null; 
	 //wait untill the next frame
 }
 Debug.Log("Scene loaded.");
}
```