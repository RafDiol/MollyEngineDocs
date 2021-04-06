# MollyEngine Class

### Description
The MollyEngine class is one of the most important classes in the entire engine. You can think of this class as you game's class since all the events such as the OnLoad can only be overridden from this class.


### Events
You can implement all of the following methods in you Game class by using the 'override' keyword.

| Method      | Description |
| :---        |    :----   |
| OnLoad | This method is only called once on startup |
| OnDraw | This method is called directly before the window is refreshed/re-rendered|
| OnUpdate | This method is called after the window has been refreshed |
| OnClose | If you game exits normally without any exceptions this method will be called. This method gives the developer a single argument 'e' of type 'System.ComponentModel.CancelEventArgs' which allows him to cancel the game's shutdown |
| OnException | If an exception occurs during run-time this method will be called, which allows the developer to figure out what went wrong through the 'e' argument of type Exception. |
| OnKeyDown | Captures when a key is pressed.A KeyEventArg variable ispassed in the method so that the program can determine which key was pressed|
| OnKeyUp | Captures when a key is released.A KeyEventArg variable is passed in the method so that the program can determine which key was pressed |
| OnMouseDown | Captures any sort of mouse click. A MouseEventArgs variable is passed in the method so for potential further processing of this click |
| OnMouseUp | Detects when the moused is released.A MouseEventArgs variable is passed in the method so for potential further processing |
| OnMouseDoubleClicked | Captures a mouse click. A MouseEventArgs variable is passed in the method so for potential further processing |
| OnMouseMoved | Captures mouse movement. A MouseEventArgs variable is passed in the method so for potential further processing |

<br></br>

### Game Window Methods

| Method      | Description | Return Type |
| :---        |    :----   |  :----:   |
|setTitle | Updates the windows title | void |
|getTitle | Returns the windows title| string |

<br></br>

### Constructors

| Constructor Signature | Description |
| :---        |    :----   |
| Scale ScreenSize, string Title, FormWindowState state| The most detailed constructor of them all. |
| Scale ScreenSize, string Title | The 3rd ommited parameter of type FormWindowState is set to **FormWindowState.Normal**|
| string Title | The state is set to Normal and the Scale to 512(Width), 512 (Height)|
| Scale ScreenSize | The state is set to Normal and the title to "New Game" |

<br></br>

### Public Properties
| Property | Description | Type |
| :---        |    :----   |    :----   |
| backgroundColor | The background color of your game | System.Drawing.Color |

<br></br>

### Misc
The misc are uncategorized or rarely used methods or properties. Some Misc methods/properties may not be documented


| Method | Description | Return Type | Is Static|
| :---        |    :----   |    :----:   |   :----:   |
| RegisterGameObject | Makes a GameObject eligible for rendering. You only need to use if you are creating your own/custom GameObject or expanding a child of the GameObject such as the Sprite2D | void | Yes |
| UnregisterGameObject | Makes a GameObject uneligible for rendering. You only need to use if you are creating your own/custom GameObject or expanding a child of the GameObject such as the Sprite2D | void | Yes |

<br></br>
Useful links:

* [Sprite2D](Components/Sprite2D.md)
* [Shape2D](Components/Shape2D.md)