#excersie 1 
```# Exercise 1. - Getting and Knowing your Data
This time we are going to pull data directly from the internet.
Special thanks to: https://github.com/justmarkham for sharing the dataset and materials.

Check out [Occupation Exercises Video Tutorial](https://www.youtube.com/watch?v=W8AB5s-L3Rw&list=PLgJhDSE2ZLxaY_DigHeiIDC1cD09rXgJv&index=4) to watch a data scientist go through the exercises

### Step 1. Import the necessary libraries
import pandas as pd
### Step 2. Import the dataset from this [address](https://raw.githubusercontent.com/justmarkham/DAT8/master/data/u.user). 
url = 'https://raw.githubusercontent.com/justmarkham/DAT8/master/data/u.user'
df = pd.read_csv(url, sep='|')
### Step 3. Assign it to a variable called users and use the 'user_id' as index
users = df
users.set_index('user_id', inplace=True)
### Step 4. See the first 25 entries
users.head(25)
### Step 5. See the last 10 entries
users.tail(10)
### Step 6. What is the number of observations in the dataset?
users.shape[0]
### Step 7. What is the number of columns in the dataset?
users.shape[1]
### Step 8. Print the name of all the columns.
users.columns
### Step 9. How is the dataset indexed?
users.index
### Step 10. What is the data type of each column?
users.dtypes
### Step 11. Print only the occupation column
users.occupation.head()
### Step 12. How many different occupations are in this dataset?
users.occupation.nunique()
### Step 13. What is the most frequent occupation?
users.occupation.value_counts()
### Step 14. Summarize the DataFrame.
users.describe(include='all')
### Step 15. Summarize all the columns
users.describe()
### Step 16. Summarize only the occupation column
users['occupation'].describe()
### Step 17. What is the mean age of users?
users['age'].mean()
### Step 18. What is the age with least occurrence?
users['age'].value_counts().idxmin()
```

#excersise 2

```# Exercise 2. - Filtering and Sorting Data

Check out [Euro 12 Exercises Video Tutorial](https://youtu.be/iqk5d48Qisg) to watch a data scientist go through the exercises
This time we are going to pull data directly from the internet.

### Step 1. Import the necessary libraries
import pandas as pd
### Step 2. Import the dataset from this [address](https://raw.githubusercontent.com/kflisikowsky/pandas_exercises/refs/heads/main/Euro_2012_stats_TEAM.csv). 
url = 'https://raw.githubusercontent.com/kflisikowsky/pandas_exercises/refs/heads/main/Euro_2012_stats_TEAM.csv'
df = pd.read_csv(url)

### Step 3. Assign it to a variable called euro12.
euro12 = df
euro12
### Step 4. Select only the Goal column.
euro12.Goals
### Step 5. How many team participated in the Euro2012?
euro12.Team.count()
### Step 6. What is the number of columns in the dataset?
euro12.shape
len(euro12.columns)
### Step 7. View only the columns Team, Yellow Cards and Red Cards and assign them to a dataframe called discipline
discipline = euro12[['Team', 'Yellow Cards', 'Red Cards']]
discipline
### Step 8. Sort the teams by Red Cards, then to Yellow Cards
discipline.sort_values(['Red Cards', 'Yellow Cards'])
### Step 9. Calculate the mean Yellow Cards given per Team
discipline['Yellow Cards'].mean()
### Step 10. Filter teams that scored more than 6 goals
euro12[euro12['Goals'] > 6]['Team']
### Step 11. Select the teams that start with G
euro12[euro12.Team.str.startswith('G')]
### Step 12. Select the first 7 columns
euro12.iloc[:, :7]
### Step 13. Select all columns except the last 3.
euro12.iloc[:, :-3]
### Step 14. Present only the Shooting Accuracy from England, Italy and Russia
euro12.set_index('Team', inplace=True)
euro12.loc[['England','Italy', 'Russia'], 'Shooting Accuracy']
```
#excersise 3
```# Exercise 3. - GroupBy
### Introduction:

GroupBy can be summarized as Split-Apply-Combine.

Special thanks to: https://github.com/justmarkham for sharing the dataset and materials.

Check out this [Diagram](http://i.imgur.com/yjNkiwL.png)  

Check out [Alcohol Consumption Exercises Video Tutorial](https://youtu.be/az67CMdmS6s) to watch a data scientist go through the exercises


### Step 1. Import the necessary libraries
import pandas as pd
### Step 2. Import the dataset from this [address](https://raw.githubusercontent.com/justmarkham/DAT8/master/data/drinks.csv). 
url ='https://raw.githubusercontent.com/justmarkham/DAT8/master/data/drinks.csv'

df = pd.read_csv(url)
### Step 3. Assign it to a variable called drinks.
drinks = df
### Step 4. Which continent drinks more beer on average?
drinks.groupby('continent')['beer_servings'].mean()
### Step 5. For each continent print the statistics for wine consumption.
gb = drinks.groupby('continent').agg({
    'wine_servings' : 'describe'
})
gb
### Step 6. Print the mean alcohol consumption per continent for every column
gb = drinks.groupby('continent').mean(numeric_only=True)
gb
### Step 7. Print the median alcohol consumption per continent for every column
gb = drinks.groupby('continent').median(numeric_only=True)
gb
### Step 8. Print the mean, min and max values for spirit consumption.
#### This time output a DataFrame
drinks.groupby('continent').spirit_servings.agg(['mean', 'min', 'max'])```


#data vizualization
## **Cleaning Data in Python live training**


Welcome to this live, hands-on training where you will learn how to effectively diagnose and treat missing data in Python.

The majority of data science work often revolves around pre-processing data, and making sure it's ready for analysis. In this session, we will be covering how transform our raw data into accurate insights. In this notebook, you will learn:

* Import data into `pandas`, and use simple functions to diagnose problems in our data.
* Visualize missing and out of range data using `missingno` and `seaborn`.
* Apply a range of data cleaning tasks that will ensure the delivery of accurate insights.

## **The Dataset**

The dataset to be used in this webinar is a CSV file named `airbnb.csv`, which contains data on airbnb listings in the state of New York. It contains the following columns:

- `listing_id`: The unique identifier for a listing
- `description`: The description used on the listing
- `host_id`: Unique identifier for a host
- `host_name`: Name of host
- `neighbourhood_full`: Name of boroughs and neighbourhoods
- `coordinates`: Coordinates of listing _(latitude, longitude)_
- `Listing added`: Date of added listing
- `room_type`: Type of room
- `rating`: Rating from 0 to 5.
- `price`: Price per night for listing
- `number_of_reviews`: Amount of reviews received
- `last_review`: Date of last review
- `reviews_per_month`: Number of reviews per month
- `availability_365`: Number of days available per year
- `Number of stays`: Total number of stays thus far

## **Getting started**
# Import libraries
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
import seaborn as sns
import missingno as msno
import datetime as dt
# Read in the dataset
airbnb = pd.read_csv('https://raw.githubusercontent.com/kflisikowsky/Descriptive_Statistics/refs/heads/main/data/airbnb.csv', index_col = 'Unnamed: 0')
## **Diagnosing data cleaning problems using simple `pandas` and visualizations**
Some important and common methods needed to get a better understanding of DataFrames and diagnose potential data problems are the following:

- `.head()` prints the header of a DataFrame
- `.dtypes` prints datatypes of all columns in a DataFrame
- `.info()` provides a bird's eye view of column data types and missing values in a DataFrame
- `.describe()` returns a distribution of numeric columns in your DataFrame
- `.isna().sum()` allows us to break down the number of missing values per column in our DataFrame
- `.unique()` finds the number of unique values in a DataFrame column

<br>

- `sns.histplot()` plots the distribution of one column in your DataFrame.
# Print the header of the DataFrame
airbnb.head()
By merely looking at the data, we can already diagnose a range of potential problems down the line such as:

<br>

_Data type problems:_

- **Problem 1**: We can see that the `coordinates` column is probably a string (`str`) - most mapping functions require a latitude input, and longitude input, so it's best to split this column into two and convert the values to `float`.
- **Problem 2**: Similar to `coordinates` - the `price` column also is a string with `$` attached to each price point, we need to convert that to `float` if we want a good understanding of the dataset.
- **Problem 3**: We need to make sure date columns (`last_review` and `listing_added`) are in `datetime` to allow easier manipulation of data data.

<br>

_Missing data problems:_

- **Problem 4**: We can see that there are missing data in some columns, we'll get a better bird's eye view of that down the line.

<br>

_Text/categorical data problems:_


- **Problem 5**: To be able to visualize number of listings by boroughs - we need to separate neighborhoud name from borough name in `neighbourhood_full` column.
- **Problem 6**: Looking at `room_type`, let's replace those values to make them `'Shared Room'`, `'Private Home/Apartment'`, `'Private Room'` and `'Hotel Room'`.
# Print data types of DataFrame
airbnb.dtypes
Printing the data types confirms that `coordinates` and `price` need to be converted to `float`, and date columns need to be converted to `datetime` _(**problems 1,2 3)**_
# Print info of DataFrame
airbnb.info()
Printing the info confirms our hunch about the following:

- There is missing data in the `price`, `last_review`, `reviews_per_month`, `rating`, `number_of_stays`, `5_stars` columns. It also seems that the missingness of `last_review`, `reviews_per_month`, `rating`, `number_of_stays`, `5_stars` are related since they have the same amount of missing data. We will confirm later with `missingno` _(**problem 4**)_.
# Print number of missing values
airbnb.isna().sum()
There are a variety of ways of dealing with missing data that is dependent on type of missingness, as well as the business assumptions behind our data - our options could be:

- Dropping missing data (if the data dropped does not impact or skew our data)
- Setting to missing and impute with statistical measures (median, mean, mode ...)
- Imputing with more complex algorithmic/machine learning based approaches
- Impute based on business assumptions of our data
# Print description of DataFrame
airbnb.describe()


- **Problem 7:** Looking at the maximum of the `rating` column - we see that it is out of range of `5` which is the maximum rating possible. We need to make sure we fix the range this column.

It's worth noting that `.describe()` does not offer a bird's eye view of all the out of range data we have, for example, what if we have date data in the future? Or given our dataset, `listing_added` dates that are in the future of `last_review` dates?
# Visualize the distribution of the rating column
sns.histplot(airbnb['rating'], kde=True, bins = 20)
plt.title('Distribution of listing ratings')
plt.show()
# Find number of unique values in room_type column
airbnb['room_type'].unique()
- **Problem 8**: There are trailing spaces and capitalization issues with `room_type`, we need to fix this problem.
# How many values of different room_types do we have?
airbnb['room_type'].value_counts()
airbnb['price'].head(5)
## **Our to do list:** 
 
_Data type problems:_   

- **Task 1**: Split `coordinates` into 2 columns and convert them to `float`
- **Task 2**: Remove `$` from `price` and convert it to `float`
- **Task 3**: Convert `listing_added` and `last_review` to `datetime`

<br>

_Text/categorical data problems:_

- **Task 4**: We need to collapse `room_type` into correct categories
- **Task 5**: Divide `neighbourhood_full` into 2 columns and making sure they are clean

<br>

_Data range problems:_

- **Task 6**: Make sure we set the correct maximum for `rating` column out of range values

<br>

_Dealing with missing data:_

- **Task 7**: Understand the type of missingness, and deal with the missing data in most of the remaining columns.

<br>

_Is that all though?_

- We need to investigate if we duplicates in our data
- We need to make sure that data makes sense by applying some sanity checks on our DataFrame
## **Q&A**
## **Cleaning data**
### Data type problems
# Reminder of the DataFrame
airbnb.head()
##### **Task 1:** Replace `coordinates` with `latitude` and `longitude` columns
To perform this task, we will use the following methods:

- `.str.replace("","")` replaces one string in each row of a column with another
- `.str.split("")` takes in a string and lets you split a column into two based on that string
- `.astype()` lets you convert a column from one type to another
airbnb.columns
airbnb[['latitude', 'longitude']] = (
    airbnb['coordinates']
    .str.replace('(', '', regex=False)
    .str.replace(')', '', regex=False)
    .str.split(', ', expand=True)
)

airbnb['latitude'] = airbnb['latitude'].astype(float)
airbnb['longitude'] = airbnb['longitude'].astype(float)

airbnb = airbnb.drop(columns='coordinates')

airbnb.head()
##### **Task 2:** Remove `$` from `price` and convert it to `float`
To perform this task, we will be using the following methods:

- `.str.strip()` which removes a specified string from each row in a column
- `.astype()`
airbnb["price"] = (
    airbnb["price"]
    .astype(str)
    .str.replace("$", "", regex=False)
    .str.replace(",", "", regex=False)
)

airbnb["price"] = pd.to_numeric(airbnb["price"], errors="coerce")
# Calculate mean of price without conversion

airbnb['price'].mean()
# Remove $ from price before conversion to float
airbnb['price'] = airbnb['price'].str.strip("$")
# Print header to make sure change was done
airbnb['price'].head()
# Convert price to float
airbnb['price'] = airbnb['price'].astype('float')
# Calculate mean of price after conversion
avg = airbnb['price'].mean()
airbnb['price'] = airbnb['price'].fillna(avg)
#vizualization distribution of prices

airbnb['logprice'] =np.log(airbnb['price'])
sns.histplot(airbnb['logprice'], kde=True, bins=20)
plt.show()
import plotly.express as px
airbnb['price_cat'] = pd.cut(
    airbnb['price'], 
    bins=[0, 100, 200, 300, 400, 500, 600, 1000, 2000, 5000, 8000],
    labels=['0-100', '100-200', '200-300', '300-400', '400-500', '500-600', '600-1000', '1000-2000', '2000-5000', '5000-8000']
)

#pd.crosstab(index=airbnb['price_cat'], columns='count')

pd.crosstab(index=airbnb['price_cat'], columns=airbnb['room_type'])

#sns.countplot(airbnb, y="price_cat", hue="room_type");

ct = airbnb.groupby(['room_type', 'price_cat']).size().reset_index(name='count')

fig = px.bar(ct, x="room_type", y="count", color="price_cat", barmode="stack")
fig.show()
#plotly express <- website  

#freq_table= airbnb['price_cat'].value_counts().sort_index().reset_index()
#freq_table.columns =['price_range', 'frequency']
#freq_table

#print(airbnb['price_cat'].unique())  

print(airbnb['price_cat'].isna().sum())
print(airbnb['price'].describe())
ct = pd.crosstab(airbnb['price_cat'], airbnb['room_type'])

ax = ct.plot(kind='bar', stacked=True, figsize=(10, 6))

ax.set_title('Price Category by Room Type')
ax.set_xlabel('Price Range ($)')
ax.set_ylabel('Frequency')
ax.legend(loc='upper right')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
##### **Task 3:** Convert `listing_added` and `last_review` columns to `datetime`
To perform this task, we will use the following functions:

- `pd.to_datetime(format = "")`
  - `format` takes in the desired date format `"%Y-%m-%d"`
# Print header of two columns
airbnb[['listing_added', 'last_review']].head()

### Text and categorical data problems
##### **Task 4:** We need to collapse `room_type` into correct categories
To perform this task, we will be using the following methods:

- `.str.lower()` to lowercase all rows in a string column
- `.str.strip()` to remove all white spaces of each row in a string column
- `.replace()` to replace values in a column with another
# Print unique values of `room_type`
airbnb['room_type'].unique()
# Deal with capitalized values
airbnb['room_type'] = airbnb['room_type'].str.lower()
airbnb['room_type'].unique()
# Deal with trailing spaces
airbnb['room_type'] = airbnb['room_type'].str.strip()
airbnb['room_type'].unique()
# Replace values to 'Shared room', 'Entire place', 'Private room' and 'Hotel room' (if applicable).
mappings = {'private room': 'Private Room',
            'private': 'Private Room',
            'entire home/apt': 'Entire place',
            'shared room': 'Shared room',
            'home': 'Entire place'}

# Replace values and collapse data
airbnb['room_type'] = airbnb['room_type'].replace(mappings)
airbnb['room_type'].unique()
##### **Task 5:** Divide `neighbourhood_full` into 2 columns and making sure they are clean
# Print header of column
airbnb['neighbourhood_full'].head()
neighbourhood_split = airbnb['neighbourhood_full'].str.split(', ', expand=True)
neighbourhood_split.columns = ['neighbourhood', 'city']
neighbourhood_split.head()
#making sure that the split was done correctly
airbnb['neighbourhood'] = neighbourhood_split['neighbourhood'].str.strip()
airbnb['city'] = neighbourhood_split['city'].str.strip()
airbnb[['neighbourhood', 'city']]= neighbourhood_split[['neighbourhood', 'city']]
airbnb[['neighbourhood', 'city']].head()      
##### **Task 6:** Make sure we set the correct maximum for `rating` column out of range values
airbnb['rating'].describe()
airbnb.loc[airbnb['rating'] > 5.0, 'rating'] = 5.0
airbnb['rating'].describe()  

## **Q&A**
### Dealing with missing data
The `missingno` (imported as `msno`) package is great for visualizing missing data - we will be using:

- `msno.matrix()` visualizes a missingness matrix
- `msno.bar()` visualizes a missngness barplot
- `msno.dendrogram()` visualizes all connections (clusters) between NA's
- `plt.show()` to show the plot
# Visualize the missingness
msno.matrix(airbnb)
plt.show()
Looking at the missingness matrix, we can see that missing values are almost identical between `last_review`, `reviews_per_month`, `rating`, `number_of_stays`, and `5_stars`. Let's confirm this further by sorting on `rating`.
# Visualize the missingness on sorted values
msno.matrix(airbnb.sort_values(by = 'rating'))
plt.show()
msno.dendrogram(airbnb)
plt.show()
# Missingness barplot
msno.bar(airbnb)
**Treating the** `rating`, `number_of_stays`, `5_stars`, `reviews_per_month` **columns**
# Understand DataFrame with missing values in rating, number_of_stays, 5_stars, reviews_per_month
airbnb[airbnb['rating'].isna()].describe()
# Understand DataFrame with missing values in rating, number_of_stays, 5_stars, reviews_per_month
airbnb[~airbnb['rating'].isna()].describe()
Looking at the missing data in the DataFrame - we can see that `number_of_reviews` across all missing rows is 0. We can infer that these listings have never been visited - hence could be inferred they're inactive/have never been visited.

We can impute them as following:

- Set `NaN` for `reviews_per_month`, `number_of_stays`, `5_stars` to 0.
- Since a `rating` did not happen, let's keep the column as is - but create a new column named `rated` that takes in `1` if yes, `0` if no.
- We will also leave `last_review` as is.

# Impute missing data
airbnb = airbnb.fillna({'reviews_per_month':0,
                        'number_of_stays':0,
                        '5_stars':0})

# Create is_rated column
is_rated = np.where(airbnb['rating'].isna() == True, 0, 1)
airbnb['is_rated'] = is_rated
**Treating the** `price` **column**
# Investigate DataFrame with missing values in price
airbnb[airbnb['price'].isna()].describe()
# Investigate DataFrame with missing values in price
airbnb[~airbnb['price'].isna()].describe()
From a common sense perspective, the most predictive factor for a room's price is the `room_type` column, so let's visualize how price varies by room type with `sns.boxplot()` which displays the following information:


<p align="center">
<img src="https://github.com/adelnehme/cleaning-data-in-python-live-training/blob/master/boxplot.png?raw=true" alt = "DataCamp icon" width="80%">
</p>



# Visualize relationship between price and room_type
sns.boxplot(x = 'room_type', y = 'price', data = airbnb)
plt.ylim(0, 400)
plt.xlabel('Room Type')
plt.ylabel('Price')
plt.show()
# Get median price per room_type
airbnb.groupby('room_type')['price'].median()
# Impute price based on conditions
airbnb.loc[(airbnb['price'].isna()) & (airbnb['room_type'] == 'Entire place'), 'price'] = 163.0
airbnb.loc[(airbnb['price'].isna()) & (airbnb['room_type'] == 'Private Room'), 'price'] = 70.0
airbnb.loc[(airbnb['price'].isna()) & (airbnb['room_type'] == 'Shared Room'), 'price'] = 50.0
# Confirm price has been imputed
airbnb.isna().sum()
### What's still to be done?
Albeit we've done a significant amount of data cleaning tasks, there are still a couple of problems we have yet to diagnose. When cleaning data, we need to consider:

- Values that do not make any sense *(for example: are there values of `last_review` that older than `listing_added`? Are there listings in the future?*)
- Presence of duplicates values - and how to deal with them?
##### **Task 8:** Do we have consistent date data?
# Doing some sanity checks on date data
today = dt.date.today()
# Are there reviews in the future?

airbnb['last_review'] = pd.to_datetime(airbnb['last_review'], errors='coerce')

today = pd.Timestamp.today().normalize()

airbnb[airbnb['last_review'] > today]
# Are there listings in the future?

airbnb['listing_added'] = pd.to_datetime(airbnb['listing_added'], errors='coerce')

today = pd.Timestamp.today().normalize()

airbnb[airbnb['listing_added'] > today]
airbnb['listing_added'] = pd.to_datetime(airbnb['listing_added'])
airbnb['last_review'] = pd.to_datetime(airbnb['last_review'])

inconsistent_dates = airbnb[airbnb['listing_added'].dt.date > airbnb['last_review'].dt.date]


inconsistent_dates

airbnb['listing_added'] = pd.to_datetime(airbnb['listing_added'])
airbnb['last_review'] = pd.to_datetime(airbnb['last_review'])

inconsistent_dates = airbnb[airbnb['listing_added'].dt.date > airbnb['last_review'].dt.date]

airbnb.drop(inconsistent_dates.index, inplace=True)

airbnb[airbnb['listing_added'].dt.date > airbnb['last_review'].dt.date] 


##### **Task 9:** Let's deal with duplicate data

There are two notable types of duplicate data:

- Identical duplicate data across all columns
- Identical duplicate data cross most or some columns

To diagnose, and deal with duplicate data, we will be using the following methods and functions:

- `.duplicated(subset = , keep = )`
  - `subset` lets us pick one or more columns with duplicate values.
  - `keep` returns lets us return all instances of duplicate values.
- `.drop_duplicates(subset = , keep = )`
  
# Print the header of the DataFrame again
airbnb.head() 
airbnb[airbnb.duplicated(keep=False)].sort_values(by='listing_id')
# Remove identical duplicates
airbnb = airbnb.drop_duplicates() 
# Find non-identical duplicates
airbnb.duplicated(subset='listing_id', keep=False).sum()  
# Show all duplicates
airbnb[airbnb.duplicated(subset='listing_id', keep=False)] 
To treat identical duplicates across some columns, we will chain the `.groupby()` and `.agg()` methods where we group by the column used to find duplicates (`listing_id`) and aggregate across statistical measures for `price`, `rating` and `list_added`. The `.agg()` method takes in a dictionary with each column's aggregation method - we will use the following aggregations:

- `mean` for `price` and `rating` columns
- `max` for `listing_added` column
- `first` for all remaining column

*A note on dictionary comprehensions:*

Dictionaries are useful data structures in Python with the following format
`my_dictionary = {key: value}` where a `key` is mapped to a `value` and whose `value` can be returned with `my_dictionary[key]` - dictionary comprehensions allow us to programmatically create dicitonaries using the structure:

```
{x: x*2 for x in [1,2,3,4,5]}
{1:2, 2:4, 3:6, 4:8, 5:10}
```
# dictionary comprehension - ustawienie reguły 'first' dla wszystkich kolumn (oprócz ID)
aggregations = {col: 'first' for col in airbnb.columns if col != 'listing_id'}

#podmienianie reguły dla trzech wyjątkowych kolumn
aggregations['price'] = 'mean'
aggregations['rating'] = 'mean'
aggregations['listing_added'] = 'max'

#łączenie wierszy (.groupby i .agg)
airbnb = airbnb.groupby('listing_id').agg(aggregations).reset_index() 

airbnb["price"] = ( 
    airbnb["price"]
    .astype(str)
    .str.replace("$", "", regex=False)
    .str.replace(",", "", regex=False)
    .astype(float)
)

table = airbnb.groupby("room_type")["price"].agg(
    mean="mean",
    median="median",
    mode=lambda x: x.mode().iloc[0],
    std="std",
    skewness="skew",
    kurtosis=lambda x: x.kurtosis(),
    q1=lambda x: x.quantile(0.25),
    q3=lambda x: x.quantile(0.75)
)

table = table.round(2)

table