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


Inheritance is a cornerstone of object-oriented programming, as it allows you to  define the behavior of something based on what it is. 

In Unity, you'd typically use inheritance when you want to create different classes that are a type of something else. 

For example , a Player , an Enemy and an NPC would all behave in different ways, but they might still need to share the same functionality , such as moving , talking, or taking damage. 

These behaviours are common to all three classes because of what they are, type of human.


The benefit of Inheritance is that it allows you to place those behaviours in one place, a human class, that each of the sub-classes will inherit from .


```Csharp

public class player : Human
{

	// I have health
}

public class NPC : Human
{

	// I have health 
}

public class Enemy : Human 
{

// I have health 
}

public class Human : MonoBehaviour
{
	pulbic float hp;
	public void Take Damage( float dmg) {}
	public void Walk() {}
	public void Talk() {}
}
```




