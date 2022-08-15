---
layout: post
title:  "GPU Accelerated Video Encoding with ffmpeg using CUDA on AWS"
date:   2022-08-15 21:01:00 +0100
categories: ffmpeg h264 cuda nvidia aws
---
Video encoding with [ffmpeg][nvidia] on an Nvidia GPU using can be extremely fast compared to software based encoding on the CPU.

Example command:
`ffmpeg -y -vsync 0 -hwaccel cuda -hwaccel_output_format cuda -extra_hw_frames 4 -i input.mp4 -c:a copy -c:v h264_nvenc -b:v 5M output3.mp4`

This results in a transcoding speed of *14.7x*!

On AWS instance type g4dn.xlarge ffmpeg [fails][error-report] unless the option **-extra_hw_frames 4** is added.

[error-report]: https://trac.ffmpeg.org/ticket/7562
[nvidia]: https://docs.nvidia.com/video-technologies/video-codec-sdk/ffmpeg-with-nvidia-gpu/
