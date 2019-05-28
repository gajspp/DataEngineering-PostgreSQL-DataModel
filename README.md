# Sparkify database model and ETL

The purpose of this database is to provide the analytics team at Sparkify with an easy way to query and analyse the data they've been collecting on songs and user activity on their new music streaming app. They've requested that we optimize the database for song play analysis. 

# Star schema in PostgreSQL

Star schema was chosen for this project based on the simplicity of the database and because they were looking for an easy way to query and aggreagte the data. Star schemas have the benefit of being denormalized, which improves read performance, and simplified queries with fast aggregation. Considering the data they've been collecting, the star schema will consist of 1 fact table and 4 dimension tables. Below are the descriptions of those tables:
    
### FACT Table (consists of measurements, metrics or events that actually happened)
 
**songplays** - contains a record for every song play from the log files. Only songplays with page = 'NextSong' are included

    fields: songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent
     
### DIMENSION Tables (contains data to categorize facts and measures to enable users to answer business questions)
    
**users** - users in the app. Joins to fact table using foreign key user_id.

    fields: user_id, first_name, last_name, gender, level
    
**songs** - songs in music database. Joins to fact table using foreign key song_id.

    fields: song_id, title, artist_id, year, duration
    
**artists** - artists in music database. Joins to fact table using foreign key artist_id.

    fields: artist_id, name, location, lattitude, longitude
    
**time** - timestamps of records in songplays broken down into specific units. Joins to fact table using foreign key start_time.

    fields: start_time, hour, day, week, month, year, weekday