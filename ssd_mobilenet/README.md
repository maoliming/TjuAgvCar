# Realtime-Object-Detection (Jetson TX2)
My Version of [Tensorflows Object Detection API](https://github.com/tensorflow/models/tree/master/research/object_detection).<br />
<br />

## About the Project
The Idea was to create a realtime capable object detection pipeline on various machines. <br />
Plug and play, ready to use without deep previous knowledge.<br /> <br />
The following work has been done based on the original API:
- Capturing frames of a Camera-Input using OpenCV in seperate thread to increase performance
- Calculate Fps, print the current value to console in a given intervall aswell as the overall mean value at the end
- Allows Models to grow GPU memory allocation. *(ssd_mobilenet_v11_coco needs 350 MB)*
- Added Option for detection without visualization to increase performance
- Added optional automated model download from [model-zoo](https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/detection_model_zoo.md) if necessary
- Added a script to be able to create tfEvent-files for Tensorboard Graph visualizationt
- Gathered necessary files to be able to export new frozen Models based on trained Checkpoints
- Exported new frozen Model based on *ssd_mobilenet_v1_coco* with altered *score_threshold* for *batch_non_max_suppression* to increase perfomance
- Added a script to be able to create tfEvent-files for Tensorboard Graph visualization
- **Results: Overall Performance Increase of up to 100%** depending on the running system
<br />

## Getting Started:  
- Optional: change **INPUT PARAMS** which can be passed to **object_detection.detection**
- For example: If you are not interested in visualization: set **visualize** to **False**. <br />
- if you want to import the pre-trained frozen Model *.pb file* to Tensorboard to visualize the Graph, <br />
run **frozenmodel_to_tensorboard.py** and follow the command line instructions <br />
(opt: change **MODEL_NAME**  inside if necessary)
- run **object_detection10.py** or **object_detection.py** Scripts  <br />
- For JetsonTX2 run **object_detectionjetson.py** Script  <br />
- For change parameters such as video_input or fps **config.yml** Script  <br />
- Enjoy!
<br />

## My Setup:
- Ubuntu 16.04
- Python 2.7
- Tensorflow 1.4
- OpenCV 3.3.1
 <br />

## Current Performance on SSD Mobilenet (with|without visualization):
- Dell Laptop with i7 and GeForce GTX 1050: **35fps | 45fps**
- Nvidia Jetson Tx2: **8fps | 12 fps**
 <br />
