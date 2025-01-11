
# iPod Classic 7th Gen Video Formatting


This guid explains how to convert a video to be compatible with the iPod 7th generation using `ffmpeg`.

## Prerequisites

- Install **FFmpeg** if you haven't already.  
  **macOS:**  
  ```bash
  brew install ffmpeg
  ```  
  **Linux (Ubuntu/Debian):**  
  ```bash
  sudo apt-get install ffmpeg
  ```  
  **Windows:**  
  Download from [ffmpeg.org](https://ffmpeg.org/download.html) and follow the installation instructions.

---

## Command Overview

```bash
ffmpeg -i "<INPUT_FILE_PATH>" \
-vf scale=640:480 \
-profile:v baseline \
-level 3.0 \
-b:v 1500k \
-bufsize 3000k \
-c:a aac \
-b:a 96k \
-ar 22050 \
-ac 1 \
"<OUTPUT_FILE_PATH>"
```

---

## Parameters Explained

- `-i "<INPUT_FILE_PATH>"`: Path to the input video file. Replace with the path to your video.
- `-vf scale=640:480`: Resizes the video to **640x480** resolution.
- `-profile:v baseline`: Sets the video profile to **Baseline**, ensuring broader device compatibility.
- `-level 3.0`: Sets the H.264 level to **3.0** for better device support.
- `-b:v 1500k`: Sets the video bitrate to **1500 kbps** for controlled file size and quality.
- `-bufsize 3000k`: Sets the video buffer size to **3000 kbps**.
- `-c:a aac`: Encodes the audio stream using the **AAC** codec.
- `-b:a 96k`: Sets the audio bitrate to **96 kbps**.
- `-ar 22050`: Sets the audio sample rate to **22,050 Hz**.
- `-ac 1`: Converts audio to **mono** (single audio channel).
- `"<OUTPUT_FILE_PATH>"`: Path where the converted file will be saved.

---

## Example Usage

Convert a video located at `/path/to/your/input_video.mp4` and save the output as `/path/to/your/output_video.mp4`:

```bash
ffmpeg -i "/path/to/your/input_video.mp4" \
-vf scale=640:480 \
-profile:v baseline \
-level 3.0 \
-b:v 1500k \
-bufsize 3000k \
-c:a aac \
-b:a 96k \
-ar 22050 \
-ac 1 \
"/path/to/your/output_video.mp4"
```

---

## Apple Music (Mac)

Drag video into `Songs`, then it should show up under `Music Videos`. Once you see it there you can drag the video onto the iPod. Then just make sure you sync and it should show up under music videos.

## Notes

- **Resolution:** Adjust `scale=WIDTH:HEIGHT` if you need a different video size.  
- **Bitrate:** Modify `-b:v` for better or worse video quality (higher values improve quality but increase file size).  
- **Audio Quality:** Tweak `-b:a` and `-ar` for higher or lower audio quality.  

For more options, refer to the [FFmpeg Documentation](https://ffmpeg.org/documentation.html).
