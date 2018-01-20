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

11. Save your work

12. Now, to differentiate between our player and another player, we're going to make our local player blue. To do this, inside of teh playercontroller script, add this to the bottom of the script.

![ScreenShot](https://raw.githubusercontent.com/junior-devleague/unity/master/exercises/Multiplayer-and-Networking/Assets/Screen%20Shot%202018-01-12%20at%209.39.31%20PM.png)

Public override void is a method that allows a local function to override features that are already provided by a superclass.  In this case, NetworkBehaviour.

# If you don't understand everything that's happened so far, review and grok! 

13. Create a new sphere GameObject, adjust the scale to .2, .2, .2.  This is going to be our bullet.

14. Add a Rigidbody component and disable the "Use Gravity" property.

15. Make it a Prefab for later use.  

16. Open up the PlayerController Script again

   Create a public GameObject variable called bulletPrefab, and a public Transform called bulletSpawn.
   
   bulletPrefab will hold the bullet we just created and the Transform is going to dictate where it spawns from. i.e. Our gun.

17. Create a new if statement that will listen for our Spacebar input (alternatively, you can use your mouse 1 if you want to) that will ru a method called fire();

18. Create the new method called fire();
   
   This method is going to instantiate a bullet from our bulletSpawn with the bullets rotation.  
   
   It will add a velocity to our bullet 
   
   And Then destroy the bullet after 2 seconds (Objects not destroyed will continue to stay in motion and will eventually take up too much space)
   
   ## Try to make the script on your own
   
   Otherwise, it should look something like this:
   
   ![ScreenShot](https://raw.githubusercontent.com/junior-devleague/unity/master/exercises/Multiplayer-and-Networking/Assets/Screen%20Shot%202018-01-12%20at%2010.50.20%20PM.png)
   
   ![ScreenShot](https://raw.githubusercontent.com/junior-devleague/unity/master/exercises/Multiplayer-and-Networking/Assets/Screen%20Shot%202018-01-12%20at%2010.51.47%20PM.png)
   
19. Create a gun as a child of our player.  You can use a cylinder for basic purposes or you may find a gun from the asset store, there are plenty of free ones.  

**Be sure to remove the collider from the gun as bullets that are spawned will collide with the gun and be destroyed**

20. Create an empty game object which will be our bullet spawn point.  Place this at the edge of your gun.

21. Place the bullet GameObject and bullet spawn into our public variables for our playercontroller script.

22. Save your game and test.  You should be able to shoot your bullets.  However, your bullets will not by synced up over the network.

23. Add the "Network Transform" component to the bullet so our Network Manager is made aware of the bullet.  Decrease the network send rate to 0.

24. Next, click the Network Manager GameObject and look for "Registered Spawnable Prefabs" Add a new entry and drag our bullet prefab into it.  

25.  Go back to the Playercontroller script, we will need to make some changes to our Fire script.
      Currently, our Fire script is only on our local build, it isn't being registered on our server.  So we need to create a command to our server.
      
      To do so, add an attribute above our fire method like so: 
      
      [Command]
      
      Cmdfire();
      
      Be sure to place CmdFire(); inside of our Input.GetKeyDown as well.
      
      What this is saying is "Run the command on this player instance on the server so that it may cross over into other local clients"
      
      Now, inside of the CmdFire() method, add a bullet spawn like so:

      NetworkServer.Spawn(bullet);

      Your code at the end should look something like this:

      ![ScreenShot](https://raw.githubusercontent.com/junior-devleague/unity/master/exercises/Multiplayer-and-Networking/Assets/Screen%20Shot%202018-01-12%20at%2011.37.52%20PM.png)

      If it compiles, the congrats! You can now shoot a gun over multiple clients through the server.

      Next we will be going over PlayerHealth and damaging the other player

26. Create a new C# script, call it playerHealth
         Instantiate a new public int "const" variable, call it maxHealth and set it to 100
         Create a new int variable called currentHealth and set it to maxHealth on start
         Create a new Public void method call TakeDamage, it should have a parameter of (int amount), inside, set currentHealth -= amount.
         Then create an if statement checking "if currentHealth <= 0", set currentHealth to 0.

         Here's what it will look like:
         
         ![ScreenShot]()
