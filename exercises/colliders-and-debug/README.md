# Colliders, Triggers and Debug.Log

**Remember:** If you ever need help, refer to https://docs.unity3d.com/ 

## A New Useful Tool to help you out: Debug.Log!

Debug.Log is a class that is already built into the Unity Framework to help developers with debugging code.  It is a simple action that will print code to the Console Window that we tell it to.  It is similiar to Console.log() in JavaScript.  

### But first, what is the Console Window?

The Console Window (menu: **Window > Console**) is a seperate window that shows us errors, warnings and other messages that are created by Unity.  Code that we use Debug.Log in will show up here in the Console Window.  

### How to use it

In any script, the easiest way to show an example of Debug.Log is to use it in the void Start action.  This way it'll always show our **Debug.Log** message on start. 

![Screenshot](https://raw.githubusercontent.com/junior-devleague/unity/master/exercises/colliders-and-debug/assets/Screen%20Shot%202017-08-21%20at%206.55.05%20PM.png)

This isn't the only use for it however, Debug.Log's main functionality is to help a developer debug so using it inside functions to figure out a compiling error is the best way for us to use it!

# Colliders 

## What are Colliders?

Colliders are simply components that define the shape of an object for physical collisions.  They do NOT need to the exact same shape as the object, and in fact, more often than not it's more efficient and not even noticeable during gameplay.  You will find out why mesh colliders sometimes aren't the best way to enable collisions.

Colliders, however, would be added to objects without a Rigidbody components to create floors, walls  and other motionless elements of a scene.  These would be called **static colliders**.  Collisions with objects that have Rigidbodies are called **dynamic colliders**.  Static Colliders and dynamic colliders can interact but since there aren't rigidbodies applied, they will not move in response to collisions.  

## The different types of Colliders

### Primitive
The simplest colliders to understand are the *primitive* collider types.  Just like there are primitive 3D Objects, surprise, there are primitive collider shapes which match the shape of the Object.  These are generally less cpu intensive, and in most instances can get the job done by putting multiple primitive colliders on an object which would create a compound primitive collider.  

### Mesh
Mesh colliders are much more complicated than primitive collider types.  The Mesh collider builds it's collision from the mesh that is attached to the game object, and reads the properties of the attached Transform to set the position and scale.  The benefit is that you can get more precise collisions with a collider that perfectly represents the GameObject.  

### What determines a Static Collider vs a Dynamic Collider vs a Kinematic Collider and what's the *difference?*

Static Colliders and Dynamic Colliders come down to differences so large that Unity has to update both colliders differently.  The difference between the two comes down to whether the specific GameObject has the "Rigidbody" component.  Doing so will let Unity know that this is a **Dynamic Collider** while those that do not have Rigidbody will be considered **Static Colliders**.  **Dynamic Colliders** like a player,  are *expected* to move thus any transformations aren't stored or updated every frame. 

**Static Colliders** on the other hand *aren't* expected to move, thus Unity is able to make useful optimizations based on this assumption.  However, if Static Colliders are moved during gameplay, Unity's physics engine will have to make extra computations which will cause a major drop in performance.  **It is recommended, to *never* move a Static Collider**

**Kinematic** Colliders are a special case, but one that will be used in completing the Roll-A-Ball tutorial.  A **Kinematic Rigidbody Collider** is a Collider that has a Rigidbody component and has the *is Kinematic* property checked.  While the collider *is* dynamic by technicality and is expected to move, it does not respond to collisions and forces like a **Dynamic Collider**.  Kinematic Rigidbodies are used for colliders that can be moved or disabled/enabled occasionally but otherwise, behave like static colliders.  A good example is a sliding door.  Normally it acts an a immovable physical obstacle, but when necessary can be opened and passed through.  

# Triggers

## Now, what are Triggers?

When you are looking for two Objects to overlap **without** creating a collision, that is a **Trigger**.  Colliders and Triggers are similiar in the sense that the Unity Engine is listening for two objects' colliders to pass into eachother.  However, a collider configured as a trigger (by using the **is Trigger** property) will not behave as a solid object and will simply allow other colliders to pass through it.  Trigger events, however, are only senf is one of the Colliders has a Rigidbody component attached.  

Collision detection only happens when a GameObject with Rigidbody **collides** with a true Collider.  With a **Trigger** however, a GameObject doesn't **need** to collide with a collider to activate.  You could imagine this as a spot in front of a door, if the player steps into this spot, the door opens and a cutscene occurs.  Or perhaps there's a boss battle that triggers but only **after** the player steps into a certain area.

## What are the different types of Triggers?

There are three main types of triggers we will be discussing and they are **OnTriggerEnter()**, **OnTriggerStay()**, and **OnTriggerExit()**.  

### How do they work?

#### OnTriggerEnter ()

OnTriggerEnter is called when the collider called "other" enters the trigger.  You can set this up so that 

#### OnTriggerStay ()

#### OnTriggerExit ()

