# Intro to Multiplayer Networking

With this simple Multiplayer Networking Example,  you will learn how to set up a Networked Multiplayer project from scratch using the simplest of assets and scripts. With this example, you should receieve a quick introduction to the most important aspects of the built-in Multiplayer Networking system and its High Level API.

Before you get started, it would be a good idea to take a look at Unity's docs for an overview of Networking and the High Level API which you can find here:

Networking Overview:https://docs.unity3d.com/Manual/UNetOverview.html?_ga=2.175619426.1574546648.1515808406-221234044.1501035519

High Level API: https://docs.unity3d.com/Manual/UNetUsingHLAPI.html?_ga=2.179296868.1574546648.1515808406-221234044.1501035519

## The Steps:

1. Create a new empty 3D Project.  Name it "Multiplayer_Test"

2. Save your default scene

3. Create a new empty GameObject, it doesnt matter what it is.  Rename the object to "NetWork Manager"

4. Find and add the components "NetWork Manager" and "NetWork Manager HUD"

### What is the NetWork Manager and Network Manager HUD?
   
The Network Manager controls the Network state of your Multiplayer project.  This includes game state management, spawn management, scene management, matchmaking and also allows access to debugging information.

The Network Manager HUD is an extension for the NetworkManager that displays a default HUD for controlling the network state of the game.UI

This is what it looks like:

![ScreenShot](https://unity3d.com/sites/default/files/002-networkmanager.png)

5. Create a new capsule GameObject and rename it to "Player"
