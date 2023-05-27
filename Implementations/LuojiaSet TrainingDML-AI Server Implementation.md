# LuojiaSet TrainingDML-AI Server Implementation

[LuojiaSet](http://58.48.42.237/luojiaSet) has implemented the TrainingDML-AI Standard and utilized it to encode the data within the LuojiaSet dataset and customized code was developed to prototype the use cases of dataset. 

This implementation allows for retrieving the complete encoded content of the corresponding dataset by using the dataset record ID. 

## Demo deployment

- Landing page: http://58.48.42.237/luojiaSet/
- TrainingDML API document (Swagger): http://58.48.42.237/luojiaSet/31cacd67b152cdab9976d4718a0c51b3

Sample requests:

- The TrainingDML-AI encoding for the scene classification task dataset(RSI-CB256 Dataset) with the dataset ID:
  - http://58.48.42.237:3389/geois-boot/ogc/trainingDataset/14
- The TrainingDML-AI encoding for the semantic segmentation task dataset(AIRS Dataset) with the  dataset ID:
  - http://58.48.42.237:3389/geois-boot/ogc/trainingDataset/74
- The TrainingDML-AI encoding for the object detection task dataset(DOTA-v2.0 Dataset) with the  dataset ID:
  - http://58.48.42.237:3389/geois-boot/ogc/trainingDataset/9
- The TrainingDML-AI encoding for the change detection task dataset(OSCD Dataset) with the  dataset ID:
  - http://58.48.42.237:3389/geois-boot/ogc/trainingDataset/54
