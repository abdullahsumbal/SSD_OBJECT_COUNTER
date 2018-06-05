![travis ci:](https://travis-ci.org/Smorodov/Multitarget-tracker.svg?branch=master)

# Multitarget-tracker

Hungarian algorithm + Kalman filter multitarget tracker implementation.

#### Demo Videos

* MobileNet SSD and tracking for low resolution and low quality videos from car DVR:

[![Tracking:](https://img.youtube.com/vi/Qssz6tVGoOc/0.jpg)](https://youtu.be/Qssz6tVGoOc)

* Mouse tracking:

[![Tracking:](https://img.youtube.com/vi/2fW5TmAtAXM/0.jpg)](https://www.youtube.com/watch?v=2fW5TmAtAXM)

* Motion Detection and tracking:

[![Motion Detection and tracking:](https://img.youtube.com/vi/GjN8jOy4kVw/0.jpg)](https://www.youtube.com/watch?v=GjN8jOy4kVw)

* Multiple Faces tracking:

[![Multiple Faces tracking:](https://img.youtube.com/vi/j67CFwFtciU/0.jpg)](https://www.youtube.com/watch?v=j67CFwFtciU)

#### Parameters
1. Background substraction: built-in Vibe, SuBSENSE and LOBSTER; MOG2 from opencv; MOG, GMG and CNT from opencv_contrib
2. Foreground segmentation: contours
3. Matching: Hungrian algorithm or algorithm based on weighted bipartite graphs
4. Tracking: Linear or Unscented Kalman filter for objects center or for object coordinates and size
5. Use or not local tracker (LK optical flow) for smooth trajectories
6. KCF, MIL, MedianFlow, GOTURN or MOSSE tracking for lost objects and collision resolving
7. Haar face detector from OpenCV
8. HOG and C4 pedestrian detectors
9. SSD detector from OpenCV and models from chuanqi305/MobileNet-SSD
10. YOLO and Tiny YOLO detectors from https://pjreddie.com/darknet/yolo/

### Prerequisites

1. Install OpenCV by following the steps [here](https://github.com/abdullahsumbal/Installtion/blob/master/OpenCV_installation_steps.md).

2. Linking libraries. Please add your <username> if you are copy pasting
``` 
export  LD_LIBRARY_PATH=/home/<username>/anaconda3/lib:$LD_LIBRARY_PATH
```
#### Build
1. Configure project CmakeLists.txt, set OpenCV_DIR. If opencv_contrib don't installed then set disable options USE_OCV_BGFG, USE_OCV_KCF and USE_OCV_UKF
2. Create a build directory and go in to the build directory
```
mkdir build 
cd build
```
3. Compile and run project.
``` 
cmake ..
make all
```


**Usage:**

           Usage:
             ./MultitargetTracker <path to movie file> [--example]=<number of example 0..3> [--start_frame]=<start a video from this position> [--end_frame]=<play a video to this position> [--end_delay]=<delay in milliseconds after video ending> [--out]=<name of result video file> [--show_logs]=<show logs> [--gpu]=<use OpenCL>
             ./MultitargetTracker ../data/atrium.avi -e=1 -o=../data/atrium_motion.avi
           Press:
           * 'm' key for change mode: play|pause. When video is paused you can press any key for get next frame.
           * Press Esc to exit from video

           Params: 
           1. Movie file, for example ../data/atrium.avi
           2. [Optional] Number of example: 0 - MouseTracking, 1 - MotionDetector, 2 - FaceDetector, 3 - PedestrianDetector, 4 - Hybrid face and motion detectors, 5 - MobileNet SSD detector, 6 - YOLO detector
              -e=0 or --example=1
           3. [Optional] Frame number to start a video from this position
              -sf=0 or --start_frame==1500
           4. [Optional] Play a video to this position (if 0 then played to the end of file)
              -ef=0 or --end_frame==200
           5. [Optional] Delay in milliseconds after video ending
              -ed=0 or --end_delay=1000
           6. [Optional] Name of result video file
              -o=out.avi or --out=result.mp4
           7. [Optional] Show Trackers logs in terminal
              -sl=1 or --show_logs=0
           8. [Optional] Use built-in OpenCL
              -g=1 or --gpu=0


#### Thirdparty libraries
* OpenCV (and contrib): https://github.com/opencv/opencv and https://github.com/opencv/opencv_contrib
* Vibe: https://github.com/BelBES/VIBE
* SuBSENSE and LOBSTER: https://github.com/ethereon/subsense
* GTL: https://github.com/rdmpage/graph-template-library
* MWBM: https://github.com/rdmpage/maximum-weighted-bipartite-matching
* Pedestrians detector: https://github.com/sturkmen72/C4-Real-time-pedestrian-detection
* Non Maximum Suppression: https://github.com/Nuzhny007/Non-Maximum-Suppression
* MobileNet SSD: https://github.com/chuanqi305/MobileNet-SSD
* YOLO: https://pjreddie.com/darknet/yolo/
* GOTURN models: https://github.com/opencv/opencv_extra/tree/c4219d5eb3105ed8e634278fad312a1a8d2c182d/testdata/tracking

#### License
GNU GPLv3: http://www.gnu.org/licenses/gpl-3.0.txt 
