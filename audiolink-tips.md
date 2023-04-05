## AudioLink Tips
### USharp Video Player Single Sound Source
By Default Merlin's [USharp Video Player](https://github.com/MerlinVR/USharpVideo) prefab comes with 3 audio sources configured:-
- StreamAudioSourceL
- StreamAudioSourceR
- VideoAudioSource

As AudioLink can only reference one audio source, we need to configure USharp video player to only use a single audio source in turn.

To do this, there are two options:

#### Blabzillaweasel's Adapter
First download the latest [version](https://github.com/Blabzillaweasel/AudioLink-USharpVideo-Adapter) of the adapter.

Simply put, you link this to both your AudioLink audio source and the USharp video player source, and it will pass the audio over to AudioLink regardless of the mode.

#### Manual method
For this you need to disable 2 out of the above 3 audio sources listed within the prefab's hierarchy.

I usually pick StreamAudioSourceL and StreamAudioSourceR to disable.

This leaves just VideoAudioSource GameObject enabled. Link this to the audio source field that's in the AudioLink prefab within your scene.

Now make sure to add a [VRC AVPro Speaker component](https://docs.vrchat.com/docs/video-players#choosing-avpro-or-unity-video-player:~:text=AVPro%20speaker%20component) to this GameObject.

