<!--
 * @Author: RuixiangLiuWHU lrx_lucky@whu.edu.cn
 * @Date: 2024-04-03 16:35:15
 * @LastEditors: RuixiangLiuWHU lrx_lucky@whu.edu.cn
 * @LastEditTime: 2024-05-10 11:41:38
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
- Comment: The Training Dataset environment has a high influence in the model trained with it，and consequently in the obtained predictions. I mean, for example, a high variety of environments/landscapes in the Datasets are required for obtaining a model able to detect objects within all of them. (This issue could be related with the “optimal applicable geographical region” defined in the extension for GeoAI models standardization proposed for the future)
- Proposed Change: Introducing an attribute defining the “Main Environment” of the Dataset (urban/rural/different land uses.. ) or even the different percentages. .
- Action: Adding "regionEnvironment [0..1]: CharacterString" to AI_AbstractTrainingDataset
### Update 2
- Comment: 
>Defines the description of quality (e.g. training data errors, training data **unrepresentativeness**) and the provenance (labeling, labeler, and labeling procedure).

While understood, a description of the highlighted word with a synonym could be helpful.
- Proposed Change: Modify the vocabulary expressions of the highlighted word.
- Action: Corrected to the following sentence: 
>Defines the description of quality (e.g. training data errors, training data representativeness) and the provenance (e.g. agents who perform the labeling, labeling procedure).
### Update 3
- Comment: 
>ISO 19103:2015, Geographic information — Conceptual schema language

Used only once in the document; it is probably not necessary to have it here. Listed in the bibliography is enough in my opinion.
- Proposed Change: Delete this item.
- Action: Deleted.
### Update 4
- Comment: 
>ISO 19107:2019, Geographic information — Spatial schema

Used in clause 8; I cannot say if it is mandatory to have it as a normative ref, but leave it for now; iso EM will check this.
- Proposed Change: Leave it for now.
- Action: ISO 19107-1:2014 is replaced by 19101-1:2014. The class Feature is from 19101-1:2014 and referred to in Section 8.5.1.3 by the object label.
> ISO 19101-1:2014, Geographic information — Reference model — Part 1: Fundamentals

### Update 5
- Comment: 
>ISO 19157-1, Geographic information — Data quality — Part 1: General requirements

Depending on the use you may well need the year here; it is difficult to know when to use/not use the year.
- Proposed Change: Add the year.
- Action: Added the year:
> ISO 19157-1:2023, Geographic information — Data quality — Part 1: General requirements

### Update 6
- Comment: 
>machine learning  
ML  
**is an important branch** of artificial intelligence that gives computers the ability to improve their performance without explicitly being programmed to do so. ML processes create models from training data by using a set of learning algorithms, and then can use these models to make predictions. Depending on whether the training data include labels, the learning algorithms can be divided into supervised and unsupervised learning. 

These type of qualifying or descriptive words (highlighted words) should not be used in the definition or standard.

A definition should be so long and should not contain multiple sentences. The definition should be able to "replace" the term if inserted to the document. This extra content can be formatted as Notes to entry or EXAMPLEs

Is it possible to find an ISO/IEC/IEEE definition suitable for this term?

- Proposed Change: The definition of "machine learning (ML) " could be replaced with one sourced from ISO/IEC.
- Action: Replaced with one sourced from ISO/IEC 22989:2022,3.3.5:
> machine learning  
ML  
process of optimizing model parameters through computational techniques, such that the model's behavior reflects the data or experience
Note 1 to entry: ML processes create models from training data by using a set of learning algorithms, and then can use these models to make predictions. Depending on whether the training data include labels, the learning algorithms can be divided into supervised and unsupervised learning.  
[SOURCE: ISO/IEC 22989:2022, 3.3.5, modified — Note 1 has been added]


### Update 7
- Comment: 
>training dataset  
collection of samples, often labelled in terms of supervised learning. **A training dataset can be divided into training, validation, and test sets. Training samples are different from samples in OGC Observations & Measurements (O&M). They are often collected in purposive ways that deviate from purely probability sampling, with known or expected results labelled as values of a dependent variable for generating a trained predictive model.**

A definition should be so long and should not contain multiple sentences. The definition should be able to "replace" the term if inserted to the document.
- Proposed Change: The highlighted sentences should be formatted as notes to entry or examples.
- Action: Corrected to the following sentence:
> training dataset  
collection of samples, often labelled in terms of supervised learning  
Note 1 to entry: A training dataset can be divided into training, validation, and test sets. Training samples are different from samples in ISO 19156:2023.   They are often collected in purposive ways that deviate from purely probability sampling, with known or expected results labelled as values of a dependent variable for generating a trained predictive model.


### Update 8
- Comment: 
>label  
refers to known or expected results annotated as values of a dependent variable in training samples. **A training sample label is different from those on a geographical map, which are known as map labels or annotations.** 

Because the term "label" is a common term (understood by many people outside of our geospatial/EO domains) we need use a &lt;domain&gt; to clarify which domain this definition belongs. &lt;earth observation&gt; may be one suitable domain because this type of "label" is different from a "cartographic label". I will let you and the experts decide. A list of current domains used in tc211 can be found in the quarterly terminology spreadsheet N5976; if you cannot find this, please let me know.

A definition should be so long and should not contain multiple sentences. The definition should be able to "replace" the term if inserted to the document.
- Proposed Change: Add the &lt;earth observation&gt; and the highlighted text should be transformed to a note to entry.
- Action: Corrected to the following sentence:
> label  
<earth observation> refers to known or expected results annotated as values of a dependent variable in training samples  
Note 1 to entry: A training sample label is different from those on a geographical map, which are known as map labels or annotations.

### Update 9
- Comment: 
>class  
result of a classification process as part of a classification system which subdivides concepts within a given topic area  
[SOURCE: ISO 19144-2:2023, 3.1.6]

The definition is incorrect. Be certain that you use the correctly published definitions (only from IS/TS published documents, not from DIS or FDIS). The published definitions can be found on the ISO OBP (https://www.iso.org/obp/ui/#search) or on Geolexica (https://isotc211.geolexica.org) which will be updated soon.  
- Proposed Change: Use the correct definition.
- Action: Corrected to the following sentence:
>class  
&lt;classification&gt; result of a classification process as part of a classification system which subdivides concepts within a given topic area  
[SOURCE: ISO 19144-2:2023, 3.1.6]


### Update 10
- Comment: 
>quality  
degree to which a set of inherent characteristics of an object fulfils requirements. **Quality of training data (such as data imbalance and mislabeling) can impact the performance of AI/ML models.**  
[SOURCE: ISO 9000:2015, 3.6.2, modified — Notes 1 and 2 to entry have been deleted.]

When a definition is used from another source, do not modify the definition. Here some descriptive test has been added, perhaps about how this term relates to this document but that is incorrect. You can modify the notes or examples, add new notes or examples but do not change the definition.

The text I have highlighted can easily be made into a note to entry.
- Proposed Change: The highlighted text is suitable as a note to entry.
- Action: Corrected to the following sentence:
> quality  
degree to which a set of inherent characteristics of an object fulfils requirements  
Note 1 to entry: Quality of training data (such as data imbalance and mislabeling) can impact the performance of AI/ML models.  
[SOURCE: ISO 9000:2015, 3.6.2, modified — Notes 1 and 2 to entry have been deleted, and a new Note 1 has been added]

### Update 11
- Comment: 
>scene classification   
 task of identifying scene categories of images, on the basis of a training set of images whose scene categories are known

Please consider a &lt;domain&gt; for this definition.

Sometimes it is not good to use "ing forms of verbs" in the definitions; we can change this (as I have shown) please check if that is acceptable where revised.
- Proposed Change: Add a &lt;domain&gt; for this definition. Don't use "ing forms of verbs" in the definitions.
- Action: Corrected to the following sentence:
> scene classification  
&lt;earth observation&gt; task to identify scene categories of images, on the basis of a training set of images whose scene categories are known

### Update 12
- Comment: 
>object detection  
recognition of objects from images. The objects are often localized using bounding boxes

Please search for a suitable definition in ISO/IEC/IEEE if possible.

A definition should be so long and should not contain multiple sentences. The definition should be able to "replace" the term if inserted to the document.

This text is suitable as a note to entry

Sometimes it is not good to use "ing forms of verbs" in the definitions; we can change this (as I have shown) please check if that is acceptable where revised.
- Proposed Change: Use a suitable definition in ISO/IEC/IEEE if possible.
- Action: We did not find an existing definition from ISO/IEC/IEEE standards, so we keep the original definition. And we add the domain to this definition and extracted the extra content from definitions as the Notes.
> object detection  
&lt;earth observation&gt;recognition of objects from images  
Note 1 to entry: The objects are often localized using bounding boxes.

### Update 13
- Comment: 
>semantic segmentation  
task of assigning class labels to pixels of images or points of point clouds 

Please consider a &lt;domain&gt; for this definition.

Sometimes it is not good to use "ing forms of verbs" in the definitions; we can change this (as I have shown) please check if that is acceptable where revised.
- Proposed Change: Add a &lt;domain&gt; for this definition. Don't use "ing forms of verbs" in the definitions.
- Action: Corrected to the following sentence:
> semantic segmentation    
&lt;earth observation&gt; task to assign class labels to pixels of images or points of point clouds

### Update 14
- Comment: 
>change detection  
recognition of changes in an area between images taken at different times


I am not sure if &lt;imagery&gt; is the best domain. We do not have an &lt;image processing&gt; domain. You could create that if you think more of the terms could benefit from that domain. I understand change detection is typically performed on images, would "change detection between two point clouds also be possible" but not easy... 

- Proposed Change: Perhaps could create &lt;image processing&gt; domain.
- Action: We use the &lt;earth observation&gt; for these specific tasks used in the EO domain:
> change detection  
&lt;earth observation&gt; recognition of changes in an area between images taken at different times

Do the same for definition "3D model reconstruction"
> 3D model reconstruction  
&lt;earth observation&gt; task that builds 3D objects and scenes from multi-view images 

### Update 15
- Comment: 
>generative model  
method of large model training, which improve model performance through unsupervised pre-training. In the fine-tuning phase, labelled data plays a critical role in optimizing the model for specific vertical domains or tasks. **By incorporating labelled data, the model can learn to accurately identify and extract relevant features, leading to better performance on specific downstream tasks. Overall, the combination of generative models and fine-tuning with labelled data can significantly improve the performance of large models in specialized domains or tasks.**

A definition should be so long and should not contain multiple sentences. The definition should be able to "replace" the term if inserted to the document.

- Proposed Change: The highlighted sentences should be formatted as notes to entry or examples.
- Action: Corrected to the following sentence:
>generative model  
method of large model training, which improve model performance through unsupervised pre-training  
Note 1 to entry: In the fine-tuning phase, labelled data plays a critical role in optimizing the model for specific vertical domains or tasks. By incorporating labelled data, the model can learn to accurately identify and extract relevant features, leading to better performance on specific downstream tasks. Overall, the combination of generative models and fine-tuning with labelled data can significantly improve the performance of large models in specialized domains or tasks.

### Update 16
- Comment: Perhaps clauses 4 "Conformance" and 5 "Conventions" could be flipped
- Proposed Change: Clauses 4 and 5 could be flipped.
- Action: Transpose Clauses 4 and 5.

### Update 17
- Comment: Clause 5.2 "Abbreviated terms" would be better these are in clause 4 or as clause 3.2 with term in 3.1.
- Proposed Change: Clause 5.2 "Abbreviated terms" would be better these are in clause 4 or as clause 3.2 with term in 3.1.
- Action: Clause 5.2 "Abbreviated terms" moved to Clause 3 "Terms and definitions" as Clause 3.2 "Abbreviated terms".

### Update 18
- Comment: For abbreviated terms, unless these are proper nouns they all should be lower case.
- Proposed Change: Change non-proper nouns to lower case.
- Action: Changed non-proper nouns to lower case:
>AI	&nbsp; artificial intelligence  
DL	&nbsp; deep learning  
EO	&nbsp; earth observation  
LC	&nbsp; land cover  
LU	&nbsp; land use  
ML	&nbsp; machine learning  
RS	&nbsp; remote sensing  
TD	&nbsp; training data  

### Update 19
- Comment: For the UML model, ISO/TC 211 require that it be available in Enterprise Architect version 15 or later for inclusion in the Harmonized UML Model. It is not allowed to show the same element several times in one UML diagram, such as Figure 5. The name of the abstract class should be written in Italics. It seems like you have provided the role name at the wrong end of associations. All navigable association ends shall have role names.
- Proposed Change: Transfer the model into Enterprise Architect, based on one of the existing HM copies on the HMMG GitHub: https://github.com/ISO-TC211/HMMG/tree/master/EA.
- Action: We converted the UML Model to EA based on existing HM copies, and modified the wrong Diagram. The link address of the latest file is https://github.com/opengeospatial/TrainingDML-AI_SWG/blob/main/standard/part1/UML/ISOTC211_HM_ISO19178-1.qea, and the figures in the document should be consistent with the EA file.
