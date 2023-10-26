# Deep Learning Model Extension of TrainingDML-AI

## 1. Abstract
The objective of the deep learning model extension (model-extension) is to develop the UML model and encoding to describe geospatial deep learning models. The model-extension will align with TrainingDML-AI and OGC standards baseline to facilitate the sharing, exchange, reusability, and inference of models in the web environment.

## 2. Scope of Work
The model-extension will undertake the following work actions around geospatial deep learning models:
- Design the UML model of geospatial deep learning models, maximize the findability, interoperability, and reusability;
- Define the description of neural network and optimization method of models;
- Define the description of model quality(e.g., performance metrics, computational complexity, generalization, robustness);
- Define the JSON schema for encoding geospatial deep learning models;
- Best practices for documenting, storing, evaluating, managing, and sharing the geospatial deep learning models.

## 3. UML Model
The core concepts of the model-extension are presented in Figure 1, followed by the specific concrete classes in Figure 2.      
The core concepts include:
- Deep Learning Model: This concept represents a deep learning model;
- Neural Network: This concept describes the neural network of the deep learning model;
- Optimization: This concept describes the information about how to train the deep learning model;
- Quality: This concept describes the quality of the deep learning model;
- Training Dataset: From TrainingDML-AI;
- Task: From TrainingDML-AI.
<div align=center>
<img width="600" src="UML/Conceptual Model.svg"/>
</div>
<div align=center> Figure 1. Conceptual model</div>

<div align=center>
<img width="900" src="UML/UML Model.svg"/>
</div>
<div align=center> Figure 2. UML model</div>

## 4. Use Cases
A collection of some encoded deep learning models:
|Model Name|Training Dataset|Description|JSON|Download|
|-|-|-|-|-|
|UPerNet_LULC|Five-Billion-Pixels|A land use land cover classification model based on UPerNet with 25 classes.|[UPerNet_LULC.json](use-cases/UPerNet_LULC.json)|[UPerNet_LULC.onnx](https://drive.google.com/file/d/1AcsTRsgHAwOROfq1qsa709kdKHleFmE0/view?usp=drive_link)|





