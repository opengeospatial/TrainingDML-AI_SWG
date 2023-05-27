# PyTDML Implementation

[PyTDML](https://github.com/TrainingDML/pytdml) is a pure python parser and encoder for training datasets based on OGC Training Data Markup Language for AI standard.

---

## Usage

### Encoding

#### From the command line

The training dataset can be encoded to TrainingDML-AI JSON format by YAML configuration file with command line.

```bash
pytdml/yaml_to_tdml.py --config=<YAML configuration file path> --output=<Output TrainingDML-AI JSON file path>
```

YAML configuration file schema is described in [encoding YAML configuration file schema](https://github.com/TrainingDML/pytdml/blob/main/encoding_config_schema.yml).

#### Using the API from python

The training dataset can also be encoded to TrainingDML-AI JSON format with Python API.

```python
from pytdml.io import write_to_json
from pytdml.type import EOTrainingDataset, EOTrainingData, EOTask, EODataSource, SceneLabel

# generate EO training dataset
dataset = EOTrainingDataset(
    id='...',
    name='...',
    description='...',
    data=[
        EOTrainingData(
            id='...',
            labels=[
                SceneLabel(
                    label_class='...',
                    data_url='...',
                    date_time='...'),
                ...
            ]),
        ...
    ],
    version="...",
    amount_of_training_data=...,
    created_time="...",
    updated_time="...",
    providers=["..."],
    keywords=["...", "..."],
    tasks=[EOTask(task_type="...",
                  description="...")],
    data_sources=[EODataSource(
        id="...",
        data_type="...",
        resolution="..."
    )],
    classes=["...", "...", "..."],
    number_of_classes=...,
    bands=["...", "...", "..."],
    image_size="..."
)
# write to json
write_to_json(dataset, "dataset.json")
```

### Parsing

The training dataset described with TrainingDML-AI JSON file can be parsed with python API and transformed to
PyTorch/TensorFlow dataset.

#### Read TrainingDataset object from JSON file

```python
import pytdml

training_dataset = pytdml.io.read_from_json("dataset.json")  # read from TDML json file
print("Load training dataset: " + training_dataset.name)
print("Number of training samples: " + str(training_dataset.amount_of_training_data))
print("Number of classes: " + str(training_dataset.number_of_classes))
```

#### Transform to PyTorch dataset

- Scene classification dataset

```python
import pytdml
from torchvision import transforms

# Load the training dataset
training_dataset = pytdml.io.read_from_json("dataset.json")  # read from TDML json file

# Transform the training dataset
class_map = pytdml.ml.creat_class_map(training_dataset)  # create class map
train_dataset = pytdml.ml.TorchEOImageSceneTD(  # create Torch train dataset
    training_dataset.data,
    class_map,
    transform=transforms.Compose(  # transform for the training set
        [transforms.RandomResizedCrop(size=156, scale=(0.8, 1.0)),  # random resize
         transforms.RandomRotation(degrees=15),  # random rotate
         transforms.RandomHorizontalFlip(),  # random flip
         transforms.CenterCrop(size=124),  # center crop
         transforms.ToTensor(),  # transform to tensor
         transforms.Normalize([0.485, 0.456, 0.406], [0.229, 0.224, 0.225])  # normalize
         ]
    ))
```

- Object detection dataset

```python
import pytdml

# Load the training dataset
training_dataset = pytdml.io.read_from_json("dataset.json")  # read from TDML json file

# Transform the training dataset
class_map = pytdml.ml.creat_class_map(training_dataset)  # create class map
train_dataset = pytdml.ml.TorchEOImageObjectTD(  # create Torch train dataset
    training_dataset.data,
    class_map,
    transform=pytdml.ml.BaseTransform([128, 128])
)
```

- Semantic segmentation dataset

```python
import pytdml
from torchvision import transforms

# Load the training dataset
training_dataset = pytdml.io.read_from_json("dataset.json")  # read from TDML json file

# Transform the training dataset
class_map = pytdml.ml.creat_class_map(training_dataset)  # create class map
train_dataset = pytdml.ml.TorchEOImageSegmentationTD(  # create Torch train dataset
    training_dataset.data,
    class_map,
    transform=transforms.Compose([
        transforms.ToTensor(),
        transforms.Normalize(mean=[0.485, 0.456, 0.406], std=[0.229, 0.224, 0.225])
    ])
)
```

#### Transform to TensorFlow dataset

- Scene classification dataset

```python
import pytdml

# Load the training dataset
training_dataset = pytdml.io.read_from_json("dataset.json")  # read from TDML json file

# Transform the training dataset
class_map = pytdml.ml.creat_class_map(training_dataset)  # create class map
train_dataset = pytdml.ml.TensorflowEOImageSceneTD(  # create TensorFlow train dataset
    training_dataset.data,
    class_map
)
tf_train_dataset = train_dataset.create_dataset()
```

- Object detection dataset

```python
import pytdml

# Load the training dataset
training_dataset = pytdml.io.read_from_json("dataset.json")  # read from TDML json file

# Transform the training dataset
class_map = pytdml.ml.creat_class_map(training_dataset)  # create class map
train_dataset = pytdml.ml.TensorflowEOImageObjectTD(  # create TensorFlow train dataset
    training_dataset.data,
    class_map
)
tf_train_dataset = train_dataset.create_dataset()
```

- Semantic segmentation dataset

```python
import pytdml

# Load the training dataset
training_dataset = pytdml.io.read_from_json("dataset.json")  # read from TDML json file

# Transform the training dataset
class_map = pytdml.ml.creat_class_map(training_dataset)  # create class map
train_dataset = pytdml.ml.TensorflowEOImageSegmentationTD(  # create TensorFlow train dataset
    training_dataset.data,
    class_map
)
tf_train_dataset = train_dataset.create_dataset()
```

### Image Cropping

The images of training dataset in TrainingDML-AI JSON format can be cropped with command line for preprocessing.

```bash
pytdml/tdml_image_crop.py  --input=<Input original TrainingDML-AU file path> --output_json=<Output result TrainingDML-AI JSON file path>
                          --output_images=<Output dir of result cropped images> --size=<Crop size of images>
```
