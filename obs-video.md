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

To get around this, at Orion Music Festival events, we provided every DJ and LD/VJ a mask of the UV space to apply at the highest level of the OBS source list, in order to replace these pixels with an unchanging black space. This results is more bits per pixel being made available to the visible part of the screen space.

*Example of UV masked applied*
![image](https://user-images.githubusercontent.com/25694892/226192640-98f8f54c-08e4-4af4-b5e3-fd80c1f4f54e.png)

If the mask is applied from the origin, then this optimisation is maintained all the way through to the video distribution in to the world, therefor preventing pixelation of the video.
