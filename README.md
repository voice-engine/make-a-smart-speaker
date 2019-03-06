To make a smart speaker
=======================

[中文](zh.md)


I believe we have enough resources to make an open source smart speaker. Let's do it. Just created [a project called `smart speaker from scratch` on hackaday](https://hackaday.io/project/164221-smart-speaker-from-scratch). Check it out to see what we can make.

Here is a collection of resources to make a smart speaker. ~~Hope we can make an open source one for daily use.~~

The simplified flowchart of a smart speaker is like:

```
+---+   +----------------+   +---+   +---+   +---+
|Mic|-->|Audio Processing|-->|KWS|-->|STT|-->|NLU|
+---+   +----------------+   +---+   +---+   +-+-+
                                               |
                                               |
+-------+   +---+   +----------------------+   |
|Speaker|<--|TTS|<--|Knowledge/Skill/Action|<--+
+-------+   +---+   +----------------------+
```

+ Audio Processing includes Acoustic Echo Cancellation (AEC), Beamforming, Noise Suppression (NS), etc.
+ Keyword Spotting (KWS) detects a keyword (such as OK Google, Hey Siri) to start a conversation.
+ Speech To Text (STT)
+ Natural Language Understanding (NLU) converts raw text into structured data.
+ Knowledge/Skill/Action - Knowledge base and plugins (Alexa Skill, Google Action) to provide an answer.
+ Text To Speech

------------------


### KWS + STT + NLU + Skill + TTS

#### Active open source projects

+ [Snips :star:](https://snips.ai) - the first 100% on-device and private-by-design open-source Voice AI platform
+ [Mycroft :star:](https://github.com/MycroftAI/mycroft-core) - a hackable open source voice assistant
+ [SEPIA :robot:](https://sepia-framework.github.io/) - Highly customizable, open-source, cross-platform voice assistant and VUI framework (HTML + Java + x)
+ [Kalliope](https://github.com/kalliope-project/kalliope) - a framework that will help you to create your own personal assistant, kind of similar with Mycroft (Both written by Python)
+ [dingdang robot](https://github.com/dingdang-robot/dingdang-robot) - a :cn: voice interaction robot based on [Jasper](https://github.com/jasperproject/jasper-client) and built with raspberry pi


#### SDK
+ Amazon Alexa Voice Service - is the most widely used voice assistant
  + [C++ SDK](https://github.com/alexa/avs-device-sdk)
  + [Java Client](https://github.com/alexa/alexa-avs-sample-app)
  + [Python Client](https://github.com/respeaker/avs)

+ [Google Assistant SDK](https://github.com/googlesamples/assistant-sdk-python)

  It has the smartest brain, its extension called Google Action can be created on a few steps with digitalflow.ai and its Device Action is very suit for home smart devices.

+ [Baidu DuerOS](https://github.com/dueros)

+ [Snips](https://snips.ai)
  + [Install Snips](https://snips.gitbook.io/documentation/installing-snips) on Raspberry Pi 3, Linux, osX, iOS and Android

+ [SEPIA Installation](https://medium.com/sepia-framework/hosting-your-own-private-virtual-assistant-533b86553d63), [SEPIA with Porcupine + ReSpeaker](https://github.com/SEPIA-Framework/sepia-wakeword-tools/tree/master/Porcupine)


### KWS
+ [Mycroft Precise](https://github.com/MycroftAI/mycroft-precise) - A lightweight, simple-to-use, RNN wake word listener
+ [Snowboy](https://github.com/Kitt-AI/snowboy) - DNN based hotword and wake word detection toolkit
+ [Honk](https://github.com/castorini/honk) - PyTorch reimplementation of Google's TensorFlow CNNs for keyword spotting
+ [ML-KWS-For-MCU](https://github.com/ARM-software/ML-KWS-for-MCU) - Maybe the most promise for resource constrained devices such as ARM Cortex M7 microcontroller
+ [Porcupine](https://picovoice.ai/products/#wake-word) - Lightweight, cross-platform engine to build custom wake words in seconds

### STT
+ [Mozilla DeepSpeech](https://github.com/mozilla/DeepSpeech) - A TensorFlow implementation of Baidu's DeepSpeech architecture
+ [Kaldi](https://github.com/kaldi-asr/kaldi)
+ [PocketSphinx](https://github.com/cmusphinx/pocketsphinx) - a lightweight speech recognition engine using HMM + GMM


### NLU
+ [Rasa NLU](https://github.com/RasaHQ/rasa_nlu)

  + [Rasa NLU for Chinese](https://github.com/crownpku/Rasa_NLU_Chi)
  
+ [Snips NLU](https://github.com/snipsco/snips-nlu) - a Python library that allows to parse sentences written in natural language and extracts structured information.

### TTS
+ [Mimic](https://github.com/MycroftAI/mimic) - Mycroft's TTS engine, based on CMU's Flite (Festival Lite)
+ [manytts](https://github.com/marytts/marytts) - an open-source, multilingual text-to-speech synthesis system written in pure java
+ [espeak-ng](https://github.com/espeak-ng/espeak-ng) - an open source speech synthesizer that supports 99 languages and accents.
+ [ekho](https://github.com/hgneng/ekho) - Chinese text-to-speech engine
+ WaveNet, Tacotron 2


### Audio Processing
+ Acoustic Echo Cancellation

  + [SpeexDSP](https://github.com/xiph/speexdsp), its python binding [speexdsp-python](github.com/xiongyihui/speexdsp-python)
  + [EC](https://github.com/voice-engine/ec) - Echo Cancelation Daemon based on SpeexDSP AEC for Raspberry Pi or other devices running Linux.

+ Direction Of Arrival (DOA) - Most used DOA algorithms is GCC-PHAT

  + [tdoa](https://github.com/xiongyihui/tdoa)
  + [odas](https://github.com/introlab/odas) - ODAS stands for Open embeddeD Audition System. This is a library dedicated to perform sound source localization, tracking, separation and post-filtering. ODAS is coded entirely in C, for more portability, and is optimized to run easily on low-cost embedded hardware. ODAS is free and open source.

+ [Beamforming](https://github.com/search?utf8=%E2%9C%93&q=beamforming&type=)

  + [BeamformIt](https://github.com/xanguera/BeamformIt) - filter&sum beamforming
  + CGMM Beamforming - [a reference implementation](https://github.com/funcwj/CGMM-MVDR)
  + MVDR Beamforming
  + GSC Beamforming

+ Voice Activity Detection

  + WebRTC VAD, [py-webrtcvad](https://github.com/wiseman/py-webrtcvad)
  + DNN VAD

+ Noise Suppresion

  + NS of WebRTC audio processing, [python-webrtc-audio-processing](https://github.com/xiongyihui/python-webrtc-audio-processing)



### Audio I/O
+ PortAudio, pyaudio
+ [libsoundio](https://github.com/andrewrk/libsoundio)
+ ALSA
+ PulseAudio
+ [Pipewire](https://github.com/PipeWire/pipewire)
