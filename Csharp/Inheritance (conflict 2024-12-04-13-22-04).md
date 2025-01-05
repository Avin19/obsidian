#OOP #OOPSConcepts 

Inheritance allows a [[Class]] to inherit [[Properties]] and behavior from another class.  The [[Class]] that inherits is called the subclass or derived class, and the class being inherited from is called the base class or superclass. This promotes code reusability and allows for hierarchical relationships.
	- Single inheritance : A Class inherits from one bass class.
	- Multiple inheritance: Not supported directly in C#, but can be achieved using [[Interface]].
```Csharp
public class Vehicles {
	public string branch = " Ford";
	public void Honk() { 
		Console.WriteLine(" Beep beep!");
		
	}
}
public class Car: Vehicle {
	public string model = "Mustang";
}
```
Here, `Car` inherits the `brand` and `Honk` method from the `Vehicle` class.