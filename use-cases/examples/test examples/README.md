# TrainingDML-AI Test Use Cases

## 1. Abstract

This folder contains some cases that are beyond the standard scope. These cases are intended to demonstrate the potential of the standard to support non-EO imagery data and unsupervised learning. Currently, the standard is still limited to EO imagery data and supervised learning.

## 2. Introduction

We have applied TrainingDML-AI to organize and encode the following five datasets to demonstrate its potential for organizing and encoding beyond the standard scope. In fact, these cases were developed in response to comments received during the OGC Public Comment stage. These cases cover the following aspects:

- "Data_for_detecting_interchanges" dataset for interchange detection;
- "ERA5_hourly_data" dataset for climate prediction and weather forecast;
- "TSMC2014_NYC" dataset for POI recommendation;
- "SCIRec" dataset for information extraction and entity recognition;
- "nuScenes" dataset for 3D object detection;

## 3. Cases

### 3.1. Data_for_detecting_interchanges

The source data for the "Data_for_detecting_interchanges" dataset is the Open Street Map (OSM) road network data, and the labels were annotated by the data provider. This dataset is a binary classification problem, with labels indicating whether a given road segment is an interchange or not. For this road network dataset, we inherit the Abstract class and define AI_FeatureTrainingDataset, AI_FeatureTrainingData, AI_FeatureTask, and AI_RoadSegmentLabel respectively. In addition, we have added additional attributes to support the complete representation of dataset information. The UML model for this dataset is shown in Figure 1.

<img src="file:///C:/Users/dell/AppData/Roaming/marktext/images/2023-04-30-23-06-55-image.png" title="" alt="" data-align="center">

Fig.1. The UML model of  "Data_for_detecting_interchanges" dataset

### 3.2. ERA5_hourly_data

The source data for the "ERA5_hourly_data" dataset is in-situ observational data (Copernicus product), and we limit its usage scenario to the autoregression problem of time series data. Therefore, its label is the data itself. Similar to unsupervised learning, the autoregression task for time series data do not require additional labeled data. For this dataset, we have not defined any inheritance class for AI_AbstractLabel, although this class is required in the existing standard (please note that these test cases are for future versions of the standard). In addition, we have added additional attributes to support the complete representation of dataset information. The UML model for this dataset is shown in Figure 2.

<img src="file:///C:/Users/dell/AppData/Roaming/marktext/images/2023-04-30-23-18-51-image.png" title="" alt="" data-align="center">

Fig.2. The UML model of "ERA5_hourly_data" dataset

### 3.3. TSMC2014_NYC

The source data for the "TSMC2014_NYC" dataset is POI data, and the goal of this dataset is POI recommendation, which is essentially a sequence data about location. During training and testing, each POI data can be either used as training data or testing data. For example, in two cycles, we respectively use the first 10 POIs to predict the location of the 11th POI, and use the 2nd-11th POIs data to predict the location of 
the 12th POI, and so on for other cycles. Therefore, for this dataset, we also did not define any inherited classes of AI_AbstractLabel, although this class is required in the current standard (please note that these test cases are for future versions of the standard). For this POI dataset, we inherit the Abstract class and define AI_POITrainingDataset, AI_POITrainingData, and AI_POITask respectively. In addition, we have added additional attributes to support the complete representation of dataset information.The UML model for this dataset is shown in Figure 3.

<img src="file:///C:/Users/dell/AppData/Roaming/marktext/images/2023-04-30-23-29-52-image.png" title="" alt="" data-align="center">

Fig.3. The UML model of "TSMC2014_NYC" dataset

### 3.4. SCIRec

The source data for the "SCIRec" dataset is textual data, and its labels are the classification of the text. This dataset is a text classification problem, with the goal of information extraction and entity recognition. For this textual dataset, we inherit the Abstract class and define AI_TextTrainingDataset, AI_TextTrainingData, AI_TextTask, and AI_EntityLabel respectively. In addition, we have added additional attributes to support the complete representation of dataset information. The UML model for this dataset is shown in Figure 4.

<img src="file:///C:/Users/dell/AppData/Roaming/marktext/images/2023-04-30-23-30-42-image.png" title="" alt="" data-align="center">

Fig.4. The UML model of "SCIRec" dataset

### 3.5. nuScenes

This dataset is a public large-scale dataset for autonomous driving developed by the team at Motional (formerly nuTonomy). The full dataset includes approximately 1.4M camera images, 390k LIDAR sweeps, 1.4M RADAR sweeps and 1.4M object bounding boxes in 40k keyframes. Although the training data may come from different domains, the 3D annotation boxes captured by numerous sensors in the same keyframe are targeted at the same object and are unique. Based on this, we use a 3D annotation box to organize each 3D object using AI_ObjectLabel. Since each training data and each 3D object require many additional attributes to be fully described, we have added many additional attributes to provide a detailed description of the training dataset, training data, labels, etc. The UML model for this dataset is shown in Figure 5.

<img src="file:///C:/Users/dell/AppData/Roaming/marktext/images/2023-04-30-23-31-21-image.png" title="" alt="" data-align="center">

Fig.5. The UML model of "nuScenes" dataset
