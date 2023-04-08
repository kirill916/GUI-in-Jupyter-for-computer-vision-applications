
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
