# Guide to Picking Up Items using Raycasting!

What is Raycasting? 
Raycasting is a commonly used operation starting from a point of origin in which a line is sent out in a specific direction. The idea behind it is that specific ray checks for any colliders in it's path.  This is useful for things such as shooting a gun, determining player line of sight with AI, creating lasers, or determining a distance from a collider.

This guide is going to show you how to create a simple Raycast from a FPSController that'll show us our line of sight, we can then use that line of sight to interact with other objects.

# The Steps

1. Create a new Project, name is  "Raycast_Practice"

2. Create a quad to be used as a floor, rotate it 90 degrees and expand it by about 20 on x and y

3. Import the Charcater standard asset package and drop the FPSController into your scene.

4. Create a new Cube, set it nearby your character. 

5. Create a custom tag for the cube, call it "Interactive" and set the tag for the cube.

6. Next, add a Rigidbody component to the cube.

7. Select the main camera in your screen and attach a new C# Script component called "LineOfSight"
![ScreenShot](https://raw.githubusercontent.com/junior-devleague/unity/master/exercises/RayCasting/assets/LineOfSight%20example.png)

8. Open the LineOfSight script in your editor. Here's a snippet of the code you can follow.
![Screenshot](https://raw.githubusercontent.com/junior-devleague/unity/master/exercises/RayCasting/assets/Line%20OF%20Sight%20Code.png)

Explanation:

**Declaring Variables in Script:**
The first thing our script is doing is declaring four variables: RaycastHit, float, bool, rigidbody. We will use all of these to dictate our logic. In the Start function, we assign our boolean and our float values to their default values. This will happen when the game starts.

**This is the first line in our Update function:**

 Debug.DrawRay(Camera.main.transform.position, Camera.main.transform.forward * rayLength, Color.red, 0.5f);

All this does is draw a Red line in our Scene View every frame that our game is running. The first parameter specifies the position where it starts, the second parameter is the direction it moves towards, the third parameter specifies the ray color, and the fourth parameter specifies the duration that the line is drawn on the screen. We do this primarily for debugging purposes. It allows us to actually see our raycast in our Scene View. 

**Next, let’s look at what actually causes the raycast to happen:**

if(Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out vision, rayLength))

This if statement essentially executes if a Raycast hits something. The condition for the if statement consists of a Physics.Raycast constructor, which takes four parameters in this example. The first parameter is the position the raycast starts at, which we specify as our camera position. The second parameter is the direction the raycast goes towards, which we specify as the forward direction of our camera. This ensures that wherever we look, the Raycast looks as well. The third parameter is the hit info parameter. It will provide further information about the raycast collision to the variable that we specify. In this example, we specify our RaycastHit variable called vision as the hit info argument. This means that our vision variable will contain collision information about the object that our Raycast hits. Lastly, the fourth parameter is the length of the raycast, which we specify as rayLength. We assigned rayLength in the Start function. It’s a public variable so we can modify it in the Inspector if we want to test different ray lengths.

**Inside our raycast statement, we have a nested if statement that determines the tag of the object our raycast is hitting:**

if(vision.collider.tag == “Interactive”)

 If the object is tagged as “Interactive”, which we setup earlier, then we will execute something.

Debug.Log (vision.collider.name);

This line is simply outputting the name of the object we’re looking at to our Unity console. If we had some sort of UI Text display, we could easily print out the name of the object onto our UI display. 

Next, we have yet another nested if statement that only gets executed if we’re looking at an Interactive object:

if(Input.GetKeyDown (KeyCode.E) && !isGrabbed)

If our player is looking at an interactive object, this statement will allow the player to press E on the keyboard and execute something but only if we are NOT already grabbing something. So, once our player presses E and is allowed to pick up an object, we execute this code:

grabbedObject = vision.rigidbody;

grabbedObject.isKinematic = true;

grabbedObject.transform.SetParent (gameObject.transform);

isGrabbed = true;

We assigned grabbedObject to the rigidbody of the object that our raycast is hitting. Keep in mind this ONLY happens if we are looking at something tagged as Interactive. Remember that vision is our RaycastHit variable, which contains collision information about what our raycast is hitting. Next, we set the grabbedObject to kinematic, which disables physics interactions on the object. This will allow our player to pick up and move the object without it being affected by rotations, gravity, etc. After that, we set the parent of our grabbedObject to our main camera. This allows the grabbed object to move relative to our main camera. Lastly, we set isGrabbed to true so that our game knows that we are in possession of an object.

**After that if statement, we have an else if statement:**

else if(isGrabbed && Input.GetKeyDown(KeyCode.E))

**This statement looks to see if the player is holding an object and if they press the E key. If both are true, then we drop the object by executing the following code within the if statement:**

grabbedObject.transform.parent = null;

grabbedObject.isKinematic = false;

isGrabbed = false;

First, we set grabbedObject’s parent back to nothing so that it is no longer a child of our camera. Then, we set it to non-kinematic so that it interacts with physics again. Lastly, we set isGrabbed to false so that we can pick up another object if we want.

Step 9. Save your game and play test it, you should be able to visually see your line of sight and interact with the cube by picking it up and dropping it.  
