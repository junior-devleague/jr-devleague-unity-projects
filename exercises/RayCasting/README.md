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

8. Open the LineOfSight script in your editor. Here's a snippet of the code you can follow.
[Screenshot]()
