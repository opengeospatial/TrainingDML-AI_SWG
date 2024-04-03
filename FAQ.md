<!--
 * @Author: RuixiangLiuWHU lrx_lucky@whu.edu.cn
 * @Date: 2024-04-03 09:42:12
 * @LastEditors: RuixiangLiuWHU lrx_lucky@whu.edu.cn
 * @LastEditTime: 2024-04-03 16:01:26
 * @FilePath: \TrainingDML-AI_SWG\FAQ.md
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
# TrainingDML-AI's Frequently Asked Questions
## Overview
### AI_Task
- What are the types of AI_Tasks?
- Specific AI_Tasks may require special treatment?
### AI_TrainingDataset
- Is TrainingDML-AI (TDML) always about imagery? What is the span of TDML applications?
- Can LIDAR, RADAR, Point Clouds, etc., be handled?
### AI_TrainingData
- What is the relationship between "patch" and AI_TrainingData?
- No attribute to indicate the spectral bands of the EO imagery?
### AI_Label
- Is there guidance or preferred formats (or, indeed, sources) for labels?
- For Instance Segmentation: How is AI_Label organized?
- Multiple labels for a single example? How can hierarchies of labels be handled?
### AI_Labeling
- Need two types of Provenance - both the lineage of the source imagery and the AI_Label provenance are needed to adequately address OE applications.
- How can ISO 19115-1 lineage model and W3C PROV model be mapped in TDML?
### AI_DataQuality
- It seems odd to pick out "AI_ClassBalanceDegree" as the only one measure of quality. What are other quality measures?
### AI_TDChangeset
- Needs to be defined in a way to be independent of whether the versioning is via a centralized app such as Pachyderm or decentralized as in Git.
### TDML
- How close or far are the Training Data formats currently used in industry and government's applications?

## FAQ List
### What are the types of AI_Tasks?
Currently, AI_Tasks include scene classification, object detection, semantic segmentation, change detection, 3D model reconstruction, instance segmentation, etc.
### Specific AI_Tasks may require special treatment?
Special treatment for AI_Tasks can be realized by adding additional properties which are allowed in the encoding rules.
### Is TrainingDML-AI (TDML) always about imagery? What is the span of TDML applications?
TDML is not always about imagery. In the scope, TDML is limited in the EO imagery and the supervised learning. However, TDML can also support more applications, like automated driving, POI recommendation, climate prediction, information extraction, 3D object detection, etc.
- The ERA5 dataset is derived from in-situ observational data (Copernicus product), and we limit its usage scenario to the autoregression problem of time series data. Therefore, its label is the data itself. Similar to unsupervised learning, the autoregression task for time series data does not require additional labeled data. For this dataset, inheritance classes for AI_AbstractLabel are not defined, although this class is required in the existing standard (please note that these test cases are for future versions of the standard). In addition, additional attributes to support the complete representation of dataset information were added. An example of JSON encoding of the ERA5 dataset following the TrainingDML-AI UML model can be found in https://github.com/opengeospatial/TrainingDML-AI_SWG/blob/main/use-cases/examples/1.0/ERA5_hourly_data.json.
- The SCIERC dataset is derived from textual data, and its labels are the classification of the text. This dataset is a text classification problem, with the goal of information extraction and entity recognition. For this textual dataset, the Abstract class is inherited and AI_TextTrainingDataset, AI_TextTrainingData, AI_TextTask, and AI_EntityLabel respectively are defined. In addition, additional attributes to support the complete representation of dataset information were added. An example of JSON encoding of the SCIERC dataset following the TrainingDML-AI UML model can be found in https://github.com/opengeospatial/TrainingDML-AI_SWG/blob/main/use-cases/examples/1.0/SCIERC.json.
- The nuScenes dataset is a public large-scale dataset for autonomous driving developed by the team at Motional (formerly nuTonomy). The full dataset includes approximately 1.4M camera images, 390k LIDAR sweeps, 1.4M RADAR sweeps and 1.4M object bounding boxes in 40k keyframes. Although the training data may come from different domains, the 3D annotation boxes captured by numerous sensors in the same keyframe are targeted at the same object and are unique. Based on this, a 3D annotation box is used to organize each 3D object using AI_ObjectLabel. Since each training data and each 3D object require many additional attributes to be fully described, many additional attributes to provide a detailed description of the training dataset, training data, labels, etc. were added. An example of JSON encoding of the nuScenes dataset following the TrainingDML-AI UML model can be found in https://github.com/opengeospatial/TrainingDML-AI_SWG/blob/main/use-cases/examples/1.0/nuScenes.json.
### Can LIDAR, RADAR, Point Clouds, etc., be handled?
LIDAR (Point Clouds), RADAR (Image/Point Clouds), Point Clouds can be handled.
- The Toronto3D dataset is a large urban outdoor point cloud dataset for segmentation collected by the Mobile Laser Scanning System. The dataset covers about 1 km of scene streets in Toronto, including four areas named L001, L002, L003, and L004, with a total of 78.3 million points. Each point in this dataset has 10 attributes representing the 3D position, RGB color, intensity, GPS time, scan angle rank, and category, respectively. This dataset has eight categories, including road, road mark, natural, building, utility line, pole, car, and fence. An example of JSON encoding of the Toronto3D dataset following the TrainingDML-AI UML model can be found in https://github.com/opengeospatial/TrainingDML-AI_SWG/tree/main/use-cases/examples/1.0/Toronto_3D.json.
### What is the relationship between "patch" and AI_TrainingData?
Note that one "patch" could contain the entire collection of labeled instanced in a Training Data Set, having perhaps hundreds of or even thousands of labeled examples in this one patch.
### No attribute to indicate the spectral bands of the EO imagery?
For a TrainingDataset, all the bands of the TrainingData must be the same across the entire TrainingDataset. Even in change detection, a training data includes two images. From this perspective, the bands of each training data in the entire dataset are also the same, except that these bands are jointly composed of two images.
### Is there guidance or preferred formats (or, indeed, sources) for labels?
For AI_ObjectLabel, the preferred format is OGC Feature which is defined by OGC. In GML, a feature is nothing more than a list of properties and geometries. In GeoJSON, a feature has a “type” member with the value “Feature”, also members with names of “geometry” and “properties”.
For AI_SceneLabel, we can use “class” to represent the label.
For AI_PixelLabel, we can use “imageURL” and “imageFormat” properties.
### For Instance Segmentation: How is AI_Label organized?
For instance segmentation, TDS can be organized by both the AI_PixelLabel and the AI_ObjectLabel. "AI_ObjectLabel" can represent the object detection labels. "AI_PixelLabel" can represent the semantic segmentation labels.
### Multiple labels for a single example? How can hierarchies of labels be handled?
When dealing with multiple labels for a single example, we utilize the "classificationScheme" (a property in AI_TrainingDataset) to depict the hierarchy of the labels. The "classificationScheme" is of type "CharacterString," suggesting an external definition. This external definition is represented by referencing a specific URL or others.
### Need two types of Provenance - both the lineage of the source imagery and the AI_Label provenance are needed to adequately address OE applications.
We will add "lineage" property both in AI_TrainingDataset and AI_TrainingData in the next version of TDML, to represent the lineage of the source imagery. This property is of type "LI_Lineage", which is defined in ISO 19115-1 lineage model.
### How can ISO 19115-1 lineage model and W3C PROV model be mapped in TDML?
AI_Labeling includes the labeler and the labeling procedure, which can be mapped to the agent and activity respectively in W3C PROV model. The labeler identifies the agent that creates the training dataset or individual samples, and the labeling procedure represents the process for data generation. AI_Labeling can also describe how the input data of the TD has been manipulated, such as resampled, color corrected, atmospherically corrected, and terrain corrected. For example, imagery with 10-cm and 15-cm resolution was resampled to 20-cm prior for labeling. 
Alternatively, despite the simple payload in this TrainingDML-AI Standard, providing a comprehensive definition of provenance using the ISO 19115 lineage model through a metadata association in the data is also applicable. 
### It seems odd to pick out "AI_ClassBalanceDegree" as the only one measure of quality. What are other quality measures?
AI_ClassBalanceDegree defines the quality elements for measuring degree of class balance of training datasets, which is an extension of the QualityElement defined in ISO 19157-1:2023. For other quality elements and measures in ISO 19157-1:2023, we provide a table for all possible quality measures that can be added to the TDML (especially for those who cannot reach ISO documents).
<table>
    <tr>
        <th width="10%">Level</th><th width="20%">EO Task Types</th><th width="20%">Quality Elements (From ISO 19157-1:2023)</th><th width="50%">Quality Measures</th>
    </tr>
    <tr>
        <td rowspan="6">Scene</td><td rowspan="6">Scene Classification</td><td>Completeness</td><td>Commission, Omission</td>
    </tr>
    <tr>
        <td>LogicalConsistency</td><td>DomainConsistency, FormatConsistency</td>
    </tr>
    <tr>
        <td>PositionalAccuracy</td><td>/</td>
    </tr>
    <tr>
        <td>ThematicQuality</td><td>ThematicClassificationCorrectness, NonQuantitativeAttributeCorrectness, QuantitativeAttributeCorrectness</td>
    </tr>
    <tr>
        <td>TemporalQuality</td><td>AccuracyOfATimeMeasurement</td>
    </tr>
    <tr>
        <td>QualityExtension (From TrainingDML-AI)</td><td>AI_ClassBalanceDegree</td>
    </tr>
    <tr>
        <td rowspan="6">Object</td><td rowspan="6">Object Detection</td><td>Completeness</td><td>Commission, Omission</td>
    </tr>
    <tr>
        <td>LogicalConsistency</td><td>DomainConsistency, FormatConsistency, TopologicalConsistency</td>
    </tr>
    <tr>
        <td>PositionalAccuracy</td><td>AbsolutePositionalAccuracy</td>
    </tr>
    <tr>
        <td>ThematicQuality</td><td>ThematicClassificationCorrectness, NonQuantitativeAttributeCorrectness, QuantitativeAttributeCorrectness</td>
    </tr>
    <tr>
        <td>TemporalQuality</td><td>AccuracyOfATimeMeasurement</td>
    </tr>
    <tr>
        <td>QualityExtension (From TrainingDML-AI)</td><td>AI_ClassBalanceDegree</td>
    </tr>
    <tr>
        <td rowspan="6">Pixel</td><td rowspan="6">Land Cover Classification, Land Use Classification, Change Detection, 3D Reconstruction</td><td>Completeness</td><td>Commission, Omission</td>
    </tr>
    <tr>
        <td>LogicalConsistency</td><td>DomainConsistency, FormatConsistency</td>
    </tr>
    <tr>
        <td>PositionalAccuracy</td><td>/</td>
    </tr>
    <tr>
        <td>ThematicQuality</td><td>ThematicClassificationCorrectness, NonQuantitativeAttributeCorrectness, QuantitativeAttributeCorrectness</td>
    </tr>
    <tr>
        <td>TemporalQuality</td><td>AccuracyOfATimeMeasurement, TemporalValidity, TemporalConsistency</td>
    </tr>
    <tr>
        <td>QualityExtension (From TrainingDML-AI)</td><td>AI_ClassBalanceDegree</td>
    </tr>
</table>

### Needs to be defined in a way to be independent of whether the versioning is via a centralized app such as Pachyderm or decentralized as in Git.
In Git, the version control workflow typically involves creating branches, making changes to files, committing those changes to the local repository, and eventually pushing those commits to a remote repository. When multiple users make changes to the same branch or file, Git requires merging those changes together to create a unified version history. This merging process can sometimes lead to conflicts that need to be resolved manually, especially if two users modify the same part of a file.

Pachyderm, on the other hand, handles version changes differently. When data is submitted to Pachyderm, it creates a new commit, representing a version change, in the data repository. Each commit in Pachyderm is immutable, meaning it cannot be modified once created. Instead of merging changes together, Pachyderm creates separate branches for each commit, allowing users to explore different versions of the data or pipeline without affecting the main branch. This approach eliminates the need for merging and reduces the risk of conflicts arising from concurrent changes.

The key difference between Git and Pachyderm in version control lies in their handling of branches and merging. While Git requires merging changes from different branches to maintain a unified version history, Pachyderm creates separate branches for each commit, enabling parallel development without the need for manual merging. This approach simplifies version management and reduces the likelihood of conflicts, particularly in collaborative environments where multiple users are making concurrent changes to data or pipelines.

As the AI_TDChangeset defined by us is a conceptual model, simply recording attributes such as ID, version number, modification count, creation time, additions, deletions, modifications, and others, its compatibility is independent of whether versioning is facilitated by a centralized application like Pachyderm or a decentralized system like Git. The AI_TDChangeset can accommodate the usage scenarios of both these tools.
### How close or far are the Training Data formats currently used in industry and government's applications?

|                 |           SpaceNet            | Kaggle                          | STAC            | AIREO                       | COCO              | OGC Testbeds     | DataBricks                |
| --------------- | :---------------------------: | ------------------------------- | --------------- | --------------------------- | ----------------- | ---------------- | ------------------------- |
| Data model      | Tiles, chips, Various structs | File                            | Item            | Profile                     | Annotation        | Coverage/Feature | Well-defined Feature sets |
| Metadata        |        AWS Marketplace        | Ad Hoc                          | Item Properties | Profile metadata            | Annotation info   | CSW metadata     | Proprietary tags          |
| Label Semantics |        Per competition        | N/A                             | Label: classes  | Classes                     | Categories        | CVM              | Externally defined        |
| Provenance      |              N/A              | Sources, collection methodology | Label: Methods  | Provenance property         | Info: contributor | N/A              | Extended Lineage          |
| Data Quality    |  Q1ty indicators for profile  | Competition metrics             | N/A             | Q1ty indicators for profile | N/A               | N/A              | Extended Lineage          |
| Changeset       |              N/A              | Pinned Docker Containers        | N/A             | N/A                         | N/A               | N/A              | Fine Grained Audit Logs   |
| Encoding        |            various            | Ad Hoc                          | JSON            | JSON                        | JSON              | JSON/XML         | SQL                       |
| API             |        Download Links         | Download Links                  | STAC API        | STAC API                    | COCO API          | OGC WCS/WFS      | External Integrations     |

[PyTDML](https://github.com/openrsgis/pytdml) provides a tool for converting datasets encoded in other formats to TDML encoding.
