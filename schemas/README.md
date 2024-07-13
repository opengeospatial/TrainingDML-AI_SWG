<!--
 * @Author: RuixiangLiuWHU lrx_lucky@whu.edu.cn
 * @Date: 2023-09-08 15:54:48
 * @LastEditors: RuixiangLiuWHU lrx_lucky@whu.edu.cn
 * @LastEditTime: 2024-07-13 11:34:06
 * @FilePath: \TrainingDML-AI_SWG\schemas\README.md
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
# TrainingDML-AI Schema
<font color=red>Important</font>

You SHALL make your implementations based on the 1.0 version of the schemas, which is stable.
The 1.1 version is under review for the next version of the Standards, which is not ready for the public. 
## 1. Abstract
This folder contains JSON Schema and XML Schema for TrainingDML-AI, corresponding to Part 2 - JSON Encoding Standard and Part 3 - XML Encoding Standard as specified in the TrainingDML-AI SWG. The schemas in this folder are intended for validating the correctness of your encoding cases of training datasets using TrainingDML-AI. Each class in TrainingDML-AI corresponds to a separate file, allowing you to select the schema you require for validating your encoding.
## 2. Contents
There are mainly three classes you can use to validate your encoding examples:

- AI_TrainingDataset: ai_trainingDataset.json/ai_trainingDataset.xsd
- AI_EOTrainingDataset: ai_eoTrainingDataset.json/ai_trainingDataset.xsd
- AI_TDChangeset: ai_tdChangeset.json/ai_tdChangeset.xsd

