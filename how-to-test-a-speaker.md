# How to test a speaker

When we get a new phone, a new computer, or a smart speaker, how to find out if its speaker is good or not?
There is a simple way to find out. It only requires your computer (running Linux, Windows or macOS) or your Raspberry Pi with the open source software [Audacity](https://www.audacityteam.org/)

![](https://www.audacityteam.org/wp-content/themes/wp_audacity/img/logo.png)

We often evaluate a speaker based on its frequency response. With `Audacity`, we quickly find out the frequency response of a speaker.

### Use Audacity to evaluate the frequency response of a speaker

1. Open `Audacity`, click menus `Generate` >> `Chirp` and create 5 seconds `logarithmic interpolation` chirp started from 100 Hz to 10,000 Hz.

   ![image](https://user-images.githubusercontent.com/948283/43753001-301b21d8-9a36-11e8-9d4b-946724d7e36c.png)

   We choose logarithmic interpolation instead of linear interpolation, as we more care about lower mid-range of audio.

2. Click `|<<` of the toolbar to the start of the chirp, and then press `r` (or shirt + r on audacity 2.2.0+) to play the chirp and record at the same time.

   ![image](https://user-images.githubusercontent.com/948283/43304765-e673f24e-91a7-11e8-8801-5d973ecb9556.png)

   ![image](https://user-images.githubusercontent.com/948283/43305140-27fdeaf2-91a9-11e8-9335-450c0cac403e.png)

3. I tested the built-in speaker of my computer and an external speaker. The two recordings is look like:

   ![image](https://user-images.githubusercontent.com/948283/43753153-e62cdbb0-9a36-11e8-9ee4-50e6aef30180.png)

   Channel 2 and  channel 3 are the recordings of the built-in speaker of the computer (my computer has two microphones). The last two channels are the recording of the external speaker. Based on the waveforms, the external speaker is much better on low frequency and has more uniform frequency response.

4. We can also switch to frequency domain to get a look of the frequency response. Select a channel and click menus `Analyze` >> `Plot spectrum...`

   ![image](https://user-images.githubusercontent.com/948283/43753119-ced68ef2-9a36-11e8-9c96-ec196f875e63.png)

   ![image](https://user-images.githubusercontent.com/948283/43753056-6fe24fee-9a36-11e8-8122-e7ef416c0fc2.png)

### Does the test reflect the real frequency response of the speaker?
We can use our microphones of our computers to test a speaker, because most of microphones have a very good frequency response. The following image is the frequency response of a microphone found in its datasheet.

![](https://user-images.githubusercontent.com/948283/43306340-612d3ae0-91ad-11e8-8731-f7358273474a.png)

So the microphone has only a little bit effect on the above test. The frequency responses we got is close to the frequency response of the speakers. Of course, the surrounding noise has some effects, so it would be better if we are in a quiet and less-reflection place or in a anechoic chamber. 

![image](https://user-images.githubusercontent.com/948283/43760690-703de1aa-9a55-11e8-8af7-714b4896f22f.png)

### tweak EQ to adjust audio output
When we know the frequency response of a speaker, we can't change it, but we can use software to adjust the audio output. 

1. On Raspberry Pi, we can use `alsaequal` to tweak the EQ. See [Max's Enabling Equalizer on Raspberry Pi using ALSA equal Plugin](https://scribles.net/enabling-equalizer-on-raspberry-pi-using-alsa-equal-plugin/)

2. On Linux with PulseAudio, we can use [PulseEffects](https://github.com/wwmm/pulseeffects)

![](https://github.com/wwmm/pulseeffects/raw/master/images/equalizer2.png)


