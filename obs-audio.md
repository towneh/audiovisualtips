## CoreAudio AAC Encoder

The Apple CoreAudio encoder is one of best and recommended AAC encoders [available](https://wiki.hydrogenaud.io/index.php?title=AAC_encoders), it has built-in support with OBS, which will automatically make use of it should it be detected on your system.

   *Note: If you are using Apple hardware to stream with OBS, you will already be using the CoreAudio encoder by default.*

To get access to this, you simply need to run the AppleApplicationSupport64.msi installer which can be extracted from the iTunes installer with 7zip, providing the version of the installer is [earlier than 12.10.8.5](https://ideas.obsproject.com/posts/1890/windows-portable-call-to-coreaudiotoolbox-dll). You will also need to ensure you are using the 64bit version of OBS as well, which are all versions since 28.0, otherwise you will need to use AppleApplicationSupport.msi for compatibility with x86 releases of 27.2.4 and older.

   *Note: You can also grab a copy of this file from this repo https://github.com/towneh/audiovisualtips/tree/main/CoreAudio please check the SHA256 hash to be safe!

Once the Apple Application Support pack is installed, start up or restart OBS Studio, and it should now be using this new encoder.

To check that is has loaded correctly, navigate to Help, then select Current Logs:

*During OBS startup*
```
16:50:45.378: [CoreAudio encoder]: Adding CoreAudio AAC encoder
```

*During stream start*
```
17:01:03.990: [CoreAudio AAC: 'Track1']: settings:
17:01:03.990:     mode:          AAC
17:01:03.990:     bitrate:       320
17:01:03.990:     sample rate:   48000
17:01:03.990:     cbr:           on
17:01:03.990:     output buffer: 1536
```

## Multi-channel Audio

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
