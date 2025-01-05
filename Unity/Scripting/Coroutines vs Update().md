#Coroutines #Update 

- [[Coroutines]] allow you to break up executing over time without blocking the main game loop, whereas [[Update()]] runs code every frame. Coroutines are great for timed delays or sequences.
- [[Coroutines]] are <b> more performance-friendly </b> for tasks that don't need to run every frame. For example, handling animations or waiting for specific [[events]] should use Coroutines rather than putting everything in `Update()`.