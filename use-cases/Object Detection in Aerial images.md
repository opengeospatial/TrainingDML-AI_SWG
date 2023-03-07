## Object Detection in Aerial images

### Use Case Senario:
The object detection training dataset not only specifies the class information of objects, but also records the minimum bounding box labelled on the objects. Each image can have multiple objects as labels.  
The current object detection algorithms are divided into two categories, namely one-step and two-step detection methods. Two-step detection method means first detecting possible object regions and then classifying these regions into different classes. A typical algorithm is the Region-based Convolutional Network method (R-CNN). One-step detection method, such as the YOLO series method, propose to combine the two steps together to improve the detection speed.  

---

### Typical Training Dataset Description
An example training dataset for object detection is the Dataset for Object deTection in Aerial images-version 1.5 (DOTA-v1.5).  
DOTA-v1.5 dataset defines a label file for each image, in this file, the first line records the image source, the second line provides the resolution, and each of rest lines describes the annotation of an object.  

- The image sources of the dataset include Google Earth, Gaofen-2, and Jilin-1 provided by China Resources Satellite Data Center； 
- The 16 classes in DOTA-v1.5 are plane, ship, storage tank, baseball diamond, tennis court, basketball court, ground track field, harbor, bridge, large vehicle, small vehicle, helicopter, roundabout, soccer ball field, swimming pool, and container crane; 
- The images in the dataset have various image sizes (from 800×800 to 2000×2000) and resolutions (Google Earth/0.1m-1m, Gaofen-2/1m, Jilin-1/0.72m).
--- 

### Using TrainingDML-AI for DOTA-v1.5  
The training dataset template is discussed in https://gitlab.ogc.org/ogc/TrainingDML-AI/-/issues/3.   
By using the current version of template, the DOTA-v1.5 training dataset could be described as follows:  

- Training Dataset Name: DOTA-v1.5
- ID: dota_v1.5
- Description: DOTA is a large-scale dataset for object detection in aerial images. It can be used to develop and evaluate object detectors in aerial images. The images are collected from different sensors and platforms. Each image is of the size in the range from 800 × 800 to 20,000 × 20,000 pixels and contains objects exhibiting a wide variety of scales, orientations, and shapes
- Provider: Wuhan University
- Data Sources: Google Earth, Gaofen-2, Jilin-1
- Sensors/Instrument: N/A
- Task: Object detection in aerial images
- Number of Training Samples: 2806
- ML Targets: plane, ship, storage tank, baseball diamond, tennis court, basketball court, ground track field, harbor, bridge, large vehicle, small vehicle, helicopter, roundabout, soccer ball field, swimming pool, container crane
- Spatial Extent: N/A
- Spatial Resolution: Google Earth/0.1m-1m, Gaofen-2/1m, Jilin-1/0.72m
- Time Period: N/A
- Data Format: A label file for each image. In the file, the first line records the image source, and the second line provides the resolution. Then each of rest lines describes the annotation of an object using the following tuple: <x1, y1, x2, y2, x3, y3, x4, y4, class, isDiffDetectable>. Among them, “x1, y1, x2, y2, x3, y3, x4, y4” is the minimum bounding box of the object. “class” is the semantic category of the object. “isDiffDetectabl”e indicates whether the instance is difficult to be detected (1 for difficult, 0 for not difficult)
- Tags: N/A

