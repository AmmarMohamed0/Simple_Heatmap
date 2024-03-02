# Simple_Heatmap
## Importing Required Libraries:

The code starts by importing necessary libraries:
- `YOLO` from `ultralytics` for object detection and tracking.
- `heatmap` from `ultralytics.solutions` for generating heatmaps.
- `cv2` for computer vision tasks using OpenCV.

## Initializing YOLO Model and Video Capture:

- The YOLO model is initialized with the specified weights file (`yolov8n.pt`).
- A video capture object (`cap`) is created to read frames from the input video file (`sample.mp4`).

## Assertion Check for Video File:

- An assertion check ensures that the video file is opened successfully. If the file cannot be opened, an error message is displayed.

## Retrieving Video Frame Properties:

- The width, height, and frames per second (FPS) of the video are retrieved using `cap.get()` method with respective property indices (`cv2.CAP_PROP_FRAME_WIDTH`, `cv2.CAP_PROP_FRAME_HEIGHT`, `cv2.CAP_PROP_FPS`).

## Initializing Video Writer:

- A video writer object (`video_writer`) is initialized to write the processed video frames to an output file (`heatmap_output.mp4`).
- The codec is set to `'mp4v'`, and the frame dimensions and FPS are specified.

## Initializing Heatmap Object:

- An instance of the `heatmap.Heatmap` class is created.
- Parameters such as colormap, image width (`imw`), image height (`imh`), and whether to display images (`view_img`) are set.

## Processing Video Frames:

- A `while` loop iterates over each frame of the input video.
- The `cap.read()` method reads the next frame (`im0`) from the video capture object.
- Object tracking is performed on the current frame using the YOLO model (`model.track()`), and the resulting tracks are obtained.
- The `generate_heatmap()` method overlays a heatmap on the frame based on the detected tracks.
- The processed frame (`im0`) is written to the output video file using the `video_writer.write()` method.

## Exiting the Loop:

- The loop exits when all frames have been processed, or when the 'Esc' key (ASCII code 27) is pressed.

## Releasing Resources:

- Once video processing is complete, resources are released:
  - The video capture object (`cap`) is released.
  - The video writer object (`video_writer`) is released.
  - OpenCV windows are destroyed using `cv2.destroyAllWindows()`.

This code performs object tracking using YOLO, overlays a heatmap on the video frames, and writes the processed frames to an output video file. 
