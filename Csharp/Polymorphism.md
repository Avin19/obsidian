Polymorphism means "many forms" and allows [[Object]]s to be treated as instance of their base class. The most common type of polymorphism in OOP are [[method overlading]] (compile-time) and [[method overriding ]] (runtime).

* Method Overloading: Same method name with different parameters (compile-time).
* Method Overriding : Redefining a method in a subclass that was already defined in a base class( runtime).
### Example of Methods Overlading in C#:

```Csharp
public class Calculator {
	public int Add(int a , int b){
		return a+b;
		}
	public double Add( double a, double b) {
		 return a+b;
	}
}

```

## Example of Methods Overriding in C#:

```Csharp
public class Animal {
	public virtual void Speak() {
		Console.WriteLine(" The animal makes a sound ");
	}
}

public class Dog :Animal 
{
	public override void Speak() {
		Console.WriteLine("Woof!");
	}
}

```

In this example, the `Dog` class overrides the `Speak` [[method]] of the `Animal` class.
