<!--
 * @Author: RuixiangLiuWHU lrx_lucky@whu.edu.cn
 * @Date: 2023-12-19 22:30:37
 * @LastEditors: RuixiangLiuWHU lrx_lucky@whu.edu.cn
 * @LastEditTime: 2023-12-19 22:35:49
 * @FilePath: \TrainingDML-AI_SWG\Implementations\Flame and Smoke Detection Dataset (FASDD) Implementation.md
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
# Flame and Smoke Detection Dataset (FASDD) Implementation

We constructed a 100,000-level Flame and Smoke Detection Dataset (FASDD) based on the OGC TrainingDML-AI (TDML) standard. FASDD stands as a pivotal benchmark, propelling continuous evolution in fire detection models for object detection tasks. FASDD dataset has been encoded into TrainingDML-AI format.

FASDD is an open-access fire detection dataset created by Professor Peng Yue's team at the School of Remote Sensing and Information Engineering, Wuhan University. FASDD serves as a challenging benchmark for object detection tasks and features three sub-datasets: FASDD_CV, FASDD_UAV, and FASDD_RS. These sub-datasets comprise cross-domain images from terrestrial, airborne, and spaceborne sensors, respectively. FASDD encompasses a wide range of variations, including image size, resolution, illumination (day and night), scenario (indoor and outdoor), perspective range (far and near), viewing angle (top view and side view), platforms (surveillance cameras, drones, and satellites), and data source (Internet, social media, and open-access fire datasets). Additionally, a unified workflow for preprocessing, annotation, and quality control is established, providing out-of-the-box annotations in four different formats to facilitate deep learning model training. FASDD stands as a pivotal benchmark, propelling continuous evolution in fire detection models for object detection tasks.

## Data availability

FASDD can be accessed freely from the Science Data Bank website at https://doi.org/10.57760/sciencedb.j00104.00103. However, due to the paper not being published yet, the dataset is currently under embargo. The dataset is provided in three compressed files: FASDD_CV.zip, FASDD_UAV.zip, and FASDD_RS.zip, which correspond to the Computer Vision dataset, the Unmanned Aerial Vehicle dataset, and the Remote Sensing dataset, respectively. Each zip file contains two folders: "images" for storing the source data and "annotations" for storing the labels. The "annotations" folder consists of label files in four formats: VOC, COCO, YOLO, and TrainingDML-AI. The dataset is divided randomly into training, validation, and test sets, with a ratio of 1/2, 1/3, and 1/6, respectively, within each label format. The image and label names are prefixed with "Fire", "Smoke", "FireAndSmoke", and "NeitherFireNorSmoke", representing different categories for scene classification tasks.

## Dataset encoded in TrainingDML-AI format

1. The FASDD dataset completes dataset parsing, including metadata parsing as well as raw data parsing, through LuojiaSet's object detection Task Upload API, and is uploaded to the training  data hub;
2. The FASDD dataset is encoded into TrainingDML-AI format by LuojiaSet's TrainingDML-AI encoding API;

