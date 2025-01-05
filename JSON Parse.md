#json

JSON ( JavaScript Object Notation) parsing refers to the process of converting a JSON string into a data structure ( like an object or array ) that a programming language can work with. In C# , parsing Json data can be done using the `JsonSerializer` class from the `System.Text.Json` namespace, or you can `JsonConvert` from the `Newtonsoft.Json` library ( a widely-used package for working with JSON in C#)
```json
{
	"name" : "Avinash",
	"age" : 30,
	"address" : {
		"city" : "New York",
		"zipcode" : "10001"
	},
	"Hobbies" : ["reading","Cycling"]
}
```
# Example : Parsing JSON in C# 

#### 1. Using `System.Text.Json` (Built-in)

```Csharp
using System;
using System.Text.Json;


public class Program 
{
	public class Person
	{
		public string Name { get; set; }
		public int Age { get; set; }
		public Address Address {get; set;}
		public string[] Hobbies {get;set; }
	}
	public class Address
	{
		public string City { get; set; }
		public string Zipcode { get; set;}
	}
}

```



The ` Person` class in the C# example serves as a model or data structure that maps the JSON data into a corresponding object in c#. Here's why it's necessary:

## Why Use the `Person` Class ?

### 1. Data Mapping: 
Json is a structured format for representing data( typically key-value pairs), and we need a way to map that structure to  a format the program can work with. In C# , this is often done by creating a class that mirrors the structure if the JSON Object. 

-  In the example : 
	-  The Json Contains fields like " name" , "age", and "address".
	-  The `Person` class has corresponding properties like `Name`, `Age`, and `Address` to hold these values.
#### 2. Type Safety :
C# is a strongly-typed language, which means it enforces types for variables. By creating the `Person` class , you define the expected types of the data.
- For example, in the JSON:
	- `"name"` is a string , so the `Name` property in the `Person` class is of type `string`.
	- `"age"` is a number, so the `Age` property is of type `int`.
- This ensures that the data is handled correctly and avoids runtime errors caused by type mismatches. 
#### 3. Structured Access: 
By using a class, you can easily access and manipulate different parts of the data using properties.
- For instance, after deserializing the JSON into  a `Person` object, you can access the `Name` property as `person.Name`, or the `City` property of the nested `Address` object as `person.Address.City`. This makes the code cleaner and easier to work with compared to directly accessing raw JSON data. 