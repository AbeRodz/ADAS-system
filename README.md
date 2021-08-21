# ADAS-system
***Bachelor's dissertation thesis***

**This project is about an ADAS system with lane and object detection.**

Why make this project?

Since quite a while i've been interested in autonomous vehicles, on september 2020 i began a coursera specialization in automous vehicles, i got insights on the math behind, carla simulator, and other stuff. What really fascinated me was Computer Vision in vehicles, so that's why i decided to explore this field while doing my thesis.

The project is divided is two sections:
  
  1. Lane detection:
  
      - Data collection ✔️
      - Video rescaling ✔️
      - Frame extraction ✔️
      - Image processing ✔️
      - Sliding window technique ✔️

(under testing and revision) ⏲️
      
  2. Object Detection:
      - **In Progress** 🚧


## Lane detection
### Data Collection and Video Rescaling
For Data collection, a video of a highway was taken using a smartphone, though the native video resolution is **1080p at 16:9**, in order to reduce 
computation requirements, it was necessary to downgrade the video resolution, **480p at 16:9** aspect ratio was selected, for rescaling use the *rescalingimages.py* file.

### Frame Extraction
Having a video with the adequate resolution, it is now necessary to extract frames and build a dataset of images, for that *datagenerator.py* uses opencv to extract each frame from a video source.



#### Lane detection Pipeline

- Convert RGB to GRAY
  - Apply a Sobel operator, and compute its magnitude and gradient
  - Obtain a binary image for both magnitude and gradient
- Convert RGB to HLS
  - Obtain a binary image of a thresholded HLS image
- Merge all binary images using bitwise operators
- Apply warping or perspective transform
- Create a histogram from the warped binary image
- Apply sliding window search for high frequency data obtain from the histogram

## Requirements
- Python 3.7
- Carla Simulator 0.9.4
- pygame
- pytorch or Tensorflow?
- Matplotlib
- Numpy
- Opencv 

