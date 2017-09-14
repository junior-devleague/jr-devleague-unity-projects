# Lighting

Possibly one of the best ways to make your game look polished and just overall alot better.  Unity models how light actually behaves and also follows the laws of physics in how light interacts with different materials.  In Unity 5, Unity uses a new feature called Real-Time Global Illumination(GI) which essentially blends direct and indirect light to make scenes realistic.

To study up more on GI, follow this link: https://docs.unity3d.com/Manual/GIIntro.html

## So, what does this mean?

In a new scene, Unity innately includes a default **Skybox** and Directional Light that is aligned with the skybox.  These two GameObject's will makeup most of the lighting in your scenes and we'll go over how to change them to our liking.  But there are a few more parts that control our lighting environment, the first of which is called **ambient light**.  Ambient Light, which you can find if you make the directional light inactive will always affect GameObjects added to a scene, unless you set the ambient intensity to 0.  

However, even though you set an ambient intensity to 0, GameObject's will still receive light information.  To completely remove all light from any GameObject, you must either 1) Deactivate the skybox or 2) set the Reflection Source to Custom.  

By turning off everything, you will notice that GameObject's won't have any light source.  

# Lighting

Just like real life, we need lighting otherwise our Cameras won't be able to see anything.  You can create multiple different light sources and you can make them by going into GameObject > Light > Light Source (Point Light, Directional Light, Spot Light, and Area Light) these four different lights can provide a different ambience of your choosing.  

Just like regular GameObjects, Light is a component of a GameObject and we can adjust the position of the light by moving the attached GAmeObject's position.

### Directional Light
Directional Lights are useful for creating effects like sunlight in your scene.  Directional Light can be like a light source that's very far away (like the sun) and doesn't have a source position so it can be placed anywhere in your scene.  
![ScreenShot](https://docs.unity3d.com/uploads/Main/Light-Direct.png)

Also, by pointing the directional light towards the sky, we can resemble nighttime on our map.  And by pointing our directional sideways, we can have it resemble a sunset.  If the directional light is selected as the ambient source, Ambient Lighting can be changed in relation to the colors.

### Spot Light
Spot Lights act exactly the same way SpotLights do in real life.  It puts down light over a specified location, but is constrained to a circle.

![ScreenShot](http://1.bp.blogspot.com/-aNV_XziDGXM/VZWEyUurY9I/AAAAAAAAEfI/7rS6wo_TVeU/s1600/light4b_5.jpg)

### Point Light
A Point Light is useful for recreating lights from lamps or even light from explosions in a simulated way.  A point light starts from a point in space and directs light out in an area evenly.  After a certain point, the light intensity will reach zero.

![ScreenShot](https://docs.unity3d.com/uploads/Main/Light-Point.png)

### Area Light
An Area Light is represented by a rectangle in Unity that emits light off of one side of the rectangle in a uniform mannor.  At further distances, the light will begin to taper off until eventually the intensity reaches zero.  Because Area Lights are more cpu intensive than the other lights, Area Lights can only be baked into lightmaps.  

### Ambient Light
Ambient Light, like mentioned above controls all global non-directional light in the scene.  Just like real-life, all objects can reflect light, and you are able to give your scene a different ambience by changing the color of the ambient lighting.  i.e. think Doom, where after lights are powered, there's that red ominous glow from shut down power.  That is controlled by ambient lighting.  For full control over lighting a scene, you would set the ambient lighting to black and you would only use Directional, Spot, Point, or Area Lights to control a scene.  

## Real time (dynamic) lighting vs Baking
By simply adding lights to our scene, we are essentially creating real time, dynamic lighting.  This is useful if lighting is going to be moving.  For example, if a car is driving at night, the headlights would be constantly moving and changing directions so baking wouldn't be ideal as Unity is constantly recalculating.

Baking, on the other hand is used for memory and processor power saving by baking the lights into a scene and saving it as a texture thus saving Unity the trouble of recalculating.  If lights aren't expected to move, we can bake the lighting in, thus giving Unity the chance to actually *look* more realistic than Dynamic lighting.  Baking should be used whenever possible, simply to save Unity the processing power and Unity can render lights in a more realistic fashion.  

![ScreenShot](http://answers.unity3d.com/storage/temp/58065-shadowbaking-problem.jpg)

# SkyBox
A Skybox is one of the most impactful ways to change our scene.  A Skybox is essentially just a wide panorama shot that, when applied is an easy way to add realism to a scene without putting your graphics under a huge load.  When creating a new scene, Unity has a default Skybox, which, if you look up is essentially just a blue sky with a single point of light.  There aren't any clouds so there really isn't much use of reflectivity and overall it looks very basic and bland.  To use a new Skybox, what we must do is import an HDRi image into our project.  You can find some free ones off of the Unity store, or you can google HDRi images and import them into your project.  From there you can simply drag and drop the HDRi image into your scene view or open up the lighting settings to also manually adjust settings.
