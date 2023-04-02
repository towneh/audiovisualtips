## Multi-channel Audio

* Used when streaming either native multi-channel 5.1, if using [ARC Upmix](https://elevativepro.com/arc/) to spatialize stereo sound for some VR worlds, or if using [VoiceMeeter Up Mix options](https://voicemeeter.com/mix-down-and-mix-up-the-voicemeeter-bus-modes/)
* If using Up Mix features in VoiceMeeter you have the following options:
  * Stereo Repeat mode, which allows you to have two more copies of the stereo channels, which you can then apply low pass and high pass filters against.
  
  ![image](https://user-images.githubusercontent.com/25694892/226199207-950a9855-8268-4f90-998f-c36fb616a99b.png)

* Composite mode, which allows you to target multiple sources to individual audio inputs to specific bus channels, useful for isolating instruments in-game or for providing environmental audio in addition to the music.
 
  ![image](https://user-images.githubusercontent.com/25694892/226199351-625e39ea-3205-4956-b18a-b0041ad5a32b.png)

* If using multi-channel Audio you must also consider how audio sensitive shader systems, such as [AudioLink](https://github.com/llealloo/vrc-udon-audio-link), will respond to an audiosource configured to specific channels, e.g. try targetting the full mix to a specific channel, which is played back in a dedicated audio source for AudioLink.

### AVPro Channel Mappings for reference
```
FrontLeft => Mono Left
FrontRight => Mono Right
FrontCenter => 3
LowFrequency => 4
BackLeft => 5
BackRight => 6
```

### Multi-channel Media Sources
https://thedigitaltheater.com/dolby-trailers/

https://kodi.wiki/view/Samples

https://www2.iis.fraunhofer.de/AAC/
