# Tensorflow Object Detection - HelmetDetection

This repository shows how to deploy Object Detection API - Tensorflow and give specific tutorials. It is based on [Object Detection](https://github.com/tensorflow/models/tree/master/research/object_detection). A specific example is to detect helmet, it could also explore to any other object detection tasks.

## Installation

* [Installation](https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/installation.md)

## Data Preparation

*Step 1*. Label - Generate the XML files based on original images, which means you locate the object in images and record the information into XML files. Label the image using [lablelImg](https://github.com/tzutalin/labelImg). The detailed explanation can be found [here](https://www.youtube.com/watch?v=K_mFnvzyLvc&list=PLQVvvaa0QuDcNK5GeCQnxYnSSaar2tpku&index=3). The Training data needs to follow the organization:

```
--data/train
    --Annotations
    --JPEGImages
```

If you have already have the datasets containing XML and JPG files, then you can skip to Step 2.

*Step 2*. Generate TF-Records. TensorFlow object detection API doesn’t take XML or Image files as an input, but it needs record files to train the model. In the example, I used `/data/cap_train.record` and `/data/cap_val.record` as input. You can generate the files using `/codes/create_helmet_record.py`, just remember to change the dir:

```
#  data_dir = FLAGS.data_dir
data_dir = '../data/train/'
#  label_map_dict = label_map_util.get_label_map_dict(FLAGS.label_map_path)
label_map_dict = label_map_util.get_label_map_dict('../models/faster_RCNN_Inception_v2/helmet_label_map.pbtxt')
```

`/models/faster_RCNN_Inception_resnet_v2/helmet_label_map.pbtxt` is a file for labeling. Give label name i.e helmet in my example. If in case you have multiple labels, increase id number starting from 1 and give appropriate label name.

```
item{
	id: 1
	name: 'helmet'
}

```

```
  num_train = int(0.8 * num_examples)
  train_examples = examples_list[:num_train]
  val_examples = examples_list[num_train:]
```

Above codes means how many datasets you split as train data and test data. I used `0.8` here.

## Train Model
Once the records files are ready, it's almost ready to train the model.

1.Choose the pre-trained model to be used. You could download [Tensorflow detection model zoo](https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/detection_model_zoo.md), which contains various pre-trained models. My example uses `/models/faster_RCNN_Inception_resnet_v2/faster_rcnn_inception_resnet_v2_atrous_coco_2018_01_28` for a better accuracy while with slower speed, and you could exchange to anyother models.

2.Remember to use the consistent config file for the same model. My example uses `/models/faster_RCNN_Inception_resnet_v2/faster_rcnn_inception_resnet_v2_atrous_coco_alldata.config`. Remember to change file dir in config file.

3.Make a new file object-detection.pbtxt which looks like this:


## Save Model


## Evaluate Model

### Calculating MAP@n 


### Evaluating a single image
