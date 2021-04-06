# Shape2D

### Description
The Shape2D is used to render squares with a single color. It is build on top of the [GameObject](GameObject.md) class and the [Collider](Collider.md) interface, so it has access to variables and methods defined withing those classes, it is advised that you look into those classes in order to find out more.

### Properties
| Property      | Description | Type | Default Value |
| :---  |    :----   | :---: | :---: |
| Color | The color of the shape | System.Drawing.Color | Red |

### Constructors

| Signature      | 
| :---  |
| Vector2 position, Scale scale, Color color, string tag, uint renderingPriority |
| Vector2 position, Scale scale, string tag |
| Vector2 position, Scale scale, Color color |
|Vector2 position, Scale scale |

Useful links:

* [GameObject](GameObject.md)
* [Vector2](../Builtin_Datatypes/vector2.md)
* [Scale](../Builtin_Datatypes/scale.md)