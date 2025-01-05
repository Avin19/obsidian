#Debugging #Inspector #Attributes


```Csharp
public class UnityAttributesCheatSheet : MonoBehaviour {
	// Data Serialization
	[SerializeField]    // Make private field visible in Inspector
	[Serializable]      // Mark Class/ Struct for serialization
	[Range(min, max)]   // Add numeric range Constraints
	[Header("Header Text")] // Add Section headers
	[Tooltip("Tooltip Text")] // Show hover information
	[HideInInspector]         // hide public fields
	[Sapce(10)]               // Add vertical spacing
	[TextArea]                // Multi-line text with Scrollbar
	[Multiline]               // Multi-line text without Scrollbar
	[ColorUsage(true,true)]   // Customize color picker (HRD, alpha)
	[Min(0)]                  // Set Minimum Value
	[Max(100)]                // Set Maximum Value
	[FormerlySerializesAs("oldName")]  //Maintain serialization after rename
	[ContextMenu("Function")]  //Add inspector context menu
	[ContextMenuItem("Menu", " Function")] // Add field context menu
	[Delayed]                   // Update only after edit complete
	[NonSerialized]             // precent serialization


	//Custom Editor Attributes
	[CustomEditor(typeof(Type))] // Create custom inspector
	[PropertyDrawer(typeof(Type))]


}
```













![[Unity Debugging Part 4.png]]

