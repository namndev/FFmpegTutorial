# Learn FFmpeg libav the Hard Way

>Don't you wonder sometimes 'bout sound and vision? David Robert Jones

Since the [FFmpeg](#ffmpeg---command-line) is so useful as a command line tool to do essential tasks over the media files, how can we use it in our programs?

FFmpeg is [composed by several libraries](https://www.ffmpeg.org/doxygen/trunk/index.html) that can be integrated into our own programs. Usually, when you install FFmpeg, it installs automatically all these libraries. I'll be referring to the set of these libraries as FFmpeg libav.

>This title is a homage to Zed Shaw's series [Learn X the Hard Way](https://learncodethehardway.org/), particularly his book Learn C the Hard Way.

## Chapter 0 - The infamous hello world

This hello world actually won't show the message "hello world" in the terminal 👅 Instead we're going to print out information about the video, things like its format (container), duration, resolution, audio channels and, in the end, we'll decode some frames and save them as image files.

FFmpeg libav architecture

But before we start to code, let's learn how FFmpeg libav architecture works and how its components communicate with others.

Here's a diagram of the process of decoding a video:

<p align="center">
    <img src=".gitbook/assets/decoding.png" />
</p>