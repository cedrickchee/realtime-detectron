# Real-time Detectron

This is a demo project of a real-time Mask R-CNN using [Detectron](https://github.com/facebookresearch/Detectron). We will be using consumer grade webcam for capturing the video stream.

**Project Status:** Early release. Still in heavy development. What this means is, things might be moved around quickly and things will break.

## Introduction

Detectron is Facebook AI Research (FAIR)'s research platform for object detection research, implementing popular algorithms like Mask R-CNN and RetinaNet.

In this project, we have implemented a simple solution to run Detectron Mask R-CNN algorithm with webcam. We are using Mask R-CNN for object detection and instance segmentation.

## Installation

Runtime requirements:
* Python 2.7
    * Note: [Python 3 is not supported by Detectron yet](https://github.com/facebookresearch/Detectron/issues/85)
* Ubuntu Linux
    * Tested in Ubuntu 16.04 LTS.
* CUDA 8 and above
    * Tested with CUDA 8 and CUDA 9.
* cuDNN 6 and above
* OpenCV 3.4
* Python dependencies
    * Detectron
    * Caffe2 (Detectron is powered by the [Caffe2](https://github.com/caffe2/caffe2) deep learning framework)

### Installing Detectron

How to install Detectron and its dependencies (including Caffe2). Please refer to this [guide](https://github.com/facebookresearch/Detectron/blob/master/INSTALL.md).

## Quick Start: Using Detectron

After installation, please see the following for brief instructions covering inference with Detectron.

## Inference with Pretrained Models

#### Directory of Image Files
To run inference on a directory of image files (`demo/*.jpg` in this example), you can use the `inference.py` tool. In this example, we're using an end-to-end trained Mask R-CNN model with a ResNet-101-FPN backbone from the model zoo:

First, place `inference.py` file in Detectron `tools` directory and `visualize.py` file in Detectron `lib/utils` directory. Then, run the following command:

```
python2 tools/infererence.py \
    --cfg configs/12_2017_baselines/e2e_mask_rcnn_R-101-FPN_2x.yaml \
    --output-dir /tmp/detectron-visualizations \
    --image-ext jpg \
    --wts https://s3-us-west-2.amazonaws.com/detectron/35861858/12_2017_baselines/e2e_mask_rcnn_R-101-FPN_2x.yaml.02_32_51.SgT4y1cO/output/train/coco_2014_train:coco_2014_valminusminival/generalized_rcnn/model_final.pkl \
    demo
```

Detectron should automatically download the model from the URL specified by the `--wts` argument. This tool will output visualizations of the detections in the directory specified by `--output-dir`.

**Notes:**

The code used for this demo in `inference.py` is the same as the one mentioned in [Detectron documentation](https://github.com/facebookresearch/Detectron/blob/master/GETTING_STARTED.md#1-directory-of-image-files) except with a few modifications to support webcam as input.

## Credits

Referenced these implementations:

1. [Demo with Mask R-CNN in Google Colab with GPU acceleration](https://github.com/OSSDC/OSSDC-VisionBasedACC/blob/master/image-segmentation/ossdc_matterport_Mask_RCNN_colaboratory.ipynb)
