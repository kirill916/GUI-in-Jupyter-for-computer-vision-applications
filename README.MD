# Background Information:

Coding Project for Professor Mario Silic' course 8,789,1.00 Programming with Advanced Computer Languages
by Kirill Kazakov

# Description

A simple Jupyter Notebook GUI tool that is capable of performing several Computer vision tasks and image transformations.

# System requirements
- Windows 10+ (may run on other operating systems, but I have not tested it)
- At least 1 Gb of free RAM


# Installation and dependencies
Requires Python 3.9.7 and pip. To install python packages dependencies:

```
pip install -r requirements.txt
```
The script may or may not work on other versions of the abovementioned software

# Usage instructions
Open main.ipynb with default jupyter notebook web interface (could be done by for example running `jupyter notebook` in the command line. Tool may not work with notebook plugins for IDEs.) Run the only cell in the main.ipynb for the interface to appear. The interface contains following buttons:
- **Select an image** Opens a file selection dialogue to load an image that would be processed
- **Discard changes** Discard all changes made to an image
- **Object detection** Attempts to detect objects in image  with a pre-trained machine learning model and draw a bounding box around them. Numbers signify confidence level. Pre-trained model weights from [Faster R-CNN model with a MobileNetV3-Large FPN backbone](https://pytorch.org/vision/stable/models/generated/torchvision.models.detection.fasterrcnn_mobilenet_v3_large_fpn.html#torchvision.models.detection.FasterRCNN_MobileNet_V3_Large_FPN_Weights)
- **Image classification** Attempts to comprehend image as a whole. Numbers signify confidence level. Pre-trained model weights from [large MobileNetV3 architecture](https://pytorch.org/vision/stable/models/generated/torchvision.models.mobilenet_v3_large.html#torchvision.models.MobileNet_V3_Large_Weights)
- **Segmentation** Attempts to detect objects in an image and draw a mask around them. Pre-trained model weights from [DeepLabV3 model with a MobileNetV3-Large backbone.](https://pytorch.org/vision/stable/models/generated/torchvision.models.segmentation.deeplabv3_mobilenet_v3_large.html)
- **Brightness, Color, Contrast sliders** Regaltes Brightness, Color, Contrast of an image respectively. Changes are relative to the current level.




# Development report

## Overview

The goal of this project is to create a tool capable of performing various machine learning computer vision tasks. Right from the start of the development I have decided that I would like to abide by following principles:
1. Whole tool should be usable with GUI. No command line interface
2. I use as little packages as possible
3. I try not to use packages that provide full pipeline for various tasks in this project

I can conclude that I managed to stick to the first principle, as the tool's complete functionality is accessed with GUI. I tried to stick to the second and third principles as much as I could. Theoretically,one could rewrite functionality provided by numpy, Pillow and torchvision with pure torch. Yet, this would be too time-consuming and would require writing plenty of code. In the end I think that I managed to find a nice balance between using pre-made functions and writing code myself.

## Structure of the code
Code contains following sections:
1. **Import of required modules and class dictionaries**
2. **Initilization of widgets**  In this section I create buttons and sliders that are going to be used as a GUI elements.
3. **Helper functions** In order to not repeat code blocks that I use multiple times in GUI interaction functions, I decided to create functions with frequently used code. 
4. **GUI interaction functions** This is essentially the main backend part of the code. Here I define functions that are going to be called when the user interacts with various GUI elements. As a rule of thumb, most of the functions first retrieve the currently loaded image from the viewer and turn it into torch tensor, then does various manipulations on it, and finally pushed the image back to viewer. 
5. **Intiation of GUI** After I have written the GUI interaction  functions, the last step is to connect buttons and sliders I have created in the second step, to the GUI interaction  functions. This is done either with `.on_click` method that runs a certain function when the button is clicked or `.observe` method which observes changes of the sliders/uploaders and run function based on change in value.

## Challenges

I have faced multiple challenges while developing this software. First, I had to learn ipywidgets package, which provides the GUI functionality in jupyter notebooks, from the scratch. This was not easy, as I have never worked with GUI development before. The result might not be professionally looking, but still I have realized all the functionality that I wanted.

Second challenge was the selection of pre-trained computer vision models. I realized that the hardware requirements have to be minimal for this project - all models should comfortably run from a CPU and take small amounts of RAM. Due to this, I opted to mobile models, as they provided good performance while keeping the system load to minimum.

Last but not the least, creating visualization functions has been quite difficult. Of course, I could have used one of the functions provided by various packages, but I wanted to resort from overusing pre-made functions. Still, some of the visualization code has been taken from other sources, for example decoding of segmentation maps or addition of padding for object detection.