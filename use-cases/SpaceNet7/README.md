# Introduction

The SpaceNet 7 Multi-Temporal Urban Development Challenge aims to identify and track buildings in satellite imagery time series collected over rapidly urbanizing areas.

The competition centers around a new open source dataset of Planet satellite imagery mosaics, which includes 24 images (one per month) covering ~100 unique geographies.

---

# Encode SpaceNet 7 Dataset with TrainingDML-AI

## Download SpaceNet 7 Dataset

The SpaceNet 7 Dataset is available on https://mlhub.earth/data/spacenet7, it is split to Imagery Collections and Label Collections, both of them are managed by STAC catalog archive.

## Install pytdml

[pytdml](https://github.com/TrainingDML/pytdml) is a pure python parser and encoder for training datasets based on OGC
Training Data Markup Language for AI standard. The package can be installed via pip.

```bash
pip install pytdml
```

## Create YAML configuration file

```yaml
dataset_type: EOTrainingDataset
id: spacenet_7
name: SpaceNet 7 Multi-Temporal Urban Development Challenge
description: The SpaceNet 7 Multi-Temporal Urban Development Challenge aims to help address this deficit and develop novel computer vision methods for non-video time series data.
version: 1.0
created_time: 2020
updated_time: 2020
license: CC-BY-SA-4.0
providers:
  - SpaceNet LLC
keywords:
  - Building Footprints
classes:
  - Building
tasks:
  - description: Identify and track buildings in satellite imagery time series
    task_type: Building Object Change Detection
data_sources:
  - id: mosaic-image
    data_type: Optical Image
    format: tif
bands:
  - red
  - green
  - blue
image_size: 1024x1023
data:
  task_type: ObjectDetection
  label_type: ObjectLabel
  data_path:
    - type: image
      format: stac
      root_path: D:\TrainingDatasets\SpaceNet7\sn7_train_source
    - type: label
      format: stac
      root_path: D:\TrainingDatasets\SpaceNet7\sn7_train_labels

```

## Execute YAML to TrainingDML-AI

The SpaceNet 7 Dataset can be encoded to TrainingDML-AI JSON format by YAML configuration file with command line.

```bash
pytdml/yaml_to_tdml.py --config=./SpaceNet7.yml --output=./SpaceNet7.json
```

## Result snippet

```json
{
    "type": "EOTrainingDataset",
    "id": "spacenet_7",
    "name": "SpaceNet 7 Multi-Temporal Urban Development Challenge",
    "description": "The SpaceNet 7 Multi-Temporal Urban Development Challenge aims to help address this deficit and develop novel computer vision methods for non-video time series data.",
    "version": 1.0,
    "amountOfTrainingData": 1423,
    "createdTime": 2020,
    "updatedTime": 2020,
    "providers": [
        "SpaceNet LLC"
    ],
    "keywords": [
        "Building Footprints"
    ],
    "numberOfClasses": 1,
    "classes": [
        "Building"
    ],
    "dataSources": [
        {
            "id": "mosaic-image",
            "dataType": "Optical Image",
            "format": "tif"
        }
    ],
    "bands": [
        "red",
        "green",
        "blue"
    ],
    "imageSize": "1024x1023",
    "tasks": [
        {
            "type": "EOTask",
            "description": "Identify and track buildings in satellite imagery time series ",
            "taskType": "Building Object Change Detection"
        }
    ],
    "quality": {
        "type": "EOTrainingDataQuality"
    },
    "data": [
        {
            "type": "EOTrainingData",
            "id": "sn7_train_source_L15-0760E-0887N_3041_4643_13_2019_11",
            "numberOfLabels": 9869,
            "labels": [
                {
                    "type": "ObjectLabel",
                    "object": {
                        "type": "Feature",
                        "properties": {
                            "Id": 0
                        },
                        "geometry": {
                            "type": "Polygon",
                            "coordinates": [
                                [
                                    [
                                        -46.34991422622779,
                                        -23.402725520530783
                                    ],
                                    [
                                        -46.35016090654362,
                                        -23.402725520530783
                                    ],
                                    [
                                        -46.35015403375182,
                                        -23.402677860982877
                                    ],
                                    [
                                        -46.3499116004759,
                                        -23.402707308301753
                                    ],
                                    [
                                        -46.34991422622779,
                                        -23.402725520530783
                                    ]
                                ]
                            ]
                        }
                    }
                }
            ]
        }
    ]
}
```