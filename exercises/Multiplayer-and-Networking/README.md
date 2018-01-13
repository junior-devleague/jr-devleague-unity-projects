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

6. Add a "Cube" GameObject as a child to the Player.  This is going to act as a "Visor" so we can see where our player is facing.
   Transform.position (0, .5, .24), Transform.scale (.95, .25, .5)
   
7. Create a new Material, color it black and attach it to the visor.

8. Add the "Network Identity" component to our Player GameObject.  Checkmark the "Local Player Authority"

### Network Identity
The NetworkIdentity component controls an object’s network identity, and it makes the networking system aware of it.  With the Unity Network System, networked objects with NetworkIdentities are "spawned” by the server using NetworkServer.Spawn(). This causes them to be assigned a NetworkInstanceId and be created on clients that are connected to the server.

Scene objects are treated a bit differently than dynamically instantiated objects. These objects are all present in the scene on both client and server.  When the client connects to the server the server tells the client which scene objects should be enabled and what their most up to date state information is through spawn messages.  This ensures the client will not contain objects placed at incorrect locations when they start playing, or even objects which will be deleted immediately on connection because some event removed them before the client connected. The Server Only checkbox will ensure this a particular object will not be spawned or enabled on clients.

The local player authority setting allows this object to be controlled by the client that owns it - the local player object on that client has authority over it. This is used by other components such as NetworkTransform.

This component contains tracking information like what scene ID, network ID and asset ID the object has been assigned. The scene ID is valid in all scene objects with a NetworkIdentity component. The network ID is the ID of this particular object instance, there might be multiple objects instantiated of a particular object type and the network ID is used to identity which object.

9. Add the Player as a "prefab".  In the Network Manager, open "Spawn Info" and then drag the Player GameObject to "Player Prefab".

10. Create a new C# script, this will be our player movement script.  

In void update: Create new float variables called horizontal and vertical.  Using the Input Manager, grab the horizontal and vertical axis and store them inside each variable respectively.  Multiply the horizontal axis by Time.Deltatime * 150.0f and the Vertical by Time.DeltaTime * 3.0f.  Then, use transform.Rotate by (0,horizontal,0). And finally, use transform.Translate (0, 0, vertical)

It should look like this:

![ScreenShot](https://raw.githubusercontent.com/junior-devleague/unity/master/exercises/Multiplayer-and-Networking/Assets/Screen%20Shot%202018-01-12%20at%208.54.46%20PM.png) 

