# Creating a Menu Screen 

## Simple tutorial to teach you how to create a main menu screen that includes a background panel, a play and quit option.

# What you will need to know:
- Accessing the Asset Store and importing packages
- Creating and handling UI components
- Scripting

# The Steps!

1. Create a new project, go into the Asset Store and download the package called "Unity Samples: UI"

2. In the Prefab folder, drag the Asset "SF Scene Elements" into your Scene View

3. Create a new **panel** UI element, rename it to "MainMenuPanel" and set the anchor to about (.2, .75) min and(.25, .8) max.  Then reset the **left, Right, Top, and Bottom** to 0.  The **panel** element is going to be our holder for our Start and Quit buttons.

4. Inside the image component on our Panel UI Element, change the image to SF Window instead of the default

5. Then in the same component, change the color of the SF window to a different color (You can use the presets on the bottom, otherwise make your own color)

6. Create a new button element, rename it to "StartButton" and then make it a child of the MainMenuPanel element. (If transform isn't 0, reset it to Origin)

7. Change the color and where it says "highlighted" color, change that to a different color as well. Don't make it the same color!

8. Open the Button element and change the text to say "Start", next, change the font style to "Jupiter"

9. After, change the font size to 32.  If you did it correct, there shouldn't be anything in the button anymore.

10. Change both overflow options to "Overflow"

11. Next, highlight the MainMenuPanel Element and add a new "Vertical Layer Group" component. This will help us layer our buttons evenly.

12. In the Vertical Layer Group component, checkmark force expand horizontal and vertical and set the child alignment to "Middle Center"

13. Next, we can add about 70px of padding all around to push the buttons back into place.

14. Duplicate our current panel and call it "Help Panel".  DRAG IT OUT OF THE MAINMENUPANEL, IT IS NOT A CHILD OF THE MAINMENUPANEL, IT IS A CHILD OF THE CANVAS! <-- Later steps will not work if this hasn't changed. Then, Deactivate the MainMenuPanel.

14b. Go to the Main Menu Panel's transform, click the gear icon, copy the component.  Go to HelpPanel and paste the component in.  This will ensure the two panels stay the same.

15. Delete the different menu options except for the back option

16. Rename the single button to "Back" and change the text inside to "Back" as well.  

17. Inside the BackPanel, duplicate the text and move it outside.  Change the text to say "Help" as that will be the title.

18. Duplicate the text again and change the text to a Lorem Ipsum.  Google Lorem Ipsum to find one that you want to use.

19. Change the overflow on the text back to "Wrap" and "truncated" This will place the Lorem Ipsum paragraph back to regular format.

20. Save the scene

21. Go into the prefabs folder again, select scenes and drag the scene called "Controls" into your scene view.

22. Go to file/build settings and add both scenes to your build

23. Go back to your first "Start" button in your MainMenuPanel and add a new C# script to it called "LoadSceneOnClick"

24. Inside LoadSceneOnClick() add in a new function that's going to take the index of the scene in the build as a parameter and load the scene by it's index in the build settings.

It should look like this:

![ScreenShot](https://raw.githubusercontent.com/junior-devleague/unity/master/exercises/MainMenu/assets/Screen%20Shot%202017-10-18%20at%2012.48.47%20AM.png)

25. Go back to the Start Button UI Element and go to the On Click () Event Listing.

26. Where it says runtime only, drag and drop the LoadScene function and this will let you choose what function you want it to specifically run when you hit start.  *Now*, underneath, add in the index number you want to load, in this case it will be index "1" for the controller.

27. Save and test your game.  When you hit start, it should take you to the Controller Scene.

28. Next, go to your second button which should be labeled "HelpLabel" and go to the On Click () Event List.  Grab your MainMenuPanel and drop it into where it says "RunTime Only" this tells it we're going to target the entire panel.  Next to it, open it, highlight GameObject and click SetActive and leave the checkmark box unchecked.  This is the same thing as telling the GameObject's SetACtive to be false without coding it.

29. Create another On Click that will be called as well, drag the Help Panel into RunTime Only and set the GameObject to True.

30. Save and test your game.  You should be able to see your Help Panel when you hit Help.

31. Now, create and attach a new C# script to our quit button and call it "QuitOnClick" open it in our text editor.

32. Create a new public void function called "Quit" and create an if/else statement that quits game view if in editor, otherwise quits the application if not.  It should look like this:

![ScreenShot](https://raw.githubusercontent.com/junior-devleague/unity/master/exercises/MainMenu/assets/Screen%20Shot%202017-10-18%20at%2012.29.54%20PM.png)

33. Go to quitButton's On Click(), drag the QuitOnClick script into the Runtime and inside function drag QuitOnClick.Quit()

34. Save your game and test
