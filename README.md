# End-to-end-spotify-data-pipeline
Building a data pipeline with Spotify API for data extraction using AWS Lambda, with automated triggers. Transform data, store files on S3, and use AWS Glue to create tables. Query data via Athena for analytics, ensuring automation and scalability.
![image](https://github.com/user-attachments/assets/dd114eaf-db9b-460f-a612-ad425068154e)

This architecture diagram illustrates the complete data pipeline for extracting, transforming, and loading Spotify data using various AWS services. The pipeline is structured into three main stages: Extract, Transform, and Load (ETL).

1. Extract:

Spotify API: Data is extracted from the Spotify API using a Python script.

AWS Lambda (Data Extraction): The Python script is deployed on AWS Lambda for automated data extraction. The script interfaces directly with the Spotify API to fetch data.
Amazon S3 (Raw Data Storage): Extracted raw data is stored in Amazon S3 buckets to ensure durability and facilitate easy access for transformation processes.
Amazon CloudWatch (Trigger): Scheduled triggers in CloudWatch initiate the data extraction process daily, ensuring up-to-date data flows into the pipeline.

2. Transform:

AWS Lambda (Data Transformation): Another AWS Lambda function is employed to transform the raw data into a more analytics-ready format. This includes data cleaning, normalization, and possibly aggregation.
Amazon S3 (Transformed Data Storage): Post-transformation, the data is stored back in S3 in a structured format, ready for loading into analytics tools.

3. Load:

AWS Glue Crawler: This component infers the schema of the transformed data stored in S3 and populates the AWS Glue Data Catalog, a metadata repository.
AWS Glue Data Catalog: Stores metadata and schema information about the transformed data, facilitating query execution and data management.
Amazon Athena: Used for running SQL queries on the transformed data stored in S3, leveraging the schema available in the Glue Data Catalog. Athena provides powerful analytics capabilities directly over S3 data.

Triggers:

S3 Object Put: Triggers the transformation function upon new data arrival in the raw data S3 bucket.
CloudWatch Event: Automatically triggers the daily data extraction function in Lambda.

This setup allows for a highly scalable, serverless, and efficient data pipeline that can handle large volumes of data with minimal management overhead, suitable for tasks such as data analytics, machine learning, and large-scale data processing.
