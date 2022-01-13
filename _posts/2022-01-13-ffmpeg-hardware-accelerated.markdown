---
layout: post
title:  "Hardware Accelerated Video Encoding on macOS with ffmpeg"
date:   2022-01-13 09:12:56 +0100
categories: ffmpeg macos
---
[ffmpeg][ffmpeg] can use a hardware acceleration framework called [VideoToolbox][videotoolbox] for h264 or hevc on macOS 10.8 and later.

`ffmpeg -i input.mp4 -c:v h264_videotoolbox -preset veryfast -b:v 5M -c:a aac -b:a 128k output.mp4`

Keep in mind this encoder does not support the same flags as the default x264 decoder.

Hardware encoding runs at **~8.5x** speed on my Mac Book Pro 13", Dual-Core Intel Core i7.
Software encoding runs at **~1.7x** speed. so the difference is pretty dramatic.

Resulting file sizes are comparable in my example. People claim software encoding usually gives a better quality.

[ffmpeg]: https://trac.ffmpeg.org/wiki/HWAccelIntro
[videotoolbox]: https://developer.apple.com/documentation/videotoolbox
