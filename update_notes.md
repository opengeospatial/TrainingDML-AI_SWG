<!--
 * @Author: RuixiangLiuWHU lrx_lucky@whu.edu.cn
 * @Date: 2024-04-03 16:35:15
 * @LastEditors: RuixiangLiuWHU lrx_lucky@whu.edu.cn
 * @LastEditTime: 2024-04-19 19:29:39
 * @FilePath: \TrainingDML-AI_SWG\update_notes.md
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
# TrainingDML-AI's Update Notes - Part 1
## Comments from Broader Communities
### Update 1
- Comment: Might there be some enumeration of AI_Task?
- Response: We have changed the type of "taskType" from CharacterString to AI_EOTaskTypeCode, which is an enumeration class.
- Action: Defining an enumeration class AI_EOTaskTypeCode, including "scene classification", "object detection", "semantic segmentation", "change detection", "3D model reconstruction" and "instance segmentation"
### Update 2
- Comment: COCO uses an "isCrowd" property to indicate a requirement for Instance Segmentation. Would some uniformity in this area be useful?
- Response: We have added the property "isCrowd" into the class AI_ObjectLabel.
- Action: Adding "isCrowd [0..1]: Bool = false" to AI_ObjectLabel.
### Update 3
- Comment: Need two types of Provenance - both the lineage of the source imagery and the AI_Labeling provenance are needed to adequately address OE applications.
- Response: We have added the property "lineage" into the class AI_AbstractTrainingDataset and AI_AbstractTrainingData to represent the lineage information of the source imagery.
- Action: Adding "lineage [0..*]: LI_Lineage" to both AI_AbstractTrainingDataset and AI_AbstractTrainingData.
### Update 4
- Comment: Ultimately, these TDS determine the performance of the models that are trained on them. Can some good statistic(s) be developed that characterize the performance envelope one might expect to extract from a TDS?
- Response: TBD
- Action: WIP

## Comments from OAB
### Update 1
- Comment: For "imageFormat" property in AI_PixelLabel, is there an enumeration? Or can only media types be specified here?
- Response: We have changed the type of "imageFormat" from CharacterString to AI_ImageFormatCode, which is an enumeration class.
- Action: Defining an enumeration class AI_ImageFormatCode, whose value is defined in Multipurpose Internet Mail Extensions (MIME) Part Two: Media Types [RFC 2046](https://www.ietf.org/rfc/rfc2046.txt).
### Update 2
- Comment: For "methods" property in AI_LabelingProcedure, is there an enumeration? If not, then there will be an interoperability issue.
- Response: We have changed the type of "methods" from CharacterString to AI_LabelingMethodCode, which is an enumeration class.
- Action: Defining an enumeration class AI_LabelingMethodCode, including "manual", "semi-automatic", "automatic", "unknown"
### Update 3
- Comment: Making description Mandatory may result in nonsense entries.
- Response: We have made the description of all classes optional.
- Action: Making "description" property of all classes optional.
### Update 4
- Comment: Bit of confusion between id and datasetId.
- Response: The 'id' refers to the AI_TrainingData, representing the individual sample's ID, whereas 'datasetId' pertains to the ID of the dataset to which the sample belongs. Thus, they represent distinct levels, indicating that datasets and data have their respective IDs.
- Action: Changing the definition of "id" from "Identification of the AI training data." to "Identification of an individual AI training sample.".
### Update 5
- Comment: What about "retraining" in AI_TrainingTypeCode?
- Response: We have added "retraining" to this enumeration class.
- Action: Adding "retraining" to AI_TrainingTypeCode.
### Update 6
- Comment: Is dataURL sufficient to describe where a dataset is?
- Response: The dataURL points to the location where the AI_EOTrainingData is stored. Both relative paths and absolute paths, such as file paths and network addresses, can be expressed.
- Action: Changing the definition of "dataURL" from "URL of the EO data." to "URL of the EO data, including both relative and absolute paths, which can encompass local paths, network addresses, and more.".

## Comments from ISO
### Update 1
- Comment:
- Response:
- Action:






