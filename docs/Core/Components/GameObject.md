# GameObject

### Description

Think of the GameObject class as the root of all components. It defines a few necessary methods and variables that every component needs. Any component which can be rendered is a child of the GameObject class.

### Public Methods
| Method      | Description |
| :---        |    :----   |
| DestroySelf | Removes the object from the game engine |

<br></br>
**Disclaimer: If you are holding a reference of the GameObject then the GC (Garbage Collector) will not collect it unless you dispose it.**

<br></br>

### Properties

| Name      | Description | Type |
| :---        |    :----   | :---- |
| Position | The position of the object| Vector2 |
| Scale | The scale of the object| Scale |
| Tag | A string identifier for the object | string |
| renderingPriority | The highest number will be infont of a smaller one, check out the [renderer section](../../Misc/renderer.md) for more details on how the renderer works | uint |
| type | Saves resources by specifing the type of the GameObject, find out more in the [renderer section](../../Misc/renderer.md) | System.Type |