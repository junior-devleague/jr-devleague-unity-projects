# Creating GameObjects to make them Pick Ups

This is going to give you the quick rundown of how to create Pick Up Objects and get them to work properly.

# The Steps to Creating A New Pick Up Object

1. Create a new GameObject cube and reset it to Origin.  Rename it to "Pick Up".  Then, move it to a space a little away from the player.

      **Remember:** Everything has colliders that tell us when there can tell us where there has been an interaction.  This is found in        the    **Colliders** components in the GameObject. 

2. Lift the Pick Up Object by .5 on y
   Adjust the Pick Up Object's x, y, z Scale to .5
   Then, **rotate** the cube by 45 degrees on the x, y, and z.
   
3. Create a new script in your script folder called "Rotate".  This is going to rotate the objects a certain degree per second.  It should look like this.

![Screenshot](https://raw.githubusercontent.com/junior-devleague/unity/master/exercises/collecting-pickup-objects/assets/Screen%20Shot%202017-08-28%20at%209.04.15%20PM.png)

    transform.Rotate - directly changes the Rotate in the transform component.  
    new Vector3 (15, 30, 45) - These are float variables that will directly override the Rotate numbers in each GameObject
    Time.deltaTime - The time between the current frame and the last frame.  This will ensure that the transitions are smooth and          FrameRate independant.

4. Apply the script to the GameObject, hit play to watch it rotate.  If there are any errors, reread the script and try to debug the issue.

5. Create a new folder and name it **Prefabs** in the projects window.  Create a new empty Prefab from **Assets > Create > Prefab**, then drag the pick up cube into the empty prefab to save it and it's properties for later use.  

   Optionally, you can just simply drag the Pick Up GameObject directly into the Prefab folder.
   
6. Next, let's create a few more by duplicating the Pick Up GameObject.  Duplicate by either going to **Edit > Duplicate** or using the HOTKEY **'CMD + D' on Mac or 'CTRL + D' on Windows**.   Place them around the map.

7. Now, change the color of the Pick Up object.
   
# Now, to Collect Them

1. Check mark the Pick Up GameObject's Collider is Trigger property.  **Remember:** Triggers is only used for triggering events and activated GameObjects are ignored by the physics engine.
 
2. Create a custom tag for our Pick Ups called "Pick Up", set the Pick Up Prefabs tag to it.

3. Open up the PlayerMove script.  At the bottom under fixedUpdate, make a new void OnTriggerEnter(Collider other) function.  This function is going to handle the trigger collision when the player comes in contact with the triggers on the Pick Up gameObject. 

     The function should look something like this:

![Screenshot](https://raw.githubusercontent.com/junior-devleague/unity/master/exercises/collecting-pickup-objects/assets/Screen%20Shot%202017-08-28%20at%208.57.00%20PM.png)

          Other.gameObject is simply the Collider that's passed in as the parameter.  It's whatever gameObject the player has touched and activated the fucntion with.  
          if (other.gameObject.CompareTag("Pick Up")) is simply saying check the tag of the other gameObject, if it's "Pick Up" then run the next function.
          SetActive(false) is the scripting way of deactivating a gameObject in the scene.

4. Now, apply a "Rigidbody" component to our Pick Up Prefab and check mark the "is Kinematic" property in the GameObject.  This helps optimize Unity so it isn't making so many calculations.

Happy Coding! Refer back to here if you have any questions.
