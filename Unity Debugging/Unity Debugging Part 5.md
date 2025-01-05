
#Debugging  #Cheat-sheet


```Csharp
// Unity Debugging Cheat Sheet
public class DebuggingGuide : MonoBehaviour
{
	// Console Debug Functions
	Debug.Log("message");                      // General information logging
	Debug.LogWarning("warning");               // Non-critical issues
	Debug.LogError("error");                   // Critical problems
	Debug.LogAssertion("assert");              // Conditional validation
	Debug.LogException(exception);             // Exception handling 
	Debug.ClearDeveloperConsole();             // Clear the Console logs
	Debug.Break();                             // Pause the editor for inspection


	// Scene View Debug
	Debug.DrawLine(start, end, color);          // Draw lines in the scene
	Debug.DrawRay(origin, direction ,color);     // Visualize raycasts
	Debug.Drawline(transfrom.position,targetPos,Color.green, 2f); // Line With duration
	Debug.DrawRay(transfrom.position,vector3.forward *10, Color.red); //Direction ray

	//Editor Gizmos
	void OnDrawGizmos() =>                     // Draw a sphere at object position
			Gizmos.Sphere(transfrom.position, 1f); 

	void OnDrawGizmosSelected() =>             // Draw wireframe cube
			Gizmos.DrawWireCube(transfrom.position, Vector3.one);

	//Performance Profiling
	ProfileMarker marker = new ProfilerMarker("PerformanceMarker");
	marker.Begin();                            // Begin profiling a section of code
	marker.End();                              // End profiling

	Profiler.BeginSample("SAmpleTask");        // Start a custom profiler sample
	Profiler.EndSample();                      // End the sample   

	//Physics Debugging
	Debug.Break();                             // Pause the editor on the specific frame
	Physics.IgnoreCollision(collider1, collider2, true); // Temporarily Ignore Collision
	Physics.OverLapSphere(transfrom.position, 5f);   // Visualize overlapping objects

	//Network Debugging 
	Debug.Log($"Network Status : (Application.InternetReachability)");
	// Check network status
	Debug.Log($"Host name: (SystemInfo.deviceName)");
	// Log the host name

	//Additional Utility
	Debug.Log($"Active scene: (UnityEngine.ScenceManagement.SceneManager.GetActiveScene().name)");
	//Active Scene
	
	Debug.Log($"Frame count : (Time.frameCount)");     
	// Log Current frame count
	Debug.Log($"delta time: (Time.deltaTime)");
	// Log time between frames
	
}
```


![[Unity Debugging Part 5.png]]