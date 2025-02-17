<!--
 * @Author: RuixiangLiuWHU lrx_lucky@whu.edu.cn
 * @Date: 2023-05-30 09:57:22
 * @LastEditors: RuixiangLiuWHU lrx_lucky@whu.edu.cn
 * @LastEditTime: 2025-02-17 15:33:07
 * @FilePath: \TrainingDML-AI_SWG\Implementations\README.md
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
# Implementations

work-in-progress

This page provides a list of implementations based on the OGC Training Data Markup Language for Artificial Intelligence (TrainingDML-AI) Standard. These implementations are designed to support the adoption and utilization of the TrainingDML-AI Standard across different platforms and applications. They offer a variety of tools, libraries, and APIs that enable users to work with training data in a standardized and interoperable manner. Whether you need to manage, annotate, share, or analyze training data for AI purposes, these implementations provide the necessary resources and functionalities to support your workflow.

## Contribution

If you have any implementations or contributions related to TrainingDML-AI, we welcome pull requests to update this page and add your contributions. You can provide more detailed information about your implementation in a subfolder. Please provide your email address so that we can contact you for page updates or any questions.

## PyTDML Implementation

[PyTDML](https://github.com/openrsgis/pytdml) is a pure python parser and encoder for training datasets based on OGC Training Data Markup Language for AI standard.

Additionally, PyTDML is currently in the process of designing and implementing a pipeline service that enables the entire workflow from sample loading to sample consistency handling, sample transformation, and iterative training. We have designed user-friendly APIs that adhere to the OGC TrainingDML-AI Standard. With these APIs, users can automate the process of feeding TrainingDML-AI-encoded datasets into deep learning frameworks such as PyTorch, TensorFlow, and others.

## TrainingDML-AI STAC Extension Implementation

[TrainingDML-AI STAC Extension](https://github.com/openrsgis/trainingdml-ai-extension) is designed as an extension to the SpatioTemporal Asset Catalog (STAC) specification. It builds upon the STAC specification and specifically addresses the requirements for geospatial machine learning training data and introduces additional fields and metadata concepts to formalize the information model of training data within the STAC framework.The extension expands upon the core STAC specification to accommodate the specific needs of training data, enabling interoperability and facilitating effective management and utilization of geospatial machine learning training datasets within the STAC ecosystem.
Now you can find the TrainingDML-AI Extension in the [STAC GitHub repository](https://stac-extensions.github.io/). The current maturity level is Proposal, and the release version is 1.0.0.

## LuojiaSet TrainingDML-AI Server Implementation

[LuojiaSet](http://58.48.42.237/luojiaSet) has implemented the TrainingDML-AI Standard and utilized it to encode the data within the LuojiaSet dataset and customized code was developed to prototype the use cases of dataset.

This implementation allows for retrieving the complete encoded content of the corresponding dataset by using the dataset record ID.

## PIE (Pixel Information Expert) Engine Online Dataset Implementation

[The PIE engine](https://engine.piesat.cn/)'s online model training module has implemented support for TrainingDML-AI encoding format in dataset import, as well as dataset export using the TrainingDML-AI format allowing users to easily upload their datasets to the platform for training purposes.

This implementation also ensures the integrity and effectiveness of the datasets used for training. By validating the data format, the platform can confirm that the datasets adhere to the required structure and standards. You can find the introduction [here](https://github.com/openrsgis/ImplementationCaseOfPIE).

## Pixalytics Plastics Detection Dataset Implementation

The implementation is based on work undertaken as part of the OGC Testbed activities, where Python code was developed to catalog a Machine Learning dataset that has been extended to use the [PyTDML](https://github.com/openrsgis/pytdml) to store the metadata in the TrainingDML-AI format.

## GeoLabs TDML-as-a-service Implementation

In OGC Testbed-19: Machine Learning Models Engineering Report, GeoLabs made an implementation:

/tdml — TDML-as-a-service: Endpoint implementing generation of training data encodings in a JSON file format based on the OGC Training-DML for AI Standard.
![TDML-as-a-service](geolabs-t19-er.png)

## The First Institute of Photogrammetry & Remote Sensing, MNR Classification Task Implementation

The First Institute of Photogrammery & Remote Sensing, MNR Uses training data in TrainingDML-AI format and performs training tasks (semantic segmentation and change detection) based on the TrainingDML-AI Standard.

The main training process can be outlined as follows:

1. Utilizing the LuojiaSet's API to incorporate the category system of MNR into the library, supporting a multi-level category system.
2. Leveraging the LuojiaSet's API to parse the datasets comprehensively, encompassing both metadata and raw data parsing.
3. Utilizing the LuojiaSet's API to transform the datasets into the TrainingDML-AI format.
4. Uploading the PyTDML installation package.
5. Developing deep learning code wherein PyTDML reads the training data in the TrainingDML-AI format and undergoes training tasks.

## Flame and Smoke Detection Dataset (FASDD) Implementation

We constructed a 100,000-level Flame and Smoke Detection Dataset (FASDD) based on the OGC TrainingDML-AI (TDML) standard. FASDD stands as a pivotal benchmark, propelling continuous evolution in fire detection models for object detection tasks. FASDD dataset has been encoded into TrainingDML-AI format.

## OSM2TDML Implementation

[Ohsome2label](https://github.com/GIScience/ohsome2label) is a tool designed for efficiently downloading OSM data and WMTS tiles in order to generate deep learning samples. The annotation format used by ohsome2label is Microsoft COCO format. 
Recently, we have been working on enhancing the tool by adding more features and rewriting it. The engineering refactoring process is currently underway, and once it is completed, we will release a completely revamped version of the tool called OSM2TDML, which will offer end-to-end functionality.
So, we provide a Jupyter [notebook](https://gist.github.com/wuzyzy/523cd14473e769a87015af6f19d7105c) demo that demonstrates how to convert geococo format to tdml format. This demo serves as a preview of the forthcoming capabilities of the tool.

## ISO 19178 Series

The transformation of the OGC TrainingDML-AI standard into the ISO 19178 series aims to standardize the OGC (Open Geospatial Consortium) technologies and methodologies, aligning them with the international standard framework of ISO (International Organization for Standardization).

The [ISO 19178-1](https://www.iso.org/standard/89050.html) is under development.

## National Standard in SAC (Standardization Administration of China)

The transformation of the OGC TrainingDML-AI standard into a national standard by the SAC (Standardization Administration of China) is aimed at standardizing cutting-edge geospatial data technologies and artificial intelligence (AI) methods to better suit China’s practical application needs. The release of the SAC [national standard](https://std.samr.gov.cn/gb/search/gbDetailed?id=20A56843E0E324D4E06397BE0A0AB583) signifies that this standard will be widely adopted within China, driving the standardization of geospatial data management, processing, storage, and analysis. It enhances interoperability in Geographic Information Systems (GIS) and big data technologies, thus boosting the country’s technological innovation in related fields.

## Land Satellite Remote Sensing Application Center, MNR Implementation

Based on the TrainingDML-AI standard, the Land Satellite Remote Sensing Application Center, MNR (Ministry of Natural Resources) has constructed a sample database of satellite imagery related to China. This database aims to enhance the processing, storage, and analysis capabilities of satellite imagery data for China through standardized geospatial data management methods and AI technologies. It plays a significant role in advancing remote sensing technology applications in areas such as natural resource management, environmental monitoring, agriculture, and urban planning.

## AI4QC Training Data Platform

The [Artificial Intelligence for Quality Control (AI4QC) project](http://eodata.bvlabs.ai/ai4qc/#/) is a research and development initiative funded by the European Space Agency (ESA). This project aims to create a robust AI framework for the automated and accurate detection of clouds and anomalies in the vast data streams from the Copernicus Sentinel-1 and Sentinel-2 missions. These AI models are essential for Quality Control (QC) services to efficiently handle the increasing volume and complexity of satellite Earth Observation (EO) data from current and future missions. The AI4QC project specifically targets a set of Sentinel-1 and Sentinel-2 anomalies identified and agreed upon by our team of data scientists and sensor experts. These anomalies include Clouds, Radiation Frequency Interference (RFI), Image Artifacts, and newly detected anomalies. To ensure high-quality results, all relevant data has been meticulously collected and curated, covering applicable missions, product types, and detection tasks. The datasets have been formatted into an [AI-ready format](https://github.com/biasvariancelabs/AI4QC?tab=readme-ov-file), facilitating effective AI model training, validation, and testing. These curated and AI-ready datasets are now available on AI4QC training data platform.