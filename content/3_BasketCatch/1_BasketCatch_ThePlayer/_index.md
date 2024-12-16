---
title: Making the Player
weight: 1
---

We'll start by making our player, a basket that can move left and right at the bottom of the screen that can catch the falling fruit.

We'll start by making a new scene for our player by clicking the "+" on the scenes dock:

![Make a new scene](../../media/BasketCatchImages/Making-the-Player/NewScene1.png)

Once we make the scene we'll need to select the proper root node. Let's take a second to think about the needs of this scene. The player will be controlling this scene directly through inputs. Think about the nodes that move, and think about which of those nodes allows for direct control. What node should be the root node for the player scene?

<details style="background-color:rgba(92, 184, 92, 0.25);">
<summary style = "cursor:pointer">Reveal Answer</summary>

- CharacterBody2D

</details>






Once you've added your node make sure to rename it to "Player" before doing anything else. Then save your scene.

Let's do some file management as well, go ahead and make a new folder in your filesystem (you can do this by right clicking "res://" and selecting Create New->Folder) and name it "Player". This is where we'll store all of the assets and files we make associated with this scene. Go ahead and drag and drop your player scene into this new folder. Your filesystem should look like this currently:

![The FileSystem](../../media/BasketCatchImages/Making-the-Player/basket-filesystem-1.png)

Before we do anything else we'll need to go online to find some assets. We'll need an image to represent our player. This could be anything you'd like, remember this is an **Aesthetic** choice. Keep in mind that the player is going to catch things falling from the sky. You can use Google Image Search or [Open Game Art](https://opengameart.org) to find a suitable image. In our example we'll use a basket.


Once you find your image, go ahead and download it. Make sure that it has a **transparent** background. If it is a .png or .jpeg file you can use a tool like [remove.bg](https://www.remove.bg/) to make the background transparent. Once you've downloaded your **transparent** image, we'll bring it into Godot by dragging it from our computer's file system into the Godot editor. Make sure to move it into the "Player" folder once you've imported the file.


<p align="center">

<img src="../../media/BasketCatchImages/Making-the-Player/file_import_gif.gif" width="852" height="480" />

</p>




Next let's add some more nodes to our scene. We'll need to add two nodes, one to display an image and another to define the shape of our player. What would these nodes be? Be careful when adding these new nodes, they should both be direct *children* of the root node.

<details style="background-color:rgba(92, 184, 92, 0.25);">
<summary style = "cursor:pointer">Reveal Answer</summary>

- Sprite2D (Image)

- CollisionShape2D (Shape)

![Player Node Structure](../../media/BasketCatchImages/Making-the-Player/player-node-structure-1.png)


</details>


Depending on the size of your image you may need to resize it. You can do this by clicking the **Sprite2D** and changing the *Scale* property in the **Inspector**. We'll need to modify the shape of our CollisionShape2D to fit over our image properly. Let's click on the "CollisionShape2D" in the scene tree and change its "Shape" property in the **Inspector**. Let's go ahead and select a *RectangleShape2D* and align it with our image.!


<p align="left">
<video width="640" height="360" autoplay muted>
    <source src="content/media/BasketCatchImages/Making-the-Player/collision-shape-vid-1.mp4" type="video/mp4">
</video>
</p>