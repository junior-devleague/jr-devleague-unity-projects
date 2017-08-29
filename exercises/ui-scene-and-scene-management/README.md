# The UI, Scene, and Scene Management

This repo will be going over the basics to Scenes, how to overlay a UI onto a scene, and how to manage different scenes.  Next, will be a step-by-step process on creating a canvas and UI for Roll-A-Ball.

## REMEMBER!

If you have questions, refer to: https://docs.unity3d.com/Manual/index.html **ALWAYS!**

## The UI Overlay

The UI is the GameObject that holds all of the information relevant to the player.  This would include life, score, points, kills, ammo in your weapon, or how fast you're going in a racing game.  If you've ever seen a video game being played, you understand how crucial having a UI is. 

In Unity, a UI is controlled by a GameObject called the **Canvas**.  This is the **parent** GameObject, and anything mentioned earlier goes inside of the Canvas.  It *is* possible to have more than one canvas per scene.

Inside of the canvas are Elements that are considered the **children**.  These Elements will control and respond to parts of a game but are handled inside the Canvas.  

## The Scene

Scenes aren't only used for 

# Okay, Guide Time!

Open up your Roll-A-Ball project.  Before you begin this portion, make sure that you have these checked off:
- There is a solid floor for the player to roll on
- There is a player with a movement script attached that can move the ball around
- There are objects that dissapear when touched - is Kinematic

Okay, once you have those, let's move on!

- Open the playerController script for editing:
  - Add a new private int variable called count
  - 
