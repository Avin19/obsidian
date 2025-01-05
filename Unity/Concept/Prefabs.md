Prefabs in Unity are per-configured [[GameObjects]] that can be reused multiple times across your projects. They allow you to create complex [[GameObjects]] ( with [[Components]] , [[script]] , settings, etc.) and save them as a 'blueprint' that can be instantiated multiple times in your scene or programmatically during gameplay.


### Key Benefits of Prefabs:
- 1.  <b> Reuseability </b> :  Create a prefabs once and reuse it wherever needed without manually setting up the object each time.
- 2.  <b> Consistency </b> : Changes made to a prefabs automatically propagate to all instances of that prefab across [[scenes]].
- 3. [[Performance]] :  Prefabs help in [[optimizing]] the game's memory usage by allowing Unity to load [[assets]] more efficiently.

### Creating Prefabs:

* 1. Creating a Prefabs:
		- Create a [[GameObjects]] in your [[scenes]] (e.g., a tree, enemy, or tile).
		- Drag the [[GameObjects]] from the [[hierarchy]] into your project folder. This creates a prefab file.
		- The [[GameObjects]] is now Connected to that prefab. You can instantiate it or reuse it in other scenes.
* 2. Instantiating Prefabs in Code:  To create objects dynamically during gameplay, you insatiate prefabs using the `Instatiate()` method. Here's a simple example of how to insatiate a prefab in Unity using C#.

```Csharp
public class PrefabSpawner :MonoBehaviour
{
	// reference to the prefab
	public GameObject prefabToSpawn;
	
	void Start()
	{
	// Spawn a prefab at the origin 
	Instatiate( prefabsToSpawn, new vector3(0,0,0),Quaternion.identity );
	}
}
```
* 3. Modifying Prefabs:
	-  Editing Prefabs: Double-click the prefab in your Project folder to enter Prefab Mode, Where you can edit it without affecting the rest of the [[scenes]].
	- Updating Instance: Any Changes made to the prefab with be applied to all instances of the prefab in all scenes, unless those instance have been overridden. 
* 4. Prefab Variants: Unity allow you to create variants of prefabs, which is useful, which is useful when you want to create a different version of a base prefab with slight modifications. For example, you might have a base "Enemy" prefab and create variants like "FastEnemy" or "StrongEnemy".
  
  