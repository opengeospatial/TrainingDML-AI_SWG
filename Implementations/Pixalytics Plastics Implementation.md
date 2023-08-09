# Pixalytics Plastics Detection Dataset Implementation

The implementation is based on work undertaken as part of the OGC Testbed activities, where [Python code](https://github.com/opengeospatial/T17-API-D168) was developed to catalog a Machine Learning dataset that has been extended to use [PyTDML](https://github.com/TrainingDML/pytdml) to store the metadata in the TrainingDML-AI format. 

The underlying Training Dataset was generated as part of an ESA funded research, and was published by [Lavender (2022)](https://doi.org/10.3390/rs14194772).

## Demo deployment

- Catalog Metadata file for a subset of the Pixalytics Plastics Detection Training Dataset stored on an AWS S3 bucket: https://pixalytics-ogc-api.s3.eu-west-2.amazonaws.com/TrainingDML-AI/output/tds-catalog-pytdml-v0-9/tds-catalog.gson

Process used to generate the Catalog Metadata:

- Install the code in the [Tesbed Python code repository](https://github.com/opengeospatial/T17-API-D168)
- The input data is stored in the same S3 bucket as output: s3://pixalytics-ogc-api/TrainingDML-AI/input/
- Activated the associated conda repository: `conda activate ogcapi`
- Ran the following command: ` create_catalog.py --tds --s3`

  - The tds option is to create the output catalog in the TrainingDML-AI format
  - The s3 option is to store it in a specified S3 bucket (specified in the associated yaml file, specified in the code as ``). **Note:** This S3 bucket is publicly accessible, but not writable