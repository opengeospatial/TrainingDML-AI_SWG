# TrainingDML-AI STAC Extension Implementation

[TrainingDML-AI STAC Extension](https://github.com/openrsgis/trainingdml-ai-extension) is designed as an extension to the SpatioTemporal Asset Catalog (STAC) specification. It builds upon the STAC specification and specifically addresses the requirements for geospatial machine learning training data and introduces additional fields and metadata concepts to formalize the information model of training data within the STAC framework.The extension expands upon the core STAC specification to accommodate the specific needs of training data, enabling interoperability and facilitating effective management and utilization of geospatial machine learning training datasets within the STAC ecosystem.

# TrainingDML-AI Extension Specification

- **Title:** TrainingDML-AI
- **Identifier:** <https://stac-extensions.github.io/trainingdml-ai/v1.0.0/schema.json>
- **Field Name Prefix:** tdml
- **Scope:** Item, Collection
- **Extension [Maturity Classification](https://github.com/radiantearth/stac-spec/tree/master/extensions/README.md#extension-maturity):** Proposal
- **Owner**: @TrainingDML

This document explains the fields of The Training Data Markup Language for Artificial Intelligence (TrainingDML-AI)  Extension to the [SpatioTemporal Asset Catalog](https://github.com/radiantearth/stac-spec) (STAC) specification. Training data plays a fundamental role in Earth Observation (EO) Artificial Intelligence Machine Learning (AI/ML), especially Deep Learning (DL). The TrainingDML-AI Extension provides detailed metadata for formalizing the information model of geospatial machine learning training data. This includes but is not limited to the following aspects: 

·    How the training data is prepared, such as provenance or quality;

·    How to specify different metadata used for different ML tasks such as scene/object/pixel levels; 

·    How to differentiate the high-level training data information model and extended information models specific to various ML applications; 

·    How to introduce external classification schemes and flexible means for representing ground truth labeling.

- Examples:
  
  - Dota-v1.5 Dataset:
    
    - [Item 1 example-Dota-v1.5 Dataset](examples/DOTA-1.5_Dataset/dota_1.5_trainingdata_0000.json): Shows the basic usage of the extension in a STAC Item
    - [Item 2 example-Dota-v1.5 Dataset](examples/DOTA-1.5_Dataset/dota_1.5_trainingdata_1228.json): Shows the basic usage of the extension in a STAC Item
    - [Collection example-Dota-v1.5 Dataset](examples/DOTA-1.5_Dataset/collection.json): Shows the basic usage of the extension in a STAC Collection
  
  - WHU building Dataset:
    
    - [Item example-WHU building Dataset](examples/WHU-building_Dataset/item.json): Shows the basic usage of the extension in a STAC Item
    - [Collection example-WHU building Dataset](examples/WHU-building_Dataset/collection.json): Shows the basic usage of the extension in a STAC Collection

- [JSON Schema](json-schema/schema.json)

- [Changelog](./CHANGELOG.md)

## Collection Fields

The fields in the table below can be used in these parts of STAC documents:

- [ ] Catalogs
- [x] Collections
- [ ] Item Properties (incl. Summaries in Collections)
- [ ] Assets (for both Collections and Items, incl. Item Asset Definitions in Collections)
- [ ] Links

| Field Name                   | Type                                                                                 | Description                                                                                   |
| ---------------------------- | ------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------- |
| tdml:amount_of_training_data | number                                                                               | **Required**, Total  number of training samples in the AI training dataset.                   |
| tdml:classification_schema   | string                                                                               | Classification schema for classes used in the AI  training dataset.                           |
| tdml:metrics_in_LIT          | [[MetricsInLIT Object](#metricsInLIT-Object)]                                        | Results of performance metrics achieved by AI/ML algorithms in the peer-reviewed  literature. |
| tdml:image_sizes             | [number]                                                                             | Size of the images used in the EO training dataset.                                           |
| tdml:scope                   | [Scope Object](https://github.com/openrsgis/trainingdml-ai-extension#Scope-Object) | Description  of the scope of the training dataset.                                            |
| tdml:quality                 | [Quality Object](#Quality-Object)                                                    | Quality description of training datasets.                                                     |
| tdml:provenance              | [provenance Object](#Provenance-Object)                                              | Provenance information of the training data and training dataset.                             |
| tdml:data_sources            | [string]                                                                             | Citation of data sources.                                                                     |

In addition, fields from the following extensions must be imported in the item:

- the [Label Extension Specification](https://github.com/stac-extensions/label) to describe properties of a training dataset.
- the [Scientific Citation Extension](https://github.com/stac-extensions/scientific) to describe DOI of a training dataset.
- the [Electro-Optical Extension](https://github.com/stac-extensions/eo) to describe bands of a training dataset.

## Item Fields

The fields in the table below can be used in these parts of STAC documents:

- [ ] Catalogs
- [ ] Collections
- [x] Item Properties (incl. Summaries in Collections)
- [ ] Assets (for both Collections and Items, incl. Item Asset Definitions in Collections)
- [ ] Links

| Field Name        | Type                                                                                     | Description                                                       |
| ----------------- | ---------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| tdml:quality      | [Quality Object](https://github.com/openrsgis/trainingdml-ai-extension#Quality-Object) | Quality description of training datasets.                         |
| tdml:provenance   | [Provenance Object](#Provenance-Object)                                                  | Provenance information of the training data and training dataset. |
| tdml:data_sources | [string]                                                                                 | Citation of data sources.                                         |

In addition, fields from the following extensions must be imported in the item:

- the [Label Extension Specification](https://github.com/stac-extensions/label) to describe label properties of a training instance.
- the [ML AOI Extension Specification](https://github.com/stac-extensions/ml-aoi) to describe training type of a training instance.

### Additional Field Information

#### tdml:amount_of_training_data

Total number of training samples in the AI training dataset.

#### tdml:classification_schema

 Time when the AI training dataset was created. 

#### tdml:metrics_in_LIT

Results of performance metrics achieved by AI/ML algorithms in the peer-reviewed  literature.  

#### tdml:image_sizes

Size of the images used in the EO training dataset.  The imageSize  is recommended to be expressed in the form of "width\*height". If the imageSize of the training data in dataset is not the same, you can use the imageSize of Smallest size image and the imageSize of largest image to express, such as "minWidth\**minHeight~maxWidth*\*maxHeight".

#### tdml:scope

Description  of the scope of the training dataset.  

#### tdml:quality

Quality description of training datasets. Quality will be aligned with the DQ_DataQuality class in the ISO 19157:2013 spatial data quality model, and the quality assessment metrics for the sample dataset are described using the quality metric classes defined in ISO 19157:2013.

#### tdml:provenance

provenance includes the labeler and the labeling procedure, which can be mapped to the agent and activity respectively in [W3C PROV](https://www.w3.org/TR/prov-overview/) model. The labeler identifies the agent that creates the training dataset or individual samples, and the labeling procedure represents the process for data generation.

#### tdml:data_sources

Citation of data sources.  

### MetricsInLIT Object

This is the introduction for the purpose and the content of the metricsInLIT Object used in field: tdml:metricsInLIT.

| Field Name | Type   | Description                                                                            |
| ---------- | ------ | -------------------------------------------------------------------------------------- |
| doi        | string | **REQUIRED**. Digital object identifier of the peer-reviewed literature.               |
| algorithm  | string | AI/ML algorithms used in the peer-reviewed literature.                                 |
| metrics    | object | **REQUIRED**. Metrics and results of AI/ML algorithms in the peer-reviewed literature. |

An example of yolov5's MetricsInLIT on the DOTA-v1.5 dataset:

```json
{
    "doi":"10.5281/zenodo.3983579",
    "algotithm": "YOLOV5",
    "metrics":[
        {
            "name": "AP50",
            "value": "66.1"
        },
        {
            "name": "AP50:95",
            "value": "41.5"
        },
        {
            "name": "AR1",
            "value": "39.4"
        },
        {
            "name": "AR10",
            "value": "54.9"
        },
        {
            "name": "AR100",
            "value": "58.4"
        }
    ]
}
```

### Quality Object

This is the introduction for the purpose and the content of the Quality Object used in filed: tdml:quality.

| Field Name | Type                                               | Description                                                  |
| ---------- | -------------------------------------------------- | ------------------------------------------------------------ |
| scope      | \[[Scope Object](#Scope-Object)]                   | **REQUIRED**. the scope of quality information is specified. |
| report     | \[[QualityElement Object](#QualityElement-Object)] | Quality reports about the training dataset.                  |

### Provenance Object

This is the introduction for the purpose and the content of the Provenance Object used in filed: tdml:provenance.

| Field Name       | Type                             | Description                                                   |
| ---------------- | -------------------------------- | ------------------------------------------------------------- |
| scope            | \[[Scope Object](#Scope-Object)] | **REQUIRED**. the scope of labeling information is specified. |
| labeling_methods | [string]                         | Methods used in the labeling procedure.                       |
| labeling_tools   | [string]                         | Tools or software used in the labeling procedure.             |
| labeler_names    | [string]                         | Name of the labeler.                                          |

### Scope Object

| Field Name        | Type   | Description                                                                                                       |
| ----------------- | ------ | ----------------------------------------------------------------------------------------------------------------- |
| level             | string | **REQUIRED**. The applicable level of data.                                                                       |
| level_description | object | **REQUIRED**. A more detailed description of the level to better understand the scope of application of the data. |

### QualityElement Object

This is the introduction for the purpose and the content of the qualityElement. Elements related to quality, or more specifically, bias that can be used to reduce the errors when using AI/ML. For example, any knowledge of the TD imbalance and mislabeling can be stored in TD quality.

| Field Name        | Type   | Description                                           |
| ----------------- | ------ | ----------------------------------------------------- |
| type              | string | **REQUIRED**. Type of evaluation quality.             |
| measure           | string | **REQUIRED**. Reference to measure used.              |
| evaluation_method | string | **REQUIRED**. Evaluation information.                 |
| result            | string | Value obtained from applying a data quality measure.. |

## Relation types

It is highly recommended to use the `version-history` as a rel type in the  [Link Object](https://github.com/radiantearth/stac-spec/tree/master/item-spec/item-spec.md#link-object) to record the changed training samples between two versions at the collection level as a changeset. The changeset is used to track updates made to a specific version of a sample dataset, identified by its "datasetId" and "version".

There are three types of updates for sample data units: "add" for adding new sample data units, "modify" for modifying existing sample data units, and "delete" for removing sample data units. "Modify" includes changes to metadata of sample data, changes to original data used in sample data, and additions, modifications, and deletions of all labeled objects in the sample data.

## Best Practices

### Core and other extensions fields

It is higly recommended to use the following fields to describe the training dataset:

| Field name                                                                                                            | TrainingDML-AI usage                                            |
| --------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------- |
| [providers](https://github.com/radiantearth/stac-spec/blob/master/collection-spec/collection-spec.md#provider-object) | People or organizations who provide the AI training dataset.    |
| [label: overviews](https://github.com/stac-extensions/label/blob/main/README.md#label-overview-object)                | Statistics results of training samples in each class.           |
| [label: classes](https://github.com/stac-extensions/label/blob/main/README.md#class-object)                           | **REQUIRED**. Classes used in the AI training dataset.          |
| [label: tasks](https://github.com/stac-extensions/label/blob/main/README.md#item-properties)                          | **REQUIRED**. Type description of the EO task.                  |
| [label: methods](https://github.com/stac-extensions/label/blob/main/README.md#item-properties)                        | Methods used in the labeling procedure.                         |
| [ml-aoi: split](https://github.com/stac-extensions/ml-aoi#item-properties-and-collection-fields)                      | Training type of the individual AI.                             |
| [eo: bands](https://github.com/stac-extensions/eo#band-object)                                                        | Description of the image bands used in the EO training dataset. |
| [sci:doi](https://github.com/stac-extensions/scientific#item-properties-and-collection-fields)                        | Digital object identifier of the AI training dataset.           |

## Contributing

All contributions are subject to the
[STAC Specification Code of Conduct](https://github.com/radiantearth/stac-spec/blob/master/CODE_OF_CONDUCT.md).
For contributions, please follow the
[STAC specification contributing guide](https://github.com/radiantearth/stac-spec/blob/master/CONTRIBUTING.md) Instructions
for running tests are copied here for convenience.

### Running tests

The same checks that run as checks on PR's are part of the repository and can be run locally to verify that changes are valid. 
To run tests locally, you'll need `npm`, which is a standard part of any [node.js installation](https://nodejs.org/en/download/).

First you'll need to install everything with npm once. Just navigate to the root of this repository and on 
your command line run:

```bash
npm install
```

Then to check markdown formatting and test the examples against the JSON schema, you can run:

```bash
npm test
```

This will spit out the same texts that you see online, and you can then go and fix your markdown or examples.

If the tests reveal formatting problems with the examples, you can fix them with:

```bash
npm run format-examples
```
