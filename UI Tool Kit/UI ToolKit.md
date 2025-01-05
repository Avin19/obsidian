#UIToolkit


The UI Toolkit is a Unity Package containing many features, resources, and tools for developing a User Interface ( #UI). You Can use UI Toolkit to build custom UI and extensions for the #UnityEditor , runtime debugging tools, and runtime UI for games and applications.

Standard web technologies inspire UI Toolkit. if you have experience developing web pages or applications, you will get used to the core concepts of how the UI toolkit works in Unity.


# UI Toolkit

To open the #UIBuilder, you will go to  Window -> UI  Tool Kit -> UI Builder.
![[UI Tool Kit/UI ToolKit.png]]

![[UI ToolKit-1.png]]

You will be greeted with the following window, the images above; this window you can attach to the other editor windows on Unity or use it separately.

1. <b> StyleSheets : </b> Manage #StyleSheets and USS Selectors to share styles across UI Documents (UXML) and elements. 
2. <b> Hierarchy </b> : On this window, you create the section where the #UI will be ; you can select, reorder, reparent ,cut ,copy ,paste ,and delete elements in the UI #hierarchy of your document.
3. <b> Library </b> : This is where you are going to get the UI #element like #Text, #Labels , #Buttons, etc.
4. <b> Viewport </b> :  This is where you can visualize where your UI element is being placed on the screen, and you can edit some parts directly here.
5. <b> Code Previews </b> : This is the UI Document (UXML) text and the Stylesheets ( #USS) when created on the Viewport window.
6. <b> Inspector </b> : When selecting a UI element using the Inspector windows, you can change properties like #color ,  #width , #size , #font , etc.


# UXML File

Having the UI Builder window open, you'll save the UXML file that will hold the UI Elements. Name your UXML file and press save.
![[UI ToolKit-2.png]]
![[UI ToolKit-3.png]]

To keep everything organized, save your UXML file in its Ui XML folder inside the Scripts folder.

Each UXML file will represent the UI you want to make.

For example, you can have a #UXML file for your Menu, another  UXML file for your Pause Menu, and another for the UI during gameplay.

Viewport

To ensure our UI fits our screen resolution, select your display preference on your Game window.
![[UI ToolKit-4.png]]

Select your canvas, and have your zoom view at 50% . On the inspector window, 
![[UI ToolKit-5.png]]

# Hierarchy 

Since we are going as simple as possible, we will add a #GroupBox from the #Library ->  #Containers section to the Hierarchy window and stretch  that #GroupBox to the end of the canvas.
![[UI ToolKit-6.png]]

Using the Inspector window , we will rename the GroupBox to MainGroupBox.

![[UI ToolKit-7.png]]

Add another GroupBox, which will be a child , to the #MainGroupBox. Rename it #TextGroupBox.

![[UI ToolKit-16]]
From the Library -> Controls window, drag a Label element and place it inside the TextGroupBox and rename the Label  to scoretxt.

![[UI ToolKit-8.png]]

![[UI ToolKit-9.png]]  ![[UI ToolKit-10.png]]

Using the #Inspector window, go to the #label section, and on Text, write Score: 0. And on the Text section for Font Style, make it Bold,  Size 50.
![[UI ToolKit-11.png]] ![[UI ToolKit-12.png]]

![[UI ToolKit-13.png]]


#StyleSheets 

The StyleSheets window is where you create your USS File.


This USS file holds properties related to Font, Color, and Size for the classes you are using. This will allow all text, buttons, or backgrounds to have a specific style without going to each element one by one and doing the property changes.

Please create a new #USS file and save it.

![[UI ToolKit-14.png]]

![[UI ToolKit-15.png]]

Once the file have been created where it says Add new selector, you will type .unity_text_element, and a window with some tips will pop up.

![[UI ToolKit-17.png]]
![[UI ToolKit-18.png]]

This Style of class Writing is very similar to how you approach style using #CSS on web design. To style all  paragraphs or all headers on HTML, you will use "p{}" or "h1{}" to target the <p.>  and <h1.> tags.

If you named your tag with a custom class like <p. class="Unity">, the way to target this specific tag is to use a period before the naming of the class, ".unity".

<b> BACK TO THE UI BUILDER </b>

To get the specific style class for the UI element on the Inspector window, a section named StyleSheet shows you what class style to use for a specific UI Element.

You can double-click the class, which will be added to the USS file, or type it as we did above. 

![[UI ToolKit-19.png]]
![[UI ToolKit-20.png]]

To see this Ui text, you will need a #GameObjects  with a #UIDocument component, and as its #Source #Asset , you will put your UXML #Layout.

![[UI ToolKit-21.png]]

You can add this by hand or right-click on the #Hierarchy window and go to  #UIToolkit  -> #UIDocument .

![[UI ToolKit-22.png]]

# UI Manager Script

The [ --- UI ---]  Game Object has the #UIManager script as a #Components , giving us access to update our text whenever we want. 

![[UI ToolKit-23.png]]

![[UI ToolKit-24.png]]

To get access to the UI Element, we need to add the following namespace: 

using UnityEngine.UIElements, like  on line 4.

On line 9, we are getting the reference to the #UIDocument that the #UIDocument  #Gamepad  is holding.

On line 10, we need to use the #VisualElement class to access our #UIElements.

You may notice that on line 23, we are getting/changing our text by directly stating that the label is named "scoretext" ; that's the name we give to the element at the beginning of this article.


This is a fundamental approach to getting a score text system using the new UI Builder 
