#Update 
- ##### Purpose  :
	- `Update()` is called once per frame, making it ideal for handling regular updates that are frame-dependent, like processing [[input]] , moving [[GameObjects]] , and playing [[animations]].
- ##### Characteristics:
	- Called every frame (frame rate dependent).
	- Runs on the main game loop.
	- Used for tasks like checking player [[input]] or adjusting [[Object]] positions based on user interaction.
	- Timing varies depending on the frame rate of the game.
- <b> Use Cases </b>:
	- Player [[input]] handling (e.g., [[movement]] , jump triggers).
	- Simple non-physcis [[Object]] [[movement]] (e.g., Ui updates or non- physics game elements).
	- Real-time game logic that needs to change every frame.
```Csharp
void Update() {
	 float move = Input.GetAxis(" Horizontal");
	 transfrom.Translate(Vector3.right * move * Time.deltaTime);
}
```
In this example, the[[Object]] moves based on player [[input]], using [[Time]].deltaTime to make the [[movement]] frame-rate independent. 