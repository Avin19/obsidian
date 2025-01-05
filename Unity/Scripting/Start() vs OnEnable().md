#### Comparison on `Start()` and `OnEnable()`

| Aspect              | OnEnable()                                              | Start()                                                    |
| ------------------- | ------------------------------------------------------- | ---------------------------------------------------------- |
| When is it called ? | Every time the [[Object]]/[[script]] is enabled.        | Once, when the[[Object]] is first initialized and enabled. |
| Number of Calls     | Can be called multiple times ( each time it's enabled). | Called only once in the [[Object]]'s lifettime.            |
| Common Use Cases    | Resetting [[Variable]]s , subscribing to [[Events]].    | One-time initialization, setting up references.            |
| Runs before         | Runs before [[Start()]] .                               | Runs after [[OnEnable()]], but before the first frame.     |
| Paired with         | Typically paired with [[OnDisable()]] for cleanup.      | Not typically paired, used for initialization only.        |
