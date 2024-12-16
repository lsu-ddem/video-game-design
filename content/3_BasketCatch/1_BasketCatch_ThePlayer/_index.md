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


Depending on the size of your image you may need to resize it. You can do this by clicking the **Sprite2D** and changing the *Scale* property in the **Inspector**. We'll need to modify the shape of our CollisionShape2D to fit over our image properly. Let's click on the "CollisionShape2D" in the scene tree and change its "Shape" property in the **Inspector**. Let's go ahead and select a *RectangleShape2D* and align it with our image.


<p align="center">
<video width="640" height="360" autoplay muted>
    <source src="../../media/BasketCatchImages/Making-the-Player/collision-shape-vid-1.mp4" type="video/mp4">
</video>
</p>


In order for us to move our player we'll need to add a script. Go ahead and click on the player and press the *attach script* button. We'll select the "CharacterBody2D: Basic Movement" template as a starting place. If we've already named our **Root Node** the default script name will be the name of that node! Make sure once you've made the script that it is in your "Player" folder. We'll need to modify this script to make our player behave how we expect it to. 

![New Script Dialogue Box](../../media/BasketCatchImages/Making-the-Player/Player-script.png)


After you've saved everything let's try running the current scene to see what happens. Does the player act as you expect?


<details style="background-color:rgba(92, 184, 92, 0.25);">
<summary style = "cursor:pointer">Reveal Answer</summary>

- The player should fall straight down. However, you should be able to move the player to the left and right slightly.

</details>


Let's close our game and go back to the **Script** view. In the **Script** view we'll see the default movement code. We'll need to modify this code so that our player will only be able to move left and right, not up and down. Below is the code:

```
extends CharacterBody2D


const SPEED = 300.0
const JUMP_VELOCITY = -400.0


func _physics_process(delta: float) -> void:
	# Add the gravity.
	if not is_on_floor():
		velocity += get_gravity() * delta

	# Handle jump.
	if Input.is_action_just_pressed("ui_accept") and is_on_floor():
		velocity.y = JUMP_VELOCITY

	# Get the input direction and handle the movement/deceleration.
	# As good practice, you should replace UI actions with custom gameplay actions.
	var direction := Input.get_axis("ui_left", "ui_right")
	if direction:
		velocity.x = direction * SPEED
	else:
		velocity.x = move_toward(velocity.x, 0, SPEED)

	move_and_slide()


```


First, let's get rid of any references to moving on the **y-axis**. The **property** *velocity* tells the CharacterBody2D how many pixels to move per second, we can see that *velocity* is referenced throughout this script, sometimes followed by a **.y** or **.x**. These lines only modify the *velocity* on that axis. We also see a line that references *gravity*, this line is applying a constant downward force on our player. Let's go ahead and remove all of the lines that include *velocity.y* or *gravity*. (Hint: Make sure to remove any *if* statements that are empty after deleting code.)


<details style="background-color:rgba(92, 184, 92, 0.25);">
<summary style = "cursor:pointer">Reveal Answer</summary>

```
extends CharacterBody2D


const SPEED = 300.0
const JUMP_VELOCITY = -400.0


func _physics_process(delta: float) -> void:

	# Get the input direction and handle the movement/deceleration.
	# As good practice, you should replace UI actions with custom gameplay actions.
	var direction := Input.get_axis("ui_left", "ui_right")
	if direction:
		velocity.x = direction * SPEED
	else:
		velocity.x = move_toward(velocity.x, 0, SPEED)

	move_and_slide()


```

</details>

