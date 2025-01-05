#MVC

Creating an inventory system in Unity using the MVC ( Model - View -Controller ) pattern involves organizing the code in a way that separates the data( Model), user interface ( view), and logic/ interaction handling ( Controller). Here's a step-by-step guide to structuring the system:

![[MVC Pattern.png]]
### 1. Model : Representing Inventory Data

The Model will hold the data related to each item in the inventory, such as name, description, and quantity. you can use a class for each item and a collection to hold the items. 

```csharp
[System.Serializable]

public class InventoryItem
{
	public string itemName;
	public string description;
	public int quantity;
	public InventoryItem(string name, string description , int quantity)
		{
			itemName= name;
			this.description = description ;
			this.quantity = quantity;
		}
}
```

#### Inventory Model

```csharp

using System.Collections.Generic;

public class InventoryModel
{
	private List<InventoryItem> items;
				
	public InventoryModel()
	{
		items = new List<InventoryItem>();
		
	}
	public List<InventoryItem> GetItems()
	{
	 return items;
		
	}
	public void AddItem(InventoryItem item)
	{
		items.Add(item);
	}
	public void RemoveItem(InventoryItem item)
	{
		items.Remove(item);
	}
	public void ClearInventory()
	{
		items.Clear();
	}
}
```


#### 2. View : Displaying the Inventory to the Player

This View is responsible for displaying the inventory on the UI and updating the display when changes occur.

##### Inventory View

This script will be responsible for rendering the inventory items on the UI. Each item can be represented by a UI elements ( e.g., `Button`, `Text` , or a custom prefab for an inventory slot).

```csharp

using UnityEngine;
using UnityEngine.UI;
using System.Collection.Generic;

public class InventoryView :MonoBehaviour
{

[SerializeField] private Transfrom inventoryPanel;//Panel to hold inventory it UI
[SerializeField] private GameObject inventoryItemOerfabs;//Prefab fro each inventory item

	public void DisplayInvnetory( List<InventoryItem> items)
	{
		//Clear existing UI Elements
		foreach( Transfrom child in InventoryPanel)
		{
			Destroy(child.gameObject);	
		}
		// Populate UI with items
		foreach( var item in items)
		{
			var itemUI = Instantiate(inventoryItemPrefab , inventoryPanel);
			itemUI.GetComponentInChildren<Text>().text = $"{item.itemName} (x{item.quantity})";
		}
	}

}
```

### 3. Controller : Handling User Actions

The Controller bridges the Model and View.  It manages actions like adding or removing items and triggers the View to update.

###### Inventory Controller

The `InventoryController` will handle the interactions, such as adding or removing items from the inventory, and notify the `InventoryView` to update the display. 

```Csharp

using UnityEngine;

public calss InventoryController : MonoBehaviour
{

	private InventoryModel inventoryModel;
	private InventoryView inventoryView;


	private void Awake()
	{
			inventoryModel = new InventoryMode();
			inventoryView = FindObjectOfType<InventoryView>();		
	}
	private void Start()
	{
		UpdateView();
	}
	public void AddItem(InventoryItem newItem)
	{
		inventoryModel.AddItem(newItem);
		UpdateView();
	}
	public void RemoveItem(InventoryItem item)
	{
		inventoryModel.RemoveItem(item);
		Updateview();
	}
	private void UpdateView()
	{
		inventoryView.DisplayInventoryModel.GetItems();
	}
}

```

### 4. Connecting the Components

1. Inventory View : Attach the `InventoryView` script to a GameObject ( eg., an empty GameObject or UI Canvas ) and set references to `inventoryPanel` and `invenotryItemPrefab` in the Inspector.
2. 