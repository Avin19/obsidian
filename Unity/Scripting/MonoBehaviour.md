#Class #Monobehaviour

It is [[ Class]] provide by Unity Engine.
## 1. Managing GameObject Components

Since scripts that inherit `Monobehaviour` are attached to [[GameObjects]], they can interact with other components attached to  the same or different [[GameObjects]]. You can access and modify components, like [[Rigidbody]],[[colliders]], [[Transform]], etc., directly within the script.

## 2. Enabling and Disabling MonoBehaviour

You can enable or disable the`Monobehaviour` script from the code. When a script is disabled, Unity stops calling its lifecycle methods like [[Update()]] , [[FixedUpdate()]] ,etc.

