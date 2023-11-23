# Deep Learning Model Extension of TrainingDML-AI

## 1. Abstract
The deep learning model extension (model-extension) of TrainingDML-AI aims to develop the UML model and encodings to describe geospatial deep learning models. The model-extension will align with TrainingDML-AI and OGC standards baseline to facilitate the sharing, exchange, reusability, and inference of models in the web environment.

## 2. Scope of Work
Deep learning has significantly contributed to geospatial analysis and revolutionized how we understand and extract information from geospatial data. Nowadays, abundant deep learning models are trained daily to accomplish various geospatial tasks, such as land cover and land use mapping, change detection, road network extraction, geospatial data fusion, etc. However, the information of most models has not been described and recorded standardized, which brings difficulties to the sharing and reusing of models and is not conducive to interoperability and reusability. Hence, the model-extension is proposed to develop the UML model to standardize the deep learning framework, neural network, optimization method, training data, tasks, quality, etc., of geospatial deep learning models so that the models can be shared and managed in a unified framework. 
The model-extension will undertake the following work actions around geospatial deep learning models:
- Design the UML model of geospatial deep learning models, maximize the findability, interoperability, and reusability;
- Define the description of neural network and optimization method of models;
- Define the description of model quality(e.g., performance metrics, computational complexity, generalization, robustness);
- Define the JSON schema for encoding geospatial deep learning models;
- Best practices for documenting, storing, evaluating, managing, and sharing the geospatial deep learning models.

## 3. Normative References
The following normative documents contain provisions that, through reference in this text, constitute provisions of this document. For dated references, subsequent amendments to, or revisions of, any of these publications do not apply. For undated references, the latest edition of the normative document referred to applies.

[ISO 19157-1 Geographic information — Data quality — Part 1: General requirements.](https://www.iso.org/standard/78900.html)

## 4. UML Model
The UML model is the normative definition of the TDML model-extension Conceptual Model. The figures in this section were software generated from the UML model. As such, this section provides a normative representation of the TDML model-extension Conceptual Model.

### 4.1	Overview of the UML model
The UML model is presented with core concepts in Figure 1. The following describes the core concepts:
- AI_DeepLearningModel: This concept represents a deep learning model;
- AI_NeuralNetwork: This concept describes the neural network of the deep learning model;
- AI_Optimization: This concept describes the information about how to train the deep learning model;
- AI_ModelQuality: This concept describes the quality of the deep learning model;
- AI_TrainingDataset: From TrainingDML-AI;
- AI_Task: From TrainingDML-AI.

<div align=center> 
<img width="600" src="UML/Conceptual Model.svg"/>
</div>
<div align=center> Figure 1. Core concepts.</div>

The full overview of concrete classes and attributes are presented in Figure 2. Concepts related to the EO AI/ML applications are defined as classes extended from abstract classes. Each core concept with related classes will be described in the rest subsections.

<div align=center>
<img width="900" src="UML/UML Model.svg"/>
</div>
<div align=center> Figure 2. UML model</div>

## 5. Use Cases
A collection of some encoded deep learning models:
|Model Name|Training Dataset|Description|JSON|Download|
|-|-|-|-|-|
|UPerNet_LULC|Five-Billion-Pixels|A land use land cover classification model based on UPerNet with 25 classes.|[UPerNet_LULC.json](use-cases/UPerNet_LULC.json)|[UPerNet_LULC.onnx](https://drive.google.com/file/d/1AcsTRsgHAwOROfq1qsa709kdKHleFmE0/view?usp=drive_link)|





