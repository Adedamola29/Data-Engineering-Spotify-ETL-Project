# Spotify-ETL-End-to-End-Project
## Introduction

This data pipeline aims to extract the top 100 songs from the Spotify API every hour and subsequently process and load the data into a database for querying and analysis.
## Prerequisites
+ Spotify API credentials (client ID and client secret).
+ An AWS account with appropriate permissions to create and manage Lambda functions, S3 buckets, AWS Glue, and Amazon Athena.
+ Basic familiarity with Python, AWS Lambda, AWS Glue, and Amazon Athena.
## Pipeline Overview
**Spotify API Data Extraction:** Python script retrieves the top 100 songs from the Spotify API.

**AWS Lambda for Data Loading (Raw Data):** AWS Lambda triggered by CloudWatch every hour to load raw data into an S3 bucket.

**AWS Lambda for Data Transformation:** Another Lambda triggered by CloudWatch to process raw data and organize it into subfolders.

**AWS Glue Data Catalog and ETL:** AWS Glue crawls the transformed data and loads it into a database table.

**Querying Data with Amazon Athena:** Query the data using SQL-like queries through Amazon Athena.

## Architecture
![Architecture Diagram](https://github.com/Adedamola29/Data-Engineering-End-to-End-Project/blob/main/Architecture.png)

## Dataset/API
This project contains Album,Song,and Artist data which was built using [Spotify API](https://developer.spotify.com/documentation/web-api)

## Services Used

The data pipeline utilizes several AWS services to efficiently extract, transform, and load data from the Spotify API into a database for analysis. Here's a summary of the key services used in the pipeline:

1. **Spotify API:** This external service provides access to a vast amount of music-related data, including details about songs, albums, and artists. The Python script interacts with the Spotify API to extract the top 100 songs.

2. **AWS Lambda:** Lambda is a serverless compute service that runs code in response to events. In this pipeline, Lambda functions are used to load data into an S3 bucket and transform the data into subfolders. These functions are triggered by CloudWatch Events on a scheduled basis.

3. **AWS CloudWatch:** CloudWatch is a monitoring and management service that provides insights into AWS resources and applications. It triggers the Lambda functions at specific intervals (hourly) to ensure data extraction, loading, and transformation occur regularly.

4. **Amazon S3:** Amazon Simple Storage Service (S3) is an object storage service that provides scalable storage for various types of data. In this pipeline, S3 is used to store both the raw data extracted from Spotify and the transformed data organized into subfolders.

5. **AWS Glue:** AWS Glue is an ETL (Extract, Transform, Load) service that automates the process of discovering, cataloging, and moving data between different data stores. It's used here to crawl the transformed data in S3 and catalog it in the AWS Glue Data Catalog.

6. **AWS Glue Data Catalog:** The Data Catalog is a central metadata repository that stores information about data sources, transformations, and schema. It helps maintain a consistent view of the data and facilitates querying using services like Athena.

7. **Amazon Athena:** Amazon Athena is an interactive query service that allows you to analyze data in Amazon S3 using standard SQL queries. It enables ad-hoc querying and analysis of the data stored in the Glue Data Catalog without the need for complex data transformations.

These services work together seamlessly to create an end-to-end data pipeline:

The Spotify API extraction script fetches data.
AWS Lambda functions load the data into S3 and then organize it into subfolders.
AWS Glue catalogs the transformed data.
Amazon Athena enables querying and analysis of the data without complex data transformations.
The combined power of these services simplifies the process of building, deploying, and maintaining a data pipeline, making it easier to extract insights from the collected data.

## Install packages
```
pip install pandas
pip install requets spotipy
pip install numpy
```
## Process Flow

1. Spotify API:
     - Extract Top 100 Songs (Album, Song, Artist data in JSON format)
   
   
2. AWS Lambda - Data Loading (Raw Data):
     - Triggered by CloudWatch Events (Hourly)           
   
3. Amazon S3 - Raw Data Storage:
     - Store Raw Data (Extracted JSON)

4. AWS Lambda - Data Transformation:
     - Triggered by CloudWatch Events (After Raw Data Load)         
  
5. Amazon S3 - Transformed Data Storage:
     - Organize Data into Subfolders (Album, Song, Artist)

6. AWS Glue Data Catalog:
     - Catalog Transformed Data in S3 Subfolders

7. AWS Glue ETL:
     - Transform and Load Data into Database Table

8. Amazon Athena:
     - Query Data for Analysis

9. Insights and Analysis:
     - Extract Insights from Query Results
   
10. Decision Making and Action:
      - Use Insights to Make Informed Decisions    






