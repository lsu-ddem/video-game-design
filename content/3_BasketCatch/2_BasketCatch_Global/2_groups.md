---
title: Groups
weight: 2
---

By this point, you may have noticed that there are some inconsistencies with the behavior of our *Player*. Your *Player* may be getting removed from the game when an object hits its side. This is due to the *Player*'s hitbox being forced into the **Area2D** for a frame. Our code currently deletes any **PhysicsBody** that enters our **Area2D**, this includes the *Player*. We can stop this from happening by using **Groups** to categorize our nodes into nodes we want to delete and nodes we do not want to delete. We'll use two different groups to do this: One for the *Player* and one for the falling *Objects*.

Let's start with the *Player*. We'll go over to the *Player* scene, select the *root* node, and open the **Node** tab in the **Inspector** dock. At the top of the **Node** tab we see the option to view the node's **Groups**. If we click on *Groups* we can add the node to a group by pressing the "+" button at the top of the tab. When we press this a dialogue box will open where we can name the group, let's name this one "player" (careful with spelling here). We'll also select the "Global" option to make this a **Global** group.



<p align="center">
<video width="640" height="360" autoplay muted loop controls>
    <source src="../../../../media/BasketCatchImages/MakeGlobal/CreateGroup.mp4" type="video/mp4">
</video>
</p>

Go ahead and open the *Apple* scene by double clicking the "apple.tscn" file in the FileSystem. Then follow the same procedure to add the apple to a new group called "collectible". Make sure this is also a **Global** group.