#Dungeon  #DungeonCreation
![[Dungeon Creation.png]]A key part of this is to provide a flexible and configurable way of constructing random dungeons. 

# Dungeon Creation Objectives . 

1. Create 'Random' dungeons that appear different on each playthrough.
2. Maximize the use of the assets create and also give the player variation in their gameplay. 
3. A dungeon layout will be based on hierarchical graphs of connected room nodes.
4. These graphs can contain any number of room nodes linked by corridors.
5. each node in the graph will represent a dungeon room type by using node types in the graph.
6. There will be multiple room type for variation in gameplay. Entrance room node type , a small room node type , a medium room node type and a boss room node. 
7. Room templates will be hand built to provide well laid out dungeon rooms. 
8. Dungeon will have multiple level generated .
9. ![[Dungeon Creation_1.png]]
10. Dungeon building process 
	1. So for each dungeon level in the game have a number of predefined room node graphs with room types and connections between rooms,
	2. In the image above on left hand side  that in each room node graph there is different room type specified and the connections between them are different. 
	3. On the right hand side , the specified room  templates, and they've indicated different.
	4. Such as for Entrance room node , it has got two different room node.
	5. The Dungeon Builder algorithm will select one of the room node graphs specified for the level randomly, and then it will randomly select from the specified room templates for each node in the selected room node graph.
	![[Dungeon Creation_3.png]]

# The Process 
Can see that process in action, random room node graph has been chosen. and then each node in that node graph is matched up with a random room templates. 

The dungeon building algorithm then places the room template tilemap in the world making sure they connect together as per the room node graph, and also that the rooms don't overlap.


![[Dungeon Creation_4.png]]

To Support this dungeon building design, we need an easy way to create and save dungeon room node. 
The most logical way would be to use a tool that allows us to visually create room nodes and connect them together. 
## Custom Node Editor 
#UnityEditor 