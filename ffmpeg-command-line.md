# FFmpeg - command line

> A complete, cross-platform solution to record, convert and stream audio and video.

To work with multimedia we can use the AMAZING tool/library called [FFmpeg](https://www.ffmpeg.org/). Chances are you already know/use it directly or indirectly \(do you use [Chrome?](https://www.chromium.org/developers/design-documents/video)\).

It has a command line program called `ffmpeg`, a very simple yet powerful binary. For instance, you can convert from `mp4` to the container `avi` just by typing the follow command:

```bash
$ ffmpeg -i input.mp4 output.avi
```

We just made a **remuxing** here, which is converting from one container to another one. Technically FFmpeg could also be doing a transcoding but we'll talk about that later.

## FFmpeg command line tool 101

FFmpeg does have a [documentation](https://www.ffmpeg.org/ffmpeg.html) that does a great job of explaining how it works.

To make things short, the FFmpeg command line program expects the following argument format to perform its actions `ffmpeg {1} {2} -i {3} {4} {5}`, where:

1. global options
2. input file options
3. input url
4. output file options
5. output url

The parts 2, 3, 4 and 5 can be as many as you need. It's easier to understand this argument format in action:

```bash
# WARNING: this file is around 300MB
$ wget -O bunny_1080p_60fps.mp4 http://distribution.bbb3d.renderfarming.net/video/mp4/bbb_sunflower_1080p_60fps_normal.mp4

$ ffmpeg \
-y \ # global options
-c:a libfdk_aac -c:v libx264 \ # input options
-i bunny_1080p_60fps.mp4 \ # input url
-c:v libvpx-vp9 -c:a libvorbis \ # output options
bunny_1080p_60fps_vp9.webm # output url
```

This command takes an input file `mp4` containing two streams \(an audio encoded with `aac` CODEC and a video encoded using `h264` CODEC\) and convert it to `webm`, changing its audio and video CODECs too.

We could simplify the command above but then be aware that FFmpeg will adopt or guess the default values for you. For instance when you just type `ffmpeg -i input.avi output.mp4` what audio/video CODEC does it use to produce the `output.mp4`?

Werner Robitza wrote a must read/execute [tutorial about encoding and editing with FFmpeg](http://slhck.info/ffmpeg-encoding-course/#/).

