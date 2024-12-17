---
title: Making a Global Script
weight: 1
---

Often we'll want to have a script that we can access from anywhere in our project that does not get deleted from scene to scene. This kind of script, often called a **Singleton** or in Godot terms an **Autoload**, is very powerful and allows us to store and manipulate data game-wide. We'll use these kinds of scripts for any multi-stage game, any game with persistent data, and any game that uses UI to communicate the state of the player. Let's start by creating our global script.

We'll create a new script by going to the **FileSystem**, right-click **res://** and selecting *Create New -> Script*. We'll rename this script "Global". Next, we'll go to the **Project Settings** and select the **Globals** tab. Then we'll select our "Global" script by pressing the folder icon next to the "Path" text field. This will open a dialogue where we can select our script. Once we've selected the "Global" script we'll click "+Add" to make the script a **Global** script.

<p align="center">
<video width="640" height="360" autoplay muted loop controls>
    <source src="../../../../media/BasketCatchImages/MakeGlobal/MakingGlobal.mp4" type="video/mp4">
</video>
</p>
