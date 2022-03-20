# Movies-ETL
![etl-process-explained-diagram](https://user-images.githubusercontent.com/89308251/159180166-2d3c9706-1d52-490c-b794-4e6386e7cbbc.png)


## Challenge Overview

### Purpose:

The purpose of this analysis is to use the Extract, Transform, Load (ETL) process to create data pipelines that takes in new data, performs the appropriate transformations, and loads the cleaned dataset into a SQL database.
   

### Resources:
- Software: 
    - Jupyter Notebooks 6.4.3
       - Python 3.8.8 
    - pgAdmin 4
- Data sources:  
    - Movies on [Wikipedia](https://en.wikipedia.org/wiki/Lists_of_films) from 1990 to 2018
      - wikipedia-movies.json
    - [Kaggle](https://www.kaggle.com/rounakbanik/the-movies-dataset) 
      - [movies_metadata.csv](https://github.com/SYDsCorner/Movies-ETL/blob/main/Resources/movies_metadata.csv) 
      - [ratings.csv](https://www.kaggle.com/rounakbanik/the-movies-dataset?select=ratings.csv)

  
## The ETL Process (Extract, Transform, Load)

#### 1. Extract:  _Gathering data from one or multiple sources_ 

- the Wikipedia Movies data stored as a JSON 
    > Movies on Wikipedia from 1990 to 2018
- the Kaggle Data stored in CSVs 
    > The [Kaggle](https://www.kaggle.com/rounakbanik/the-movies-dataset) dataset pulls from [MovieLens](https://grouplens.org/datasets/movielens/) website run by the GroupLens       research group at the University of Minnesota which is the dataset of over 20 million reviews that contains a metadata file with details about the movies from 
      [the Movie Database (TMDb)](https://www.themoviedb.org/) and also contains ratings data file which will use for this challenges.


#### 2. Transform: _the transformation step is used to clean up your data_
  - Create a Function to Clean the Data: that takes in the argument "movie"
  - Create another function that takes in three arguments: Wikipedia data, Kaggle metadata, and MovieLens rating data
    - Read in the three data files
    - Filter out TV shows
    - Iterate through the clean_movie function
    - Use 'try-except' block to catch errors and drop any 'imdb_id' duplicate rows


    - Clean Individual Datasets
      - Clean the Wikipedia Movies data
        - Parse the Box Office Data 
        - Parse Budget Data 
        - Parse Release Date 
        - Parse Running Time 
      - Clean the Kaggle Data
        - Keep rows where the adult column is False
        - Convert Data Types
      - Clean the Ratings Data
        - Convert the timestamp to a datetime data type

- Merge Datasets
    - Merge the Wikipedia and the Kaggle Metadata into the movies DataFrame
      - Drop unnecessary columns
      - Fill in the missing data
      - Filter and Rename the movies DataFrame for specific columns
    - Transform and Merge Rating Data

#### 3. Load: _Load tranformed data into its final destination_ 
- Connect Pandas and SQL: _using Pandas to_sql method paired with sqlAlchemy_
 	- Add the 'movies_df' DataFrame to a SQL database
 	- Add MovieLens rating CSV data to a SQL database


 
