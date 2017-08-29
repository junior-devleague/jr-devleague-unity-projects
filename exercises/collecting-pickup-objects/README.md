# Creating GameObjects to make them Pick Ups

This is going to give you the quick rundown of how to create Pick Up Objects and get them to work properly.

# The Steps

1. Create a new GameObject cube and reset it to Origin.  Rename it to "Pick Up".  Then, move it to a space a little away from the player.

**Remember:** Everything has colliders that tell us when there can tell us where there has been an interaction.  This is found in the **Colliders** components in the GameObject. 

2. Lift the Pick Up Object by .5 on y
   Adjust the Pick Up Object's x, y, z Scale to .5
   Then, **rotate** the cube by 45 degrees on the x, y, and z.
   
3. Create a new script in your script folder called "Rotate".  This is going to rotate the objects a certain degree per second.  It should look like this.


   

Open the PlayerController Script.

  In the Script, under FixedUpdate add a function called OnTriggerEnter(Collider other)
