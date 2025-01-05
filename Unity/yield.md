#yield

# Types of Yield Statements

- 1. `yield return new WaitForSeconds(time)` : Pauses the Coroutine for a set number of seconds. 
```Csharp
IEnumerator WaitExample() {
	yield return new WaitForSeconds(3f);
	// Waits for 3 seconds
	Debug.Log(" 3 seconds later ...");
}
```
- 2. ` yield return null` : Pauses the [[Coroutines]] until the next frame.
```Csharp
IEnumerator WaitNextFrame() {
 yield return null ; // Waits untill the next frame
debug.Log(" Resuming in the next frame ...");
}
```
- 3.  `yield return new WaitForEndOfframe() `: Waits until the end of the current frame before continuing.
```Csharp
Ienumerator EndOfFrameExample() {
yield return new WaitForEndOfFrame();
// Waits untill  the end of the frame
Debug.Log("End of the frame reached.");
}
```
* 4. `yield retrun new WaitUntil(condition)` : waits until a specific condition becomes true before continuing.
```Csharp
IEnumerator WaitUntilExample() {
yield retrun new waitUnitl( () => Time.time >5f); // Waits unitl the game's time exceeds 5 seconds
Debug.Log(" Time is greate than 5 second ");

}
```
* 5 `yield retrun new WaitWhile(condition)` : Waits while a condition remains true before continuing. 
```Csharp 
Ienumerator WaitWhileExample() {
 yield return new WaitWhile( () => Input.Getkey( KeyCode.Space));
 //wait while the sapcebar is held down 
 debug.Log("SpaceKey released.");
}
```
