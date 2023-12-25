# Spotify_DATA_pipeline_snowflake_aws_py
- Set up a seamless Spotify data pipeline to Snowflake on AWS with a streamlined process, from Spotify API integration to Snowflake database storage. Leverage Jupyter Notebooks, AWS S3, Lambda functions, and Snowflake for efficient data extraction, transformation, and analysis.

## Project Architecture 
![Alt text](https://github.com/AbhishekTheCoder00/Spotify_DATA_pipeline_snowflake_aws_py/blob/main/Project%20Architecture.png)

## Technology Used

- Programming Language: Python
- Amazon Web Services Cloud Platform:
  1. Amazon S3
  2. Lambda
  3. CloudWatch
- Snowflake, Snowpipe

## Project Workflow 

### 1. Spotify Developer Account Setup
- Create a Spotify Developer account and generate `client_id` and `client_secret` on the Spotify Developer Dashboard.

### 2. Jupyter Notebook Setup
- Install the `spotipy` library using `pip install spotipy` in a Jupyter Notebook.
- Use provided credentials to fetch data via the Spotify API, convert nested JSON data to dictionaries, and structure it into `album_list`, `artist_list`, and `song_list`.
- Convert the data to CSV using `pd.to_dataframe.from_dict()` and format date.

### 3. AWS S3 Setup
- Create S3 buckets with folders for raw_data/processed and transformed_data/album_data, artist_data, songs_data.

### 4. AWS Lambda Functions
- **Data Extraction (`data_extract`):**
  - Configure environment variables for `client_id` and `client_secret` for security.
  - Utilize `boto3` to access S3 and download raw data.
  
- **Data Transformation (`data_transformation`):**
  - Establish connections between S3 and Lambda.
  - Apply transformations on `album_list`, `artist_list`, and `song_list`.
  - Convert data to CSV, drop duplicates, and format date.
  - Upload transformed data to S3 in the raw_data/processed folder.

### 5. Lambda Triggers
- Set up Lambda triggers for both data extraction and data transformation.

### 6. Snowflake Database Setup
- Create tables in Snowflake for album, artist, and song data.
- Establish external stages for S3 storage with trust relationships for security.

### 7. Snowpipe Setup
- Create three Snowpipes for individual folders (album_data, artist_data, songs_data).
- Test connections, run complete pipelines, and validate data transfer.

### 8. Power BI Analysis
- Utilize Power BI to analyze the data and extract meaningful insights.
