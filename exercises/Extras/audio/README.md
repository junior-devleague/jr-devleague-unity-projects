# "Dem can't take my audio, audio, audio, audio from me" - J Boog

Any game you've ever played or seen has *some* type of audio in it.  A game would simply be considered incomplete without music just because of how music can add so much to making a game immersive for the player.  It isn't uncommon these days for games to come with complete Original Sound Tracks (OST's for short) that gamers can reminisce on.  Personally, games with incredible audio tracks are usually the most memorable.  My personal favorite soundtrack is from Final Fantasy X and I still listen back on it to this very day.  

## What's behind the audio engine?

Basically, audio in Unity can work just like how real life does.  Sounds are emitted off and are heard by listeners through our ears.  Sounds are able to be nearly perfectly simulated by adding audio effects to sounds through Unity's *audio mixer*.  Essentially, if you wanted to recreate voices in a cave, naturally, you would alot of echo or reverb since sounds would reflect off of the walls.  If you are in an open space, you don't necessarily *need* that as sound wouldn't reflect in open space.  However, you have the option to add your own custom sounds by recording, mixing, and mastering in Unity just like any other Digital Audio Workstation (DAW).  Another thing is that Unity accepts all types of audio formats including (but aren't limited to) .mp3, .ogg, .wav, .aiff, or .mod.  

## So how does it work?

Unity includes mainly two types of audio, these two sources are 2D and 3D. 2D spatial most commonly represents background/theme music while 3D audio generally tries to represent audio sources from a specific location.  2D spatial can be referred to as background/theme music.  While 3D audio generally encompasses where the relative speed of the source and listener objects help to add realism.  Generally, this would mean that with headphones/quality speakers you are capable of hearing sound sources from specific directions and the volume of the sound can give you a general idea of where you are in relation to it.  For example, a car in the distance would use a 3D audio source so you can detect where the car is coming from or even what direction it's heading in.

## How would I set up 2D or 3D Audio in my project?

Simple! In a default project, the **Main Camera** GameObject includes an innate component called **audio Listener**.  The audio listener essentially acts as a pair of ears, it listens for different audio sources that you've included in your scene and plays them back for you in the spatial area that the object emitting the sound source is placed.  

Playing a 2D sound is simple enough: After downloading/importing an AudioClip, drag the audio file into the hierarchy window and you should automatically begin hearing your audio file when you hit play.  

Playing a 3D sound is a little more complicated.  Unlike a 2d sound, 3D sounds require a GameObject and the audio file needs to be attached to that GameObject.

1. First start by importing all sound files into your Project.  Create a folder to store your audio files.

2. Create a new GameObject to attach your audio file to.

3. Add the **AudioSource** component to the GameObject.  
  - Think of AudioSource as a controller that determines playback and different settings for your specified AudioClip.
  ![ScreenShot](https://docs.unity3d.com/uploads/Main/AudioSourceInspector.png)

4. In the Inspector window looking at the AudioSource component, Attach your specified AudioClip to where it says the **AudioClip** property

5. Now, when we hit play, we can hear the AudioClip if we are within hearing range of it.  Using an audio mixer would fix this, but what if we just want an AudioClip to play on a trigger, perhaps?

6. Set our GameObject to a trigger in the Collider component, whether you want the mesh rendered or not is up to you.

7. Create a new C# script and name it Sound_Trigger

8. Attach this script to the same GameObject you created the AudioSource on.

9.  Inside of visual Studio:
    - create a public AudioSource variable and name it SoundSource, then create a public AudioClip variable and name it SoundClip.
    - create a new OnTriggerEnter function that compares the tag for "Player" and if it passes, simply run SoundSource.Play();
    
    



## The Audio Mixer

