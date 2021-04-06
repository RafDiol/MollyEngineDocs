# Quick Start

In this quick start guide we will make game in which the player will be collecting coins.

To begin with lets create our game window as follows
```csharp
public class DemoGame : Core.MollyEngine
{
    public DemoGame() : base("New Game")
    {
        
    }
}
```
The code above creates our **DemoGame** object and passes in a parameter, a title.

Now that our DemoGame object is setup lets get started on setting up the player movement. MollyEngine offers some great extensions which help you out prototype and implement your ideas faster, one of which is the [**PlayerController extension**](Extensions/PlayerController.md). The engine offers some event's, similarly to Unity, Unreal etc that you can implement such as **OnLoad**.

```csharp
public override void OnLoad()
{
    player = new Sprite2D(new Vector2(100, 100), new Scale(100, 100),   Path.GetFullPath(@"Images\player.jpg") , "Player", 1);
    playerController = new PlayerController(player, speed);
}
```
**Remember: Make sure to import MollyEngine.Extensions**

This code creates a [Sprite2D](Core/Components/Sprite2D.md), which is our player and passes him to the player controller extension.The constructor used for our player sprite has the following signature:
```Sprite2D(Vector2 position, Scale scale, string directory, string tag, uint renderingPriority)```.

The [PlayerController extension](Extensions/PlayerController.md) needs to be implemented in the following events for it to work properly:
```csharp
public override void OnUpdate()
{
    playerController.Update();
}

public override void OnKeyDown(KeyEventArgs e)
{
    playerController.OnKeyDownHandler(e);
}

public override void OnKeyUp(KeyEventArgs e)
{
    playerController.OnKeyUpHandler(e);
}
```
**Remember: PlayerController is an extension and not part of the core framework and that's why you need to call the above methods by yourself!**

We should at this point have a character which can move around freely withing our screen, so its time we spawn in our coins. Coins are just sprites that need to be spawned at a random point on startup so it only makes sense that we add the coin spawning code to the **OnLoad** method. 

```csharp
public override void OnLoad()
{
    // Previous Code
    player = new Sprite2D(new Vector2(100, 100), new Scale(100, 100),   Path.GetFullPath(@"Images\player.jpg") , "Player", 1);
    playerController = new PlayerController(player, speed);
    //
    // New Code - Coin spawning
    //
    for (int i = 0; i < 30; i++)
    {
       Sprite2D coin = new Sprite2D(new Vector2(rnd.Next(0, 1200), rnd.Next(0, 800)), new Scale(50, 50), Path.GetFullPath(@"Images\coin.jpg"), $"coin{i}");
    }
}
```
**Remember: rnd is of type System.Random so you will need to create a variable of type System.Random named rnd!**

Go ahead test it out, our coins are spawning in but you may have noticed that we cannot pick up/collect those coins, so how would we go about implementing the coin collection system? Well we will need to do some collision detection preferably on the **OnUpdate** method/event.

```csharp
public override void OnUpdate()
{
    // Previous Code
    playerController.Update();
    //
    // New Code - Collision detection
    // 
    GameObject collide;
   if (sprite.isColliding(out collide))
   {
        Sprite2D coin = (Sprite2D)collide;
        coin.DestroySelf();
   }
}
```
The code above checks every frame to see whether or not our player is colliding with something, if it is the collide is passed to the collide variable as a [GameObject](Core/Components/GameObject.md). Then we create a [Sprite2D](Core/Components/Sprite2D.md) named coin out of the [GameObject](Core/Components/GameObject.md) and destroy it, essentially removing it from the game.

The full code is available here:
```csharp
using System;
using System.Windows.Forms;
using MollyEngine;
using MollyEngine.Core;
using System.IO;
using MollyEngine.Extensions;

namespace MollyEngine
{
    public class DemoGame : Core.MollyEngine
    {
        Sprite2D sprite;
        ulong speed = 1;
        Random rnd = new Random();
        PlayerController playerController;

        public DemoGame() : base("New Game")
        {

        }

        public override void OnLoad()
        {
            sprite = new Sprite2D(new Vector2(100, 100), new Scale(100, 100), Path.GetFullPath(@"Images\player.jpg") , "Player", 1);
            playerController = new PlayerController(sprite, speed);
            for (int i = 0; i < 30; i++)
            {
                Sprite2D coin = new Sprite2D(new Vector2(rnd.Next(0, 1200), rnd.Next(0, 800)), new Scale(50, 50), Path.GetFullPath(@"Images\coin.jpg"), $"coin{i}");
            }
        }

        public override void OnUpdate()
        {
            playerController.Update();
            GameObject collide;
            if (sprite.isColliding(out collide))
            {
                Sprite2D coin = (Sprite2D)collide;
                coin.DestroySelf();
            }
        }

        public override void OnKeyDown(KeyEventArgs e)
        {
            playerController.OnKeyDownHandler(e);
        }

        public override void OnKeyUp(KeyEventArgs e)
        {
            playerController.OnKeyUpHandler(e);
        }
    }
}
```



