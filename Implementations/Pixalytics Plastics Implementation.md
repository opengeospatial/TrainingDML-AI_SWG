# Pixalytics Plastics Detection Dataset Implementation

The implementation is based on work undertaken as part of the OGC Testbed activities, where [Python code](https://github.com/opengeospatial/T17-API-D168) was developed to catalog a Machine Learning dataset that has been extended to use [PyTDML](https://github.com/TrainingDML/pytdml) to store the metadata in the TrainingDML-AI format. 

The underlying Training Dataset (TDS) was generated as part of an ESA funded research, and published by [Lavender (2022)](https://doi.org/10.3390/rs14194772), and a small subset of this TDS is deployed as the Copernicus Sentinel-2 RGB colour composite and labelled image (both GeoTiFFs). For the full TDS, there is another file - the multi-layer input to the Neural Net that is constructed from both Sentinel-2 and Sentinel-1 data as described in Lavender (2022).

## Demo deployment

- Catalog Metadata file for a subset of the Pixalytics Plastics Detection Training Dataset stored on an AWS S3 bucket: https://pixalytics-ogc-api.s3.eu-west-2.amazonaws.com/TrainingDML-AI/output/tds-catalog-pytdml-v0-9/tds-catalog.gson

Process used to generate the Catalog Metadata:

- Install the code in the [Tesbed Python code repository](https://github.com/opengeospatial/T17-API-D168)
- The input data is stored in the same S3 bucket as output: s3://pixalytics-ogc-api/TrainingDML-AI/input/
- Activated the associated conda repository: `conda activate ogcapi`
- Ran the following command: ` create_catalog.py --tds --s3`

  - The tds option is to create the output catalog in the TrainingDML-AI format
  - The s3 option is the option to store the TDS in an Amazon Simple Storage Service (Amazon S3) bucket specified in the associated [yaml file](https://github.com/opengeospatial/T17-API-D168/blob/main/build_catalog/configuration-tds-pytdml-s3.yaml). **Note:** This S3 bucket is publicly readable, but not writable.