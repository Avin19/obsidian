#Class #DataType


A variable is a storage location in a computer program that holds data, which can be used and manipulated throughout the program. Each variable has a name, a data type, and a value.

#### Key Concepts of Variables:

1. <b> Declaration : </b> Before using a variable, you must declare it by specifying its data type and name.
```Csharp
	int age;
```
2. <b> Initialization : </b> A variable is initialized when you assign a value to it. You can do this at the time of declaration or later in the program.
```Csharp
	int age =25; // Declaration and initialization
```
3. <b> Data Types : </b> Variables can store different kinds of data. Common data types includes:
		1. int : Stores integers (e.g., 10 ,-5)
		2. float/ double : Stores floating-point numbers ( e.g., 3.14 , -0.01).
		3. char : Stores sequences of characters (e.g., 'A', 'z').
		4. string: Stores sequences of characters (e.g., " Hello" , " World").
		5. bool : Stores Boolean values ( `True` or `false`).
4. Scope : The part of the program where the variable can be accessed. Variables can have different scopes:
	1.  Local Variables: Declared inside a method or function and only accessible within that method.
	2. Global Variables: Declared inside a block (e.g., an if statement or a loop ) are only accessible within that block.
	3. Block Scope: variables declared inside a block ( e.g., an if statement or a loop) are only accessible within that block.
5. Constant Variable: Variable whose value cannot be changes once assigned.
		Declared using the `const` keyword.
```Csharp 
	const double PI =3.14159;
```

## Variable Example in C# :

```Csharp
using System;

public class Program {
	public static void Main() {
		// Declaring variable
		int age = 30;
		double height = 5.9;
		string name = " Avinash";
		bool isStruct = false ;
		
		// Printing variable
	Console.WriteLine("Name : " + name);
	Console.WriteLine("Age : " + age);
	Console.WriteLine("Height : " + height);
	Console.WriteLine("Is a student : " + isStudent);
	}
}
```

## Types of Variables:
1.  Local Variables: These are declared inside methods and can only be used within that method.
2. Instance Variables : Also known as non-static fields, they are declared inside a class but outside of [[method]]s. They are unique t each instance of the class.
3. Static variables : Declared with the static keyword, shared among all instances of a class. 