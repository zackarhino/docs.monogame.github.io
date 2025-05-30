---
title: Understanding the Code
description: This tutorial will go over the code that is generated when you start a blank project.
---

> [!NOTE]
> For help with creating a project, please look at the Creating a New Project section of the [Getting Started guide](index.md).

Within the `Game1.cs` class file, which is the core of any MonoGame project, you will find several critical sections necessary for your game to run:

- `Using statements` - which provide easy access to the various components of MonoGame.

- The `Game` Class definition - the heart of any MonoGame project.

- The `Game constructor` and key variables - which tell the project how to start.

- The `Initialize` method - to initialize the game upon its startup.

- The `Load and Unload Content` methods - which are used to add and remove assets from the running game from the [Content project](4_adding_content.md).

- The `Update` method - which is called on a regular interval to update your game state, e.g. take player inputs, move ships, or animate entities.

- The `Draw` method - which is called on a regular interval to take the current game state and draw your game entities to the screen.

Read further for more details and examples while looking through the code of your new project.

---

## Using Statements

```csharp
using Microsoft.Xna.Framework;
using Microsoft.Xna.Framework.Graphics;
using Microsoft.Xna.Framework.Storage;
using Microsoft.Xna.Framework.Input;
```

These using statements make it easier to use the code that MonoGame has to offer.

> They are prefixed with Microsoft.Xna.Framework because MonoGame is an open source re-implementation of Microsoft's XNA framework, and in order to maintain compatibility with the XNA code, it uses the same namespaces.

## The Game1 Class

```csharp
public class Game1 : Game
```

The main `Game1` class inherits from the `Game` class, which provides all the core methods for your game (ie. Load/Unload Content, Update, Draw etc.). You usually only have one Game class per game, so its name is not that important.

## Instance Variables

```csharp
GraphicsDeviceManager graphics;
SpriteBatch spriteBatch;
```

The two default variables that the blank template starts with are the `GraphicsDeviceManager` and `SpriteBatch`. Both of these variables are used for drawing to the screen, as you will see in a later tutorial.

## Constructor

```csharp
public Game1()
{
    graphics = new GraphicsDeviceManager(this);
    Content.RootDirectory = "Content";
    IsMouseVisible = true;
}
```

The main game constructor is used to initialize the starting variables. In this case, a new `GraphicsDeviceManager` is created, the root directory containing the game's content files is set, and the mouse cursor is set to visible.

## Initialize Method

```csharp
protected override void Initialize()
{
    // TODO: Add your initialization logic here

    base.Initialize();
}
```

The `Initialize` method is called after the constructor but before the main game loop (Update/Draw). This is where you can query any required services and load any non-graphic related content.

## LoadContent Method

```csharp
protected override void LoadContent()
{
    // Create a new SpriteBatch, which can be used to draw textures.
    spriteBatch = new SpriteBatch(GraphicsDevice);

    // TODO: use this.Content to load your game content here
}
```

The `LoadContent` method is used to load your game content. It is called only once per game, within the `Initialize` method, before the main game loop starts.

## Update Method

```csharp
protected override void Update(GameTime gameTime)
{
    if (GamePad.GetState(PlayerIndex.One).Buttons.Back == ButtonState.Pressed || Keyboard.GetState().IsKeyDown(Keys.Escape))
        Exit();

    // TODO: Add your update logic here

    base.Update(gameTime);
}
```

The `Update` method is called multiple times per second, and it is used to update your game state (checking for collisions, gathering input, playing audio, etc.).

## Draw Method

```csharp
protected override void Draw(GameTime gameTime)
{
    GraphicsDevice.Clear(Color.CornflowerBlue);

    // TODO: Add your drawing code here

    base.Draw(gameTime);
}
```

Similar to the Update method, the `Draw` method is also called multiple times per second.  This, as the name suggests, is responsible for drawing content to the screen.

---

## Next Steps

Next, learn how to add and import content into your game project:

- [Adding Content](4_adding_content.md)
