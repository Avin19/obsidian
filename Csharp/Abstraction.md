#OOP #OOPSConcepts 

Abstraction is the process of hiding the internal implementation details of a [[Class]] and exposing only the functionality to the user. This allows the user to interact with the [[Object]] without worrying about its complexity.

In C# , [[Abstract class]] and [[interfaces]] are used to achieve abstraction. Abstract [[Class]]es provide partial implementation, while [[interfaces]] define what [[method]]s a [[Class]] must implement without providing the implementation itself.

```Csharp
public abstract class Animal {
	public abstract voif Speak(); // Abstract method
}

public class Dog : Animal  {
	public override void Speak()  {
		Console.WriteLine("Woof");
	}
}
```

The `Dog` [[Class]] provides the implementation for the abstract `Speak` [[method]].