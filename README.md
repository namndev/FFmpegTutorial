---
description: >-
  FFmpeg tutorial - learn how media works from basic to transmuxing, transcoding
  and more
---

# Introduction

I was looking for a tutorial/book that would teach me how to start to use [FFmpeg](https://www.ffmpeg.org/) as a library \(a.k.a. libav\) and then I found the ["How to write a video player in less than 1k lines"](http://dranger.com/ffmpeg/) tutorial. Unfortunately it was deprecated, so I decided to write this one.

Most of the code in here will be in c **but don't worry**: you can easily understand and apply it to your preferred language. FFmpeg libav has lots of bindings for many languages like [python](https://mikeboers.github.io/PyAV/), [go](https://github.com/imkira/go-libav) and even if your language doesn't have it, you can still support it through the `ffi` \(here's an example with [Lua](https://github.com/daurnimator/ffmpeg-lua-ffi/blob/master/init.lua)\).

We'll start with a quick lesson about what is video, audio, codec and container and then we'll go to a crash course on how to use `FFmpeg` command line and finally we'll write code, feel free to skip directly to[ ](http://newmediarockstars.com/wp-content/uploads/2015/11/nintendo-direct-iwata.jpg)the section [Learn FFmpeg libav the Hard Way.](./#learn-ffmpeg-libav-the-hard-way)

Some people used to say that the Internet video streaming is the future of the traditional TV, in any case, the FFmpeg is something that is worth studying.

#### Video - what you see!

If you have a sequence series of images and change them at a given frequency \(let's say [24 images per second](https://www.filmindependent.org/blog/hacking-film-24-frames-per-second/)\), you will create an [illusion of movement](https://en.wikipedia.org/wiki/Persistence_of_vision). In summary this is the very basic idea behind a video: **a series of pictures / frames running at a given rate**.

![](https://upload.wikimedia.org/wikipedia/commons/1/1f/Linnet_kineograph_1886.jpg)

Zeitgenössische Illustration \(1886\)

#### Audio - what you listen!

Although a muted video can express a variety of feelings, adding sound to it brings more pleasure to the experience.

Sound is the vibration that propagates as a wave of pressure, through the air or any other transmission medium, such as a gas, liquid or solid.

> In a digital audio system, a microphone converts sound to an analog electrical signal, then an analog-to-digital converter \(ADC\) — typically using [pulse-code modulation \(PCM\)](https://en.wikipedia.org/wiki/Pulse-code_modulation) - converts the analog signal into a digital signal.

![audio analog to digital](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c7/CPT-Sound-ADC-DAC.svg/640px-CPT-Sound-ADC-DAC.svg.png)

> [Source](https://commons.wikimedia.org/wiki/File:CPT-Sound-ADC-DAC.svg)

#### Codec - shrinking data

> CODEC is an electronic circuit or software that **compresses or decompresses digital audio/video.** It converts raw \(uncompressed\) digital audio/video to a compressed format or vice versa. [https://en.wikipedia.org/wiki/Video\_codec](https://en.wikipedia.org/wiki/Video_codec)

But if we chose to pack millions of images in a single file and called it a movie, we might end up with a huge file. Let's do the math:

Suppose we are creating a video with a resolution of `1080 x 1920` \(height x width\) and that we'll spend `3 bytes` per pixel \(the minimal point at a screen\) to encode the color \(or [24 bit color](https://en.wikipedia.org/wiki/Color_depth#True_color_.2824-bit.29), what gives us 16,777,216 different colors\) and this video runs at `24 frames per second` and it is `30 minutes` long.

```c
toppf = 1080 * 1920 //total_of_pixels_per_frame
cpp = 3 //cost_per_pixel
tis = 30 * 60 //time_in_seconds
fps = 24 //frames_per_second

required_storage = tis * fps * toppf * cpp
```

This video would require approximately `250.28GB` of storage or `1.11Gbps` of bandwidth! That's why we need to use a [CODEC](https://github.com/leandromoreira/digital_video_introduction#how-does-a-video-codec-work).

#### container - a comfy place for audio and video

> A container or wrapper format is a metafile format whose specification describes how different elements of data and metadata coexist in a computer file. [https://en.wikipedia.org/wiki/Digital\_container\_format](https://en.wikipedia.org/wiki/Digital_container_format)

A **single file that contains all the streams** \(mostly the audio and video\) and it also provides **synchronization and general metadata**, such as title, resolution and etc.

Usually we can infer the format of a file by looking at its extension: for instance a `video.webm` is probably a video using the container [`webm`](https://www.webmproject.org/).

![container](.gitbook/assets/container.png)