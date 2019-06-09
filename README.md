# Data-Modeling-with-Postgres
Build a data warehouse for analytical operations. to allow Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. the analytics team is particularly interested in understanding what songs users are listening to.


#####  Purpose:	
 Build a data warehouse for analytical operations.
 
##### Benefits
 The query will be fast and simplify  

##### Schema design 
 Star schema because it's more effective for handling queries
 
# Fcat Table
  songplays:
  - records in log data associated with song plays 
# Dimension Tables
 users 
 - users in the app
 songs 
 - songs in music database
 artists
 - artists in music database
 time 
 - timestamps of records in songplays broken down into specific units

* Please see the ER Diagram.PNG file.

* Example from user data: 
 user_id	first_name	last_name	gender	level
    79	     James	      Martin	  M	     free
    78	     Chloe	      Roth     	  F    	 free
 
##### Example Query for analytic

 SELECT u.gender,count(*) FROM songplays s inner join  users u on (s.user_id=u.user_id) group by u.gender;
 
 The above query explain how many Male and Female using the application
 
 ##### Project Explanation
 there are three files:
 1-sql_queries.py contains all the sql commands for create and insert tables.
 2-create_tables.py contains create or recreate database and tables.
 3-etl.py contains python code for reads and processes files from song_data and log_data and loads them into the tables. 
 
##### Etl proces
 Python code:
 # function :
 create_database() : run the command for create database.
 
 create_tables(cur, conn) : create tables inside the connection that passed as parameters.
 
 drop_tables(cur, conn) : drop tables inside the connection that passed as parameters.
 
 process_song_file(cur, filepath) : read the json file from the file path that passed as parameter
 and insert the data ino the tables inside the connection that passed as parameter.
example  :
     cur.execute(song_table_insert, song_data) 
     
 process_log_file(cur, filepath):  read the json file from the file path that passed as parameter
 and insert the data ino the tables inside the connection that passed as parameter.
 
  process_data(cur, conn, filepath, func): reads the files path inside the directory and call the function that passed as parameter.
 
 ##### how to run:
   open the terminal and enter the below commands:
   >>python3 create_tables.py
   >>python3 etl.py
