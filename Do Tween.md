#dotween #Animation #tweening #animationSequencing


It is a popular tweening library for unity. DoTween is used to create animations and smooth transitions for objects in unity. It allows developers to animate properties like position, rotation, scale, and other values with ease and efficiency.

### Key Features of DoTween:
- <b> Smooth animations </b> : You can animate almost any type of property ( like Position, rotation, scale, color, etc.)
- <b> Performance optimized </b> : DoTween is designed  to be very fast and efficient, even for complex animations.
- <b> Simple API </b> : DoTween provides a simple interface to animate object with minimal code.
- <b> Sequencing </b> :  You can chain animations together to create more complex, timed sequences.
- <b> Callbacks </b> :  Allows you to trigger custom actions when the tween finishes, is paused, or when specific events occur. 

### How to Use DoTween in Unity:
##### 1. Install DoTween
First, you need to install 
-  Downloading it from the Unity Asset Store.
-  Or by using NuGet to add it to you Unity project .

##### 2. Basic Example 
Here's an example of how you can DoTween to animate a GameObject's position in Unity.

```Csharp
using Dg.Tweening;
using UnityEngine;

public class DoTweenExample : MonoBehaviour
{
	void Start()
	{
		// Move the object to the right over 2 seconds 
		transform.DOMove( new Vector3(5,0,0), 2f);
		
		// scale the object over 1 second
		transform.DOScale(new Vector3(2, 2 ,2 ), 1f);
		
	}
}
```
##### 3. Animating Rotation 

You can also animate rotations using DoTween :

```Csharp 
transform.DORotate(new Vector3(0,180, 0 ),2f , RotateMode.FastBeyond360);
```

#### 4. Using Sequence 

You can create a sequence of animations with DOTween :