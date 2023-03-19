## Video compression considerations with H.264

To start, you might first want to try a primer on the subject such as [this site](https://sidbala.com/h-264-is-magic/) which explains how H.264 encoding achieves its low bitrate results.

Next we want to ensure that the fidelity of the stream content remains of a decent enough quality and to [keep the VMAF score around good to excellent high](https://medium.com/exmachinagroup/harder-better-faster-cheaper-optimizing-video-bitrate-for-ultra-low-latency-live-content-a2d0be55660a).

We also need to consider that we're operating within a CBR range of 3500-6000 Kbps in most cases, in order to accomodate both the rules of the content provider and the bandwidth that is available to the viewer.

Note: If the stream is destined for a production system used by larger events, rather than direct to the attendees, then you can probably increase this to the maximum available 6000 Kbps.

![image](https://miro.medium.com/v2/0*8WmTeqaDW5tB7jGZ)

In the graph above, "Sport" is defined as:

```The content is “complex.” It has a high amount of temporal motion, fast-moving small objects, and a medium number of scene changes.```

Arguably a lot of visuals produced by either a DJ or dedicated VJ can be complicated, fast transitioning, and glitchy, which further serves to drive the VMAF score down.

**How can we make this better?**

Glad you asked! In a lot of events, there is usually a complex UV mapping used with the virtual world space video screens.

This means that not all of the canvas that is broadcast will be visible and this deemed to be wasted space (and more importantly, wasted bitrate)

*Example of entire canvas space being used*
![image](https://user-images.githubusercontent.com/25694892/226192556-0731e31c-2fd9-4667-825c-563e133dc841.png)

To get around this, at Orion Music Festival events, we provide every DJ and LD/VJ a mask of the UV space to apply at the highest level of the OBS source list, in order to replace these pixels with an unchanging black space. This results is more bits per pixel being made available to the visible part of the screen space.

*Example of UV masked applied*
![image](https://user-images.githubusercontent.com/25694892/226192640-98f8f54c-08e4-4af4-b5e3-fd80c1f4f54e.png)

If the mask is applied from the origin, then this optimisation is maintained all the way through to the video distribution to the world, otherwise the next hop in the production chain can mask it and potentially remove further degradation.

### Multi-channel Audio

* Used when streaming either native multi-channel 5.1, if using [ARC Upmix](https://elevativepro.com/arc/) to spatialize stereo sound for some VR worlds, or if using [VoiceMeeter Up Mix options](https://voicemeeter.com/mix-down-and-mix-up-the-voicemeeter-bus-modes/)
* If using Up Mix features in VoiceMeeter you have the following options:
  * Stereo Repeat mode, which allows you to have two more copies of the stereo channels, which you can then apply low pass and high pass filters against.
  ![image](https://user-images.githubusercontent.com/25694892/226199207-950a9855-8268-4f90-998f-c36fb616a99b.png)
  * Composite mode, which allows you to target multiple sources to individual audio inputs to specific bus channels, useful for isolating instruments in-game or for providing environmental audio in addition to the music.
  ![image](https://user-images.githubusercontent.com/25694892/226199351-625e39ea-3205-4956-b18a-b0041ad5a32b.png)
* If using multi-channel Audio you must also consider how audio sensitive shader systems, such as [AudioLink](https://github.com/llealloo/vrc-udon-audio-link), will respond to an audiosource configured to specific channels, e.g. try targetting the full mix to a specific channel, which is played back in a dedicated audio source for AudioLink.

*AVPro Channel Mappings for reference*
```
FrontLeft => Mono Left
FrontRight => Mono Right
FrontCenter => 3
LowFrequency => 4
BackLeft => 5
BackRight => 6
```
