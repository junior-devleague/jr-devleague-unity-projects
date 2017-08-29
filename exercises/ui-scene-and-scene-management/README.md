# The UI, Scene, and Scene Management

This repo will be going over the basics to Scenes, how to overlay a UI onto a scene, and how to manage different scenes.  Next, will be a step-by-step process on creating a canvas and UI for Roll-A-Ball.

## REMEMBER!

If you have questions, refer to: https://docs.unity3d.com/Manual/index.html **ALWAYS!**

## The UI Overlay

The UI is the GameObject that holds all of the information relevant to the player.  This would include life, score, points, kills, ammo in your weapon, or how fast you're going in a racing game.  If you've ever seen a video game being played, you understand how crucial having a UI is. 

In Unity, a UI is controlled by a GameObject called the **Canvas**.  This is the **parent** GameObject, and anything mentioned earlier goes inside of the Canvas.  It *is* possible to have more than one canvas per scene.

Inside of the canvas are Elements that are considered the **children**.  These Elements will control and respond to parts of a game but are handled inside the Canvas.  

## The Scene

Scenes aren't only used for displaying a game.  Scenes can also compose the Menu, and restart functions as well.  I.E. When you start a game, you don't automatically load into the game.  You start at a menu screen where you can hit "Play" to load the first scene of a game, enter the Options screen, or Quit the game.  There are many different scenes that compose one project/game.  

## Scene Management

Unity has built in tools that allow you to control through scripting Scene load order.  through the scene manager you can handle Multi-Scene editing, Merging scenes or you can even copy from one to another scene.  

# Okay, Guide Time!

Open up your Roll-A-Ball project.  Before you begin this portion, make sure that you have these checked off:
- There is a solid floor for the player to roll on
- There is a player with a movement script attached that can move the ball around
- There are objects that dissapear when touched - is Kinematic

Okay, once you have those, let's move on!

1. Open the playerController script for editing:

2. Add a new private int variable called count
  ![Screenshot](https://github.com/junior-devleague/unity/blob/master/exercises/ui-scene-and-scene-management/assets/Screen%20Shot%202017-08-28%20at%2010.49.12%20PM.png)
  
3. Then, in void Start () set the count to 0.
  ![Screenshot](https://github.com/junior-devleague/unity/blob/master/exercises/ui-scene-and-scene-management/assets/Screen%20Shot%202017-08-28%20at%2010.50.39%20PM.png)
  
4. And lastly, inside OnTriggerEnter () **AFTER** it sets the GameObject to false, add count plus 1 like so:
  ![Screenshot](https://github.com/junior-devleague/unity/blob/master/exercises/ui-scene-and-scene-management/assets/Screen%20Shot%202017-08-28%20at%2010.51.31%20PM.png)
  
5. Now, create a new UI Text element from Hierarchy's create menu.
 ![Screenshot](https://raw.githubusercontent.com/junior-devleague/unity/master/exercises/ui-scene-and-scene-management/assets/Screen%20Shot%202017-08-28%20at%2010.57.47%20PM.png)
  
6. Rename the text element to "Count Text", and then anchor the text element in the top-left hand corner.  To do so looks like this:
 ![Screenshot](https://raw.githubusercontent.com/junior-devleague/unity/master/exercises/ui-scene-and-scene-management/assets/Screen%20Shot%202017-08-28%20at%2011.05.13%20PM.png)
 
7. Open up the PlayerController script again. At the top near line 1 where it says "using UnityEngine" and "using System.Collections" add "using UnityEngine.UI".  This tells Unity that we will be using Unity's UI toolset.

8. Create a new public Text variable, name it countText.  This will be a reference to the UI Text component we made earlier.

9. Create a new function under OnTriggerEnter that will set our countTexts' count.

![Screenshot](https://raw.githubusercontent.com/junior-devleague/unity/master/exercises/ui-scene-and-scene-management/assets/Screen%20Shot%202017-08-28%20at%2011.33.20%20PM.png)

10. Call SetCountText inside of our void start and OnTriggerEnter

11. Next, drag the count text UI element into the public "Count Text" inside the player controller script.

12. Now, create a new text UI element for when we win the game.  Rename it to "Win Text".  Then adjust the Font size to 24.

13. Adjust the rect transform's **pos y** value, to raise the text a little bit higher and out of the center. Use value **75**.

14. Now, go back to the **player controller** script again and create a new public variable called "winText"

15. In void start (), set the winText.text to an empty string for now.  We don't want it to display in our game until we've won.  

16. Now, in our SetCountText function, make a conditional statement that says "if count is >= (your amount of Pick Ups), then display winText.text is 'You've Won!'".  It should look like this:

![Screenshot](https://raw.githubusercontent.com/junior-devleague/unity/master/exercises/ui-scene-and-scene-management/assets/Screen%20Shot%202017-08-28%20at%2011.33.52%20PM.png)


