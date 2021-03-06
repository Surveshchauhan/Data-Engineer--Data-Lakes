# Project: Data Warehouse
## Project Overview
### Introduction
A music streaming startup, Sparkify, has grown their user base and song database and want to move their processes and data onto the cloud. Their data resides in S3, in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

As their data engineer, we are tasked with building an ETL pipeline that extracts their data from S3, stages them in Redshift, and transforms data into a set of dimensional tables for their analytics team to continue finding insights in what songs their users are listening to. 
### Project Description
In this project, we'll apply what we've learned on data warehouses and AWS to build an ETL pipeline for a database hosted on Redshift. To complete the project, we will be loading the data from S3 to staging tables on Redshift and execute SQL statements that create the analytics tables from these staging tables.
### Dataset:
#### Song Dataset
The first dataset is a subset of real data from the Million Song Dataset. Each file is in JSON format and contains metadata about a song and the artist of that song. The files are partitioned by the first three letters of each song's track ID. For example, here are filepaths to two files in this dataset.

#### Log Dataset
The second dataset consists of log files in JSON format generated by this event simulator based on the songs in the dataset above. These simulate app activity logs from a music streaming app based on specified configurations.

The log files in the dataset you'll be working with are partitioned by year and month. For example, here are filepaths to two files in this dataset.

### Schema for Song Play Analysis
Using the song and log datasets, we'll be creating a star schema optimized for queries on song play analysis. This includes the following tables.

#### Fact Table
1. **songplays** - records in log data associated with song plays i.e. records with page NextSong
(songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent)
#### Dimension Tables
2. **users** - users in the app
(user_id, first_name, last_name, gender, level)
3. **songs** - songs in music database
(song_id, title, artist_id, year, duration)
4. **artists** - artists in music database
(artist_id, name, location, lattitude, longitude)
5. **time** - timestamps of records in songplays broken down into specific units
(start_time, hour, day, week, month, year, weekday)

In addition to the data files, the project includes 7 files: description below


1. **create_table.py** is where we'll create your fact and dimension tables for the star schema in Redshift.
2. **etl.py** is where we'll load data from S3 into staging tables on Redshift and then process that data into your analytics tables on Redshift.
3. **sql_queries.py** is where we'll define you SQL statements, which will be imported into the two other files above.
4. **README.md** is where we'll provide discussion on your process and decisions for this ETL pipeline.
5. **dwh.cfg** is where we be will storing our config parameters
6. **TestQueries.ipynb/html** will be used to query the tables on redshift database to test out data lakes


### Instructions:
1. Run the following commands in the project's root directory via jupyter notebook

    - To create the database and star scheme tables for ETL pipeline that cleans data and stores in database
        `%run create_tables.py`
    - To run ETL pipeline 
        `%run etl.py`
2. Run the TestQueries.ipynb to test the results or check TestQueries.html for results
