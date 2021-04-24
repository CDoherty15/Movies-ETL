# Movies-ETL

- Here we are practicing the ETL process by gathering wikipedia film data for movies since 1990 and ratings data from the Movielens database. From here we have merged the datasets to form a larger database in SQL that holds data for over 26 million movies. 
- This was a very long process of sifting and cleaning the data, if you open the `wiki_movies.ipynb` file, it shows the different commands and functions that were ran to clean and see which datasets were needed to complete the database. From there, we were able to use this same code to create one large function to streamline this process and so that the databases in SQL can stay updated.
- As shown by the `wiki_movies.ipynb` file, this was a long and tedious process, so in order to create a larger function, we need to go step by step in order to get it right.

### Step 1: `ETL_function_test.ipynb`
- First we needed to make sure that our overall function would open the files we give it and transform it into dataframes this is done in the `extract_transform_load` function. With the given outputs, we see that the csv and json files were inputed correctly.

### Step 2: `ETL_clean_wiki_movies.ipynb`
- Next we add our `clean_movie` function to start cleaning the data. Since we are gathering world wide data, we have many foreign films, but this causes for to many extra columns. So this means we need to gather all of the original languages and group them into one column, that will list the language of the film, instead of having boolean columns for each language. 
- When inspected the column names of the wikipedia data, there are a lot of columns that contain the same data, a few are: 'Edited by' & 'Editor(s)' , 'Music by' & 'Composer(s)' , 'Release Date' & 'Release date'. 
- We also add regex strings to our `extract_transform_load` function to extract and change the data values for certain columns to make the data values easier to read. 

### Step 3: `ETL_clean_kaggle_data.ipynb`
- The kaggle data is the Movielens data that we used for ratings. We keep our `clean_movie` function and we add certain code to our `extract_transform_load` function to change the data types. Then we merge the two dataframes to create `movies_df`. 
- From here we need to create a function to fill in the missing kaggle data with the wikipedia data. Then we are able to use the `.loc` method to only take in the columns we need and then rename them to make them easier to read. Then finally, we merge `movies_df` with the `ratings.csv` file we have that is from imdb to create our final dataframe `movies_with_ratings_df`

### Step 4: `ETL_create_database.ipynb`
- Now it is the final step, to create a SQL database. We keep all the functions the same at the bottom of the `extract_transform_load` function, we add the necessary steps to upload all the data through postgress in order to create our SQL database. The import part of this step is to make sure that when new data is added to the origianl csv and json files, is that the code appends the database, instead of duplicating or deleting the original tables and reuploading it.

ETL is a long and ardious process but these are the necessary steps to take in order to get accurate and correct data.
