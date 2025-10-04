# ffmpeg-commands

```
ffmpeg -i input.mkv -c:v libx265 -c:a copy output.mkv
```

`ffmpeg`: Invokes the FFmpeg program.

`-i input.mkv`: Specifies the input file, in this case, an MKV file named `input.mkv`. Replace `input.mkv` with the actual name of your file.

`-c:v libx265`: This is the core part of the command that instructs FFmpeg to use the `libx265` encoder for the video stream, which encodes the video in H.265 (HEVC).

`-c:a copy`: This option copies the audio stream from the input file to the output file without re-encoding it. This saves time and maintains the original audio quality. If you want to re-encode the audio, you would specify a different audio codec (e.g., `-c:a aac`).

`output.mkv`: Specifies the name of the output file. You can choose a different name and extension if desired (e.g., `output.mp4`). While H.265 can be in MP4 containers, MKV is also a suitable container for H.265.


### Optional parameters for quality and speed control:

You can further customize the H.265 encoding process using x265-params or by setting presets:

- __Constant Rate Factor (CRF)__: This is a common way to control quality. A lower CRF value results in higher quality and larger file size.
```
ffmpeg -i input.mkv -c:v libx265 -x265-params crf=28 -c:a copy output.mkv
```
(Replace `28` with your desired CRF value; typical values range from 18 (high quality) to 30 (lower quality, smaller size)).

- __Preset__: Presets offer a balance between encoding speed and compression efficiency. Faster presets generally result in larger files or lower quality for a given bitrate, while slower presets achieve better compression but take longer.
```
ffmpeg -i input.mkv -c:v libx265 -preset medium -c:a copy output.mkv
```
(Common presets include ultrafast, superfast, fast, medium, slow, slower, veryslow).


### Important Notes:
- Ensure your FFmpeg build includes `libx265` support. Most static builds include it by default.
- Encoding to H.265 can be computationally intensive and may take a significant amount of time, especially for high-resolution videos and slower presets.
