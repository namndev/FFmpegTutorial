---
description: >-
  FFmpeg tutorial - learn how media works from basic to transmuxing, transcoding
  and more
---

I was looking for a tutorial/book that would teach me how to start to use [FFmpeg](https://www.ffmpeg.org/) as a library \(a.k.a. libav\) and then I found the ["How to write a video player in less than 1k lines"](http://dranger.com/ffmpeg/) tutorial. Unfortunately it was deprecated, so I decided to write this one.

Most of the code in here will be in c **but don't worry**: you can easily understand and apply it to your preferred language. FFmpeg libav has lots of bindings for many languages like [python](https://mikeboers.github.io/PyAV/), [go](https://github.com/imkira/go-libav) and even if your language doesn't have it, you can still support it through the `ffi` \(here's an example with [Lua](https://github.com/daurnimator/ffmpeg-lua-ffi/blob/master/init.lua)\).

We'll start with a quick lesson about what is video, audio, codec and container and then we'll go to a crash course on how to use `FFmpeg` command line and finally we'll write code, feel free to skip directly to[ ](http://newmediarockstars.com/wp-content/uploads/2015/11/nintendo-direct-iwata.jpg)the section [Learn FFmpeg libav the Hard Way.](./#learn-ffmpeg-libav-the-hard-way)

Some people used to say that the Internet video streaming is the future of the traditional TV, in any case, the FFmpeg is something that is worth studying.
