DIY智能音箱
==========

这是一份为DIY智能音箱或者语音交互设备而收集的资源列表，希望最终我们可以DIY一个可以日常使用的开源智能音箱。

语音交互的简化逻辑大致是这样的:

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

+ Audio Processing 即语音前端处理，包括回声消除 (Acoustic Echo Cancellation, AEC), 波束成形 (Beamforming), 降噪 (Noise Suppression, NS)等，现在主流采用阵列麦克风实现远场语音交互，开始有一些将神经网络跟经典语音处理算法结合的研究。
+ Keyword Spotting (KWS) 即关键词检测，用于检测OK Google、Hey Siri之类的关键词，然后开启一次对话。运行在终端设备，避免语音一直上传到云端
+ Speech To Text (STT) 即语音转文字，现在已经HMM+GMM全面切换到神经网络了
+ Natural Language Understanding (NLU) 即自然语言理解，用神经网络实现已经是主流了
+ Knowledge/Skill/Action 即知识库和扩展
+ Text To Speech 即文本转语音，Google的基于神经网络的WaveNet TTS已经开始应用在Google Assistant上了

在语音、自然语言处理及图像领域，基于神经网络的机器学习非常有效，像Google的AI First和百度的All In AI，他们有能力把AI落地，而不是在建造空中楼阁。

------------------

这个列表以语音交互技术栈的各部分划分。

### KWS + STT + NLU + Skill + TTS

提供比较完整语音交互技术栈是比较难，并且KWS、STT、NLU和TTS等这4个部分，最好的算法都是基于神经网络的，近几年发展得非常迅速。

其中一些活跃的开源项目值得去了解和参与：

+ [Mycroft :star:](https://github.com/MycroftAI/mycroft-core) -  
+ [dingdang robot](https://github.com/wzpan/dingdang-robot) - a :cn: voice interaction robot based on [Jasper](https://github.com/jasperproject/jasper-client) and built with raspberry pi


基于巨头的云服务和SDK，可以快速打造一个语音交互设备。
+ Amazon Alexa Voice Service - 拥有最多的用户、开发者和第三方合作商，

  + [C++ SDK)](https://github.com/alexa/avs-device-sdk)
  + [Java Client](https://github.com/alexa/alexa-avs-sample-app)
  + [Python Client](https://github.com/respeaker/avs)

+ [Google Assistant SDK](https://github.com/googlesamples/assistant-sdk-python)

  Google则有最好的技术，Google Assistant通过 digitalflow.ai 可以快速扩展，其Device Action可以很好联动本地设备

+ [Baidu DuerOS](https://github.com/dueros)


### KWS
+ [Snowboy](https://github.com/Kitt-AI/snowboy) - DNN based hotword and wake word detection toolkit
+ [Honk](https://github.com/castorini/honk) - PyTorch reimplementation of Google's TensorFlow CNNs for keyword spotting
+ [ML-KWS-For-MCU](https://github.com/ARM-software/ML-KWS-for-MCU) - Maybe the most promise for resource constrained devices such as ARM Cortex M7 microcontroller

### STT
+ [Mozilla DeepSpeech](https://github.com/mozilla/DeepSpeech) - A TensorFlow implementation of Baidu's DeepSpeech architecture
+ [Kaldi](https://github.com/kaldi-asr/kaldi)
+ [PocketSphinx](https://github.com/cmusphinx/pocketsphinx) - a lightweight speech recognition engine using HMM + GMM


### NLU
+ [Rasa NLU](https://github.com/RasaHQ/rasa_nlu)

  + [Rasa NLU for Chinese](https://github.com/crownpku/Rasa_NLU_Chi)


### TTS
+ [Mimic](https://github.com/MycroftAI/mimic) - Mycroft's TTS engine, based on CMU's Flite (Festival Lite)
+ [manytts](https://github.com/marytts/marytts) - an open-source, multilingual text-to-speech synthesis system written in pure java
+ [espeak-ng](https://github.com/espeak-ng/espeak-ng) - an open source speech synthesizer that supports 99 languages and accents.
+ [ekho](https://github.com/hgneng/ekho) - Chinese text-to-speech engine
+ WaveNet, Tacotron 2


### Audio Processing

语音前端处理现在集中在麦克风阵列信号处理上，还不算成熟，远场、嘈杂环境、鸡尾酒效应还待解决。神经网络算法也开始被应用到DOA、Beamforming等算法上。

+ Acoustic Echo Cancellation

  + [SpeexDSP](https://github.com/xiph/speexdsp)

+ Direction Of Arrival (DOA) - Most used DOA algorithms is GCC-PHAT

  + [odas](https://github.com/introlab/odas)

+ [Beamforming](https://github.com/search?utf8=%E2%9C%93&q=beamforming&type=)

  + [BeamformIt](https://github.com/xanguera/BeamformIt) - filter&sum beamforming
  + CGMM Beamforming - [a reference implementation](https://github.com/funcwj/CGMM-MVDR)
  + MVDR Beamforming
  + GSC Beamforming

+ Noise Suppresion

  + NS of WebRTC audio processing

### Audio I/O
+ PortAudio
+ [libsoundio](https://github.com/andrewrk/libsoundio)
+ ALSA
+ PulseAudio
