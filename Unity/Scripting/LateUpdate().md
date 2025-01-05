
#LateUpdate #Update 
- <b> Purpose </b> :
	- `LateUpdate()` is called <b> once per frame </b> , like [[Update()]], but it called after all [[Update()]] methods have finished. This makes it ideal for actions that should happen after other updates, such as following or aligning the [[camera]].
- <b> Characteristics </b> :
	- Called once per frame, but after all [[Update()]] calls.
	- Often used for tasks that need to occur <b> after </b> all other [[Object]]s have been updated. 
	- Especially useful for adjusting the [[camera]], character [[animations]], or any dependencies between [[Object]]s.
- Use Cases :
	- [[camera]] [[movement]] and following (e.g., following a character after their [[movement]] is updated in [[Update()]] ).
	- Smoothing and final adjustments after all calculations have been made in [[Update()]].
	- Adjusting UI or visual elements that rely on the final positions of [[GameObjects]].
```Csharp

void LateUpdate() {
	 // camera follows the player's postion after the player has moved 
	 transfomr.position = player.transfrom.position + new vector3(0,5,-10);
}
```
In this example, the camera follows the player's position after the player has moved ( updated in  [[Update()]] ).