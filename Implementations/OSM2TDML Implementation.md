# OSM2TDML Implementation

[Ohsome2label]([GIScience/ohsome2label: Historical OpenStreetMap Objects to Machine Learning Training Samples (github.com)](https://github.com/GIScience/ohsome2label)) is a tool designed for efficiently downloading OSM data and WMTS tiles in order to generate deep learning samples. The annotation format used by ohsome2label is Microsoft COCO format. 

Recently, we have been working on enhancing the tool by adding more features and rewriting it. The engineering refactoring process is currently underway, and once it is completed, we will release a completely revamped version of the tool called OSM2TDML, which will offer end-to-end functionality.

So, we provide a Jupyter [notebook](https://gist.github.com/wuzyzy/523cd14473e769a87015af6f19d7105c) demo that demonstrates how to convert geococo format to tdml format. This demo serves as a preview of the forthcoming capabilities of the tool.

## USAGE

1. Download the `example_result` folder  and `config` folder in [Ohsome2label]([GIScience/ohsome2label: Historical OpenStreetMap Objects to Machine Learning Training Samples (github.com)](https://github.com/GIScience/ohsome2label)) repo.
2. Rename `config` folder to `example_config`.
3. Download and put the  [notebook](https://gist.github.com/wuzyzy/523cd14473e769a87015af6f19d7105c) in the same folder.
4. Run the notebook and you will get three tdml files in `example_result` folder, corresponding to `dltask` (`SemanticSegmentation`, `ObjectDetection` and `InstanceSegmentation`).

## Result snippets

### SemanticSegmentation

```json
{
    "id": "HD_landuse",
    "name": "HD_landuse",
    "description": "",
    "license": "",
    "data": [
        {
            "id": "0",
            "labels": [
                {
                    "type": "AI_PixelLabel",
                    "imageURL": [
                        "labels/14.8584.5595.png"
                    ],
                    "imageFormat": [
                        "png"
                    ]
                }
            ],
            "type": "AI_EOTrainingData",
            "dataURL": [
                "images/14.8584.5595.png"
            ]
        },
        ...
    ],
    "amountOfTrainingData": 24,
    "numberOfClasses": 2,
    "providers": [
        "ohsome2label"
    ],
    "type": "AI_EOTrainingDataset",
    "bands": [
        "RGB"
    ],
    "extent": [
        8.625,
        49.3711,
        8.7334,
        49.4397
    ],
    "dltask": {
        "id": "SemanticSegmentation"
    }
}
```

### ObjectDetection

```json
{
    "id": "HD_landuse",
    "name": "HD_landuse",
    "description": "",
    "license": "",
    "data": [
        {
            "id": "0",
            "labels": [
                {
                    "type": "AI_ObjectLabel",
                    "object": {
                        "type": "Feature",
                        "geometry": {
                            "type": "Polygon",
                            "coordinates": [
                                [
                                    [
                                        0.0,
                                        244.30855
                                    ],
                                    [
                                        0.0,
                                        93.844347
                                    ],
                                    [
                                        170.769579,
                                        93.844347
                                    ],
                                    [
                                        170.769579,
                                        244.30855
                                    ],
                                    [
                                        0.0,
                                        244.30855
                                    ]
                                ]
                            ]
                        },
                        "properties": {
                            "id": 0
                        }
                    },
                    "class": "urban",
                    "bboxType": "Horizental BBox"
                }
                ...
            ],
            "type": "AI_EOTrainingData",
            "dataURL": [
                "images/14.8584.5595.png"
            ]
        },
    "amountOfTrainingData": 24,
    "numberOfClasses": 2,
    "providers": [
        "ohsome2label"
    ],
    "type": "AI_EOTrainingDataset",
    "bands": [
        "RGB"
    ],
    "extent": [
        8.625,
        49.3711,
        8.7334,
        49.4397
    ],
    "dltask": {
        "id": "ObjectDetection"
    }
}
```

###  InstanceSegmentation

```json
{
    "id": "HD_landuse",
    "name": "HD_landuse",
    "description": "",
    "license": "",
    "data": [
    {
        "id": "0",
        "labels": [
            {
                "type": "AI_ObjectLabel",
                "object": {
                    "type": "Feature",
                    "geometry": {
                        "type": "Polygon",
                        "coordinates": [
                            [
                                [
                                    0.0,
                                    200.131218,
                                    0.0,
                                    209.060231,
                                    12.92544,
                                    216.322884,
                                    ...
                                 ]
                             ]
                            ],
                        "properties": {
                            "id": 0
                        }
                    }
                },
                "class": "urban"
            },
                ...
        ],
        "type": "AI_EOTrainingData",
        "dataURL": [
            "images/14.8584.5595.png"
        ]
    },
    "amountOfTrainingData": 24,
    "numberOfClasses": 2,
    "providers": [
        "ohsome2label"
    ],
    "type": "AI_EOTrainingDataset",
    "bands": [
        "RGB"
    ],
    "extent": [
        8.625,
        49.3711,
        8.7334,
        49.4397
    ],
    "dltask": {
        "id": "InstanceSegmentation"
    }
}
```

