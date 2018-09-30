# Tensorflow Object Detection - HelmetDetection

This repository shows how to deploy Object Detection API - Tensorflow and give specific tutorials. It is based on [Object Detection](https://github.com/tensorflow/models/tree/master/research/object_detection). A specific example is to detect helmet, it could also explore to any other object detection tasks.

## Installation

* [Installation](https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/installation.md)

## Data Prepare


Step 1. Label - Generate the XML files based on original images, which means you locate the object in images and record the information into XML files. Label the image using [lablelImg](https://github.com/tzutalin/labelImg). The detailed explanation can be found [here](https://www.youtube.com/watch?v=K_mFnvzyLvc&list=PLQVvvaa0QuDcNK5GeCQnxYnSSaar2tpku&index=3). The Training data needs to follow the organization:

```
--data/train
    --Annotations
    --JPEGImages
```

If you have already have the datasets containing XML and JPG files, then you can skip to Step 2.

Step 2. Generate TF-Records. TensorFlow object detection API doesn’t take XML or Image files as an input, but it needs record files to train the model. In the example, I used `/data/cap_train.record` and `/data/cap_val.record` as input. You can generate the files using 


## Train Model



## Save Model


## Evaluate Model

### Calculating MAP@n 


### Evaluating a single image
