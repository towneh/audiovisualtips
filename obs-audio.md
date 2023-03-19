## CoreAudio AAC Encoder

The Apple CoreAudio encoder is one of best and recommended AAC encoders [available](https://wiki.hydrogenaud.io/index.php?title=AAC_encoders), it has built-in support with OBS, which will automatically make use of it should it be detected on the system.

If you are using an Apple macbook to stream with OBS, you will already be using the CoreAudio encoder by default.

To get access to this, you simply need to run the AppleApplicationSupport64.msi installer which can be extracted from the itunes installer with 7zip, providing the version of the installer is [earlier than 12.10.8.5](https://ideas.obsproject.com/posts/1890/windows-portable-call-to-coreaudiotoolbox-dll)

Note: This document falls outside of the scope of providing these msi files directly.

Once AppleApplicationSupport64.msi is installed, start up or restart OBS Studio, and it should now be using this new encoder.

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
