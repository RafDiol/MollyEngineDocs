# Renderer

### Description

The **Renderer** is in the Misc section because it is not some sort of class or struct that the developer, it can only be called by the Engine itself. The renderer though is documented so that you can understand the rendering system of your game.

## How Does it Work

#### When is it called
The renderer method is being called every frame after the OnDraw event has been completed.

#### Order of operation
The rendering does the following, in the following order.

1. Clears the screen and fills it with the background color.

2. Updates the camera position.

3. Creates a list of all the elements in the game it will need to render.

4. Due to the fact that a [Shape2D](../Core/Components/Shape2D.md) is rendered differently than a [Sprite2D](../Core/Components/Sprite2D.md) and that the rendering list is made out of [GameObjects](../Core/Components/GameObject.md) we need to identify every GameObject who's type is null/undefined.

5. Loops through our list of GameObjects we need to render and checks whether or not the GameObjects priority is equal to the ```currentRenderingPriority```. Every time the loop is completed the ```currentRenderingPriority``` is incremented and any items that have been rendered are removed from our list of GameObjects we need to render.

#### Notes

The rendering algorithm used by MollyEngine is far from perfect and some flaws do exist. For example if you have 2 objects(a and b) and objects a rendering priority is 0 while objects b rendering priority is 100 the loop will run 100 times untill the ```currentRenderingPriority``` reaches 100.

#### Feature planning

The rendering algorithm is on my TODO list of thing to fix/update since I have already come up with a few ways too make it more efficient.