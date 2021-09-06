# ADAS-system
***Bachelor's dissertation thesis***

**This project is about an ADAS system with lane and object detection.**

Why make this project?

Since quite a while I've been interested in autonomous vehicles, on september 2020 I began a coursera specialization in automous vehicles, I got insights on the math behind, carla simulator, and other stuff. What really fascinated me was Computer Vision in vehicles, so that's why I decided to explore this field while doing my thesis. ALso there's currently the search of reducing complex sensorial systems and focus on CV systems.

The project is divided is two sections:
 
  1. Lane detection:
      - Data collection ✔️
      - Video rescaling ✔️
      - Frame extraction ✔️
      - Image processing ✔️
      - Sliding window technique ✔️
      - Testing done on Carla simulator ✔️
      - Testing done on Dataset ✔️
      - Precision calculation 

(under testing and revision) ⏲️
      
  2. Object Detection:
      - **In Progress** 🚧
      - Yolov5 Implementation


## Lane detection
### Data Collection and Video Rescaling
For Data  collection, a video of a highway was taken using a smartphone, though the native video resolution is **1080p at 16:9**, in order to reduce computation requirements, it was necessary to downgrade the video resolution, **480p at 16:9** aspect ratio was selected, for rescaling use the `rescalingimages.py` file.

### Frame Extraction
Having a video with the adequate resolution, it is now necessary to extract frames and build a dataset of images, for that `datagenerator.py` uses opencv to extract each frame from a video source.

### Lane detection Pipeline
#### Preprocessing
  - Convert RGB to GRAY
    - Apply a Sobel operator for border detection, and compute its magnitude and gradient
    - Obtain a binary image for both magnitude and gradient
  - Convert RGB to HLS
    - Obtain a binary image of a thresholded HLS image
  - Merge all binary images using bitwise operators

#### Sliding window technique and bounding area 
  - Apply warping or perspective transform to the binary image
  - Create a histogram from the warped binary image
  - Apply sliding window search for high frequency data obtain from the histogram
  - Apply polinomial fitting
  - Fill the detected area with a bounding box
  - Apply the inverse perspective transform
  - Final image
  - Apply the algorithm to each frame on the dataset, for that use `lanedetector.py`
- Merge processed frames onto a video, use `final2video.py`

### Object Detection
For the custom dataset, each frame was marked with the lanes detected, this frames are passed to yolov5 on a google colab with gpu acceleration.
Note: It hasn't been implemented on Carla Simulator yet.

### Where's the code?
This project is Open Source, but as I'm doing my dissertation thesis, I'll try to publish it on a journal, I was advised to wait before uploading it on this repo if the project is going to be published.

## Requirements
- Python 3.7
- yolov5
- google colab
- Carla Simulator 0.9.4
- pygame
- pytorch 
- Matplotlib
- Numpy
- Opencv 

