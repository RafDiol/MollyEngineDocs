# Sprite2D

### Description

Most if not all of your GameObjects will be of type Sprite2D. Sprite2D allows for the rendering/control of an image on the screen. It is a child of the [GameObject](GameObject.md) class and it also implements the [Collider](Collider.md) interface. The implementations/methods/properties inherited by those classes will not be listed here and can be found at the appropriate docs.

### Public Methods

| Method & Signature     | Description | Return Type |
| :---        |    :----   | :----:   |
| setImage(string directory) | Sets the sprites image to another image located in the giver directory| void |
| setImage(string directory, Scale scale) | Sets the sprites image to another image located in the giver directory and resized it accordingly | void |
| getImage | Returns the sprites image | Bitmap |

### Properties
| Property     | Description | Type |
| :---        |    :----   | :----:   |
| Directory | The directory in which the sprites image is stored | string | 

### Constructors

| Signature     | Description |
| :---        | :----:
|Vector2 position, Scale scale, string directory, string tag, uint renderingPriority| - |
|Vector2 position, Scale scale, string directory, string tag| renderPriority has its default value 0 |
|Vector2 position, Scale scale, string directory| renderPriority has its default value 0 and tag is equal to an empty string|

Useful links:

* [GameObject](GameObject.md)
* [MollyEngine Class](../MollyEngineClass.md)
* [Camera](Camera.md)