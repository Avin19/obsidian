
#UIElements  #UXML 

# 1. Accessing UI Elements Using `UIDocument` and  UXML (Recommended)

The most common way to access UI elements is via the `UIDocument` component. The #UIDocument  component acts as a container for your UI structure (defined in UXML files) and can be used to reference UI elements at runtime. 

Example Workflow:

-  <b> 1. Create UXML </b> : In Unity, create a UXML file to define the layout UI elements ( such as buttons , text, labels).
-  <b> 2. Accessing Elements in C# Script </b> : You can the `rootVisualElement` to access all the UI components define in the UXML.

```csharp
using UnityEngine;
using UnityEngine.UIElements;

public class UIToolkitExample : MonoBehaviour
{
	public VisualTreeAsset uxmlAsset; // Link to UXML in the inspector

	private void OnEnable()
	{
		// Access the root of the UI document
		var root = GetComponent<UIDocument>().rootVisualElement;

		// Load UXML and add it to the root
		var uxml = uxmlAsset.CloneTree();
		root.Add(uxml);

		// Assign events to UI elements
		var button = root.Q<Button>("myButton");
		// Use the Q() method for querying by name 
		var label = root.Q<Label>("myLabel");

		//Assign events to UI elements
		button.clicked += () => Debug.Log("Button clicked");
		label.text = "Hello , UI Toolkit!";
	}

}
```

- `Q<T>(string name` : Used to query elements by name and type.
	-  T: Type of the UI element you are searching for ( e.g, `Button` , `Label`).
	-  name: The name of the UI element defined in UXML.


### 2. Accessing Elements by Class Name

You can use the `Q()` method to search for a specific UI element type, and you can query it using various options like `name` , `type`, or `class`.

```csharp
var buttons = root.Query<Button>().Class("myButtonClass").ToList(); 

foreach (var button in buttons) 
{ 
	
	button.clicked += () => Debug.Log("A button was clicked!");

}
```

- `Query<T>()` : Retrieves elements of type `T` (e.g., `Button` )  within the root visual element.
- `Class("className")` : Filters elements based on their assigned class in the #USS ( style sheets ).

### 3. Accessing Elements Using `Q()` for Specific Types

You can use the `Q()` method to search for a specific UI element type, and you can query it using various options like `name` , `type` , or `class`.

```csharp 
var button = root.Q<Button>("myButton");  // Access by name 
var textField = root.Q<TextField>("myTextField"); //Access by name
var image = root.Q<Image>(); // Access first Image element
```
