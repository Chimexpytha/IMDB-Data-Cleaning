IMDB Movie Dataset Cleaning Process
Introduction
Welcome to the IMDB Movie Dataset Cleaning project! This project outlines the steps taken to clean and preprocess the IMDB movie dataset for better analysis and data quality. Data cleaning is a crucial step to ensure accuracy and reliability in any data analysis project.

Dataset
The dataset contains information about movies, including:

Title
Genre
Description
Director
Actors
Year
Runtime
Rating
Votes
Revenue
Metascore
You can find the dataset here.

Cleaning Steps
1. Handling Missing Values
Missing values were found in the 'Revenue (Millions)' and 'Metascore' columns. These were filled with the mean value of their respective columns and converted to integers.
# Handling Missing Values
revenue_mean = int(df['Revenue (Millions)'].mean())
metascore_mean = int(df['Metascore'].mean())

df['Revenue (Millions)'].fillna(revenue_mean, inplace=True)
df['Metascore'].fillna(metascore_mean, inplace=True)

df['Revenue (Millions)'] = df['Revenue (Millions)'].astype(int)
df['Metascore'] = df['Metascore'].astype(int)

Data Type Conversion
Certain columns had incorrect data types. Specifically, 'Year' and 'Runtime (Minutes)' were converted to integers, along with 'Revenue (Millions)' and 'Metascore'.
# Data Type Conversion
df['Year'] = df['Year'].astype(int)
df['Runtime (Minutes)'] = df['Runtime (Minutes)'].astype(int)

Removing Duplicates
Duplicate rows can skew analysis results. I checked for duplicates and found none.

4. Trimming Whitespace
Whitespace in string fields can cause issues during analysis. Leading and trailing whitespace were trimmed from relevant columns.

# Trimming Whitespace
df['Title'] = df['Title'].str.strip()
df['Genre'] = df['Genre'].str.strip()
df['Description'] = df['Description'].str.strip()
df['Director'] = df['Director'].str.strip()
df['Actors'] = df['Actors'].str.strip()

Splitting Genres
The 'Genre' column contained multiple genres in a single string. This column was split into a list of genres for each movie.

# Splitting Genres
df['Genre'] = df['Genre'].apply(lambda x: x.split(',') if isinstance(x, str) else x)

Final Data Overview
After cleaning, the dataset is now free of missing values, has correct data types, no duplicates, trimmed whitespace, and split genres. The cleaned dataset is ready for analysis.

Conclusion
The data cleaning process involved:

Handling missing values
Converting data types
Removing duplicates
Trimming whitespace
Splitting genres
These steps are crucial for ensuring data quality and reliability in any analysis. The cleaned dataset can now be used for insightful data analysis and visualization.

Thank you!

Author
Chimezie Nnabuihe
