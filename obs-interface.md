# OBS Streaming Best Practices for Virtual Events

This document was created following years of trial and error, from running virtual events, and feedback provided from multiple DJs that stream regularly to VR platforms.

## Required Streaming Software

First thing you need is an up to date release version of OBS Studio. For the purpose of production stability I would advise against beta releases where possible.

* [OBS Studio](https://obsproject.com/)
* [Virtual Cable & VoiceMeeter?](https://vb-audio.com/index.htm) *I didn't forget this, not required for streaming since [28.0 release](https://github.com/obsproject/obs-studio/releases/tag/28.0.0#:~:text=Added%20application%20audio%20capture) UNLESS using Multi-channel 5.1*


## OBS Settings

Below are the recommended settings that differ from the default options in OBS following a fresh installation.

### General

* Theme: Dark `We still find this the cleanest theme to use during production`

Enable the following:
* Show confirmation dialogue when starting streams
* Show confirmation dialogue when stopping streams
* Automatically record when streaming `Never forget to record your sets again!`

### Stream

If VRCDN or other third party ingest server, select Custom as the serice name.

Configure the appropriate server location, specifying the protocol (most likely rtmp:// or srt://) followed by the address. 

![image](https://user-images.githubusercontent.com/25694892/226189293-dc628c8b-e8f8-469f-8c5e-9edd3b89b7dc.png)

If Twitch, first use [this link](https://stream.twitch.tv/ingests/) to find your optimal ingest server. Use Stream Key to connect your account. *Don't worry anout integrations, we can use docks later on*

select Twitch as the service name

Tick "Ignore streaming service setting recommendations"

![image](https://user-images.githubusercontent.com/25694892/226189066-33cfb603-5a19-4499-a948-c87882eedc5b.png)

### Output

* Under Output Mode, select Advanced
* Under the Streaming tab, make sure Audio Track 1 is selected and the appropriate Encoder for your PC system is selected.

For low-latency streaming we will prefer hardware encoding. As of this document there are three viable options to pick:

* NVIDIA NVENC (H.264, HEVC)
* QuickSync (H.264)
* AMD HW (H.264)

#### NVIDIA
![image](https://user-images.githubusercontent.com/25694892/226189752-6d45fc6e-3985-4c24-956b-b52eb95af7af.png)

#### INTEL
Include screenshot of QuickSync settings

#### AMD
Include screenshot of AMD settings

### Audio
* 48 KHz sample rate
* Channels Stereo or 5.1 if using multi-channel 
* Dedicate a Mic/Auxiliary device to your USB Audio Interface (as below)

![image](https://user-images.githubusercontent.com/25694892/226196267-4f8cbf25-374c-4fb3-afe7-820d71bd96e1.png)


### Video
* Base (Canvas) Resolution: 1920x1080
* Output (Scaled) Resolution: 1280x720 or 1920x1080
* Common FPS Value: 30

### Hotkeys
*Nothing specific needded here for best practices*

### Accessbility
*Nothing specific needded here for best practices*

### Advanced
* Colour Space: Rec. 709
* Colour Range: Limited (usually, otherwise Full if you need to match the output from a capture device)
