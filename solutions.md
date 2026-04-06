#zad 1
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
users['age'].value_counts().idxmin()```

#Excersise 2

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
