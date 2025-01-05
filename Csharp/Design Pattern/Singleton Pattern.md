#DesignPattern

One of the first problems you're likely to run into  when building your games is how to connect objects together.


For example, enemy objects in the game may need a reference to  the player object in order to fire at it or more towards it. 

A common solution to this problem is by using a #Singleton, which is a technique that creates a static reference, which is a reference that any class  can access without a link to a specific object, but to an instance of an object.

It generally works by having a script set the static reference, which is of its own type, to itself , so long as it's not already set. 

```Csharp

public static Singleton Instance { get; private set;}

public void Awake()
{
	// If there is an instance, and it's not me, delete myself.

	if( Instance != null && Instance != this)
	{
		Destory(this);	
	}
	else
	{
	
		Instance = this ;
	}

}

```

Generally Singletons are bad, and that you shouldn't use them. 


While this can be true, it's only an issue if you singletons in the wrong way. 


# But what's the wrong way to use a singleton ?

Singletons are based on static variables and, as general rule of thumb, you should only make something static if there will definitely only ever be one of those types of things. 


#AudioManager, for example , are an ideal use case for singletons, because they need to exist in the scene, everything may need to use it and there will only ever be one in the game. 

While a player singleton ,  despite being very convenient , Could cause problems later if you decide to add multiplayer to your game. 

