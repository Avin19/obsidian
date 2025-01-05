Scripting in Unity is a Core aspect of game development, allowing developers to create custom behaviors, control game logic, and interact with other Unity systems. unity primarily uses C# for scripting. Below is a more in-depth look at key scripting concepts, features, and practices in Unity.


*  <b> 1.  MonoBehaviour </b> 
		*  Base [[Class]] : Almost all Unity scripts derive from the [[MonoBehaviour]] class. This provides a structure for how scripts interact with the Unity engine.
		* Lifecycle Methods:
			- [[Awake()]] : Called when the script instance is being loaded. Used for initialization before [[Start()]].
			- [[Start()]] : Called before the first frame update. Initialization code can go here if you need something after the scene has fully loaded.
			- [[Update()]] : Called once per frame. Commonly used for real-time updates such as checking for user input or moving objects.
			- [[FixedUpdate()]] : Called at fixed intervals, independent of frame rate. It is typically used for physics-related updates like [[Rigidbody]] movement.
			- [[LateUpdate()]] : Called after all [[Update()]] methods. Useful for operations that need to happen after the game logic updates (like camera following).
			- [[OnEnable()]] / [[OnDisable()]] : called when the object is enabled /disabled.
			- [[OnDestory()]] : Called when the object is destroyed, good for cleanup logic.
			- [[OnTriggerEnter()]] / [[OnCollisionEnter()]] : Handle physics-based interactions such as when objects collide or enter trigger zones.
* <b> 2. Variables and Access Modifiers </b> 
		- Public vs Private Variables :
			 * [[public]] :  Variables accessible by other classes and shown in the Unity Inspector.
			 * [[private]] : Variable that are only accessible within the script and are hidden from the inspector unless explicitly serialized.
			 * Serialized Fields: Even `private` fields can be made editable in the Unity Inspector using `[SerializeField]` .
```Csharp
public int health = 100 ; // Visivle and editable inInspector
[SerializeField] private int speed =5 ; // Editable in Inspector but private to the class 
```

* <b> 3. Unity's  Input System </b> 
		- Old Input System: Use `Input.GetAxis()` , `Input.GetKey()` , and `Input.GetMouseButton()` to handle player input.
		-  New input System: More complex and flexible, allowing support for multiple input devices (gamepad , touch, mouse). It uses action maps and events for input detection.
```Csharp 
float horizontal = Input.GetAzid("Horizontal");
if(Input.GetKeyDown(KeyCode.Space))
{
	//Jump Code 
}
```
* <b> 4.  Coroutines</b>
		- [[Coroutines]] allow you to pause the execution of a functions and resume it after a certain condition is meet or a time delay has passed.
		- Useful for creating timed actions, such as animations. delay between attacks, or loading screens.
```Csharp
IEnumerator DelayedAction() 
{
	yield retrun new WaitForSeconds(2f);
	// Wait for 2 Seconfs
	Debug.Log(" Action after delay !");
}
// Starting a Coroutine
startcoroutine(DelayedAction());
```
* <b> 5. Physics and RigidBody Control </b>
	- Unity's <b> Physics System </b>uses the [[Rigidbody]] component to enable physics behavior. Scripts can apply forces, set velocity, or handle physics-based movement.
	- `ForceMode` : Determines how the force is applied (e.g., impulse ,velocity changes, or continuous).
```Csharp
public Rigidbody rb;

void Start()
{
	rb = GetComponent<Rigidbody>();
}
void Update()
{
	if(Input.GetKeyDown(KeyCode.Space))
	{
		rb.AddForce(Vector3.up*10, ForceMode.Impulse); // Apply force for jumping
	}
}
```
* <b>  6. Collision and Trigger Events </b>
	* [[Collision]] Detection: Handle physical interactions between objects. Commonly used methods:
		* `OnCollisionEnter(Collision collision)` : Called when two objects with colliders and rigidbodies touch.
		* `OnTriggerEnter(Collider other)` : Called when a [[GameObjects]] enters a [[trigger]] collider (trigger colliders are non-physical, used for events).
```Csharp
void onCollision(Collision collision)
{
	if(collision.gameobject.Comparetag("Enemy"))
	{
		// Handle collision with enemy
	}
}
```
* <b> 7.  Delegates and Events </b>
	* [[Delegates]] : Allow methods to be passed as parameters, enabling flexible event-driven programming.
	* [[Events]] : Built on delegates, they allow objects to notify other objects when something happens. Useful for decoupling systems.
```Csharp
public delegate void GameOverDelegate();
public event GameOverDelegate OnGameOver;

void EndGame()
{
	if(OnGameOver != null)
	{ 
		OnGameOVer(); // Trigger the event
	}
}
```
* <b> 8. ScriptableObjects </b>
	* [[ScriptableObjects]] : Used to store data and configurations outside of scenes and [[GameObjects]]. They are reusable and can be shared across multiple scenes or objects without being attached to a [[GameObjects]].
	* Great for storing configuration data, levels, item properties, etc.
```Csharp
[CreateAssetMenu(fileName = "NewCharacterStats", menuName = " Character Stats")]
public class CharacterStats : ScriptableObject {
	public int health;
	public int attackPower;

}
```
* <b> 9. Managing Game State </b>
	* [[Singletons]] : A common design pattern used to maintain one instance of a class throughout the game. Useful for managing game states (e.g., GameManager , AudioManager).
	* `DontDestoryOnLoad(gameObject)` : Keeps the [[GameObjects]] intact between scene loads.
```Csharp
public class GameManager : MonoBehaviour {
public static GameManager Instance {get; private set;}

void Awake() {
	if(Instance == null){
		Instance = this ; 
		DontDestoryOnLoaf(gameObjects);  // Persist through scene loads
	}
	else {
		Destory(gameObject);
		// Ensure only one instance
		}
	
	}
}
```
* <b> 10. Interfaces and Inheritance </b>
	* [[Interface]] : Define common behavior that multiple classes can implement.
	* [[Inheritance]] : Allows sharing common functionality across multiple classes. For example, a base class `Character` can be inherited by `Player` and `Enemy`.
```Csharp 
public interface IDamageable
{
	void TakeDamage( int damage);

}

public class Enemy : Monobehaviour , IDamageable {
	 public void TakeDamage(int damage){
	 // Enemy takes damage
	 }
}
```
 * <b> 11. Serialization and Persistence </b>
	 * [[PlayerPrefs]] :  Simple way to store and retrieve small amounts of data, like scores or settings.

```Csharp
PlayerPrefs.SetInt("HighScore", score);
int highScore = PlayerPrefs.GetInt("HighScore");
```
 
 * [[JSON]] Serialization : Save and load game data in [[JSON]] format, allowing for more complex data persistence.
 ```Csharp
 [System.Serializable]
 public class PlayerData{
	 public int level;
	 public int health;
 }
 string json = JsonUtility.ToJson(playerData);
 PlayerData loadData = JsonUtility.FromJson<PlayerData>(json);
```
* <b> 12 . Object Pooling </b>
		*  [[Object Pooling]] is a performance optimization technique to reuse objects ( like enemies or bullets) rather than creating and destroying them.
```Csharp
public class ObjectPool : MonoBehavior {
	[SerializeField] private GameObject prefab;
	private Queue<GameObject> pool = new Queue<GameObject>();

	public gameObject GetObjrct()
	{
	if()}
}
```
- <b> 13. Custom Inspector and Editor Scripts </b>
	- You can extend [[Unity Editor]]'s by creating custom inspectors to visualize and edit data in ways that are more intuitive for your specific game.
```Csharp
[CustomEditor(typeof(MyScript))]
public class myScriptEditor : Editor {
	public override void OnInspectorGUI(){
		MyScript script = (MyScript) target;
		script.myvariable = EditorGUILayout.IntSlider("Varaible", script.myVaraible, 0 ,100);
		DrawDefultInspector();
		
	}
}
```
- <b> 14. Managing Time </b> 
	- [[Time.deltaTime]] : Represents the time that has passed since the last frame. It's essential for frame-rate independent movement and animations.
```Csharp 
transform.position += Vector3.forward * speed * Time.deltaTime;
```
