##Raport
This document describes the technical steps used to analyze three datasets. The main goal was to use Pandas for data loading, indexing and grouping.

##Taks 1
The first part involved loading a user dataset. We used set index to organize the data by user id. We checked the data using methods like info, columns and dtypes to understand the variable types. We also used the describe method to get a statistical summary of the ages and occupations.

##Task 2
The second part used a Euro 2012 dataset. We used boolean indexing to find teams with specific scores. We used string methods like startswith to filter teams by name. We used loc and iloc for precise selection of columns and rows. Finally, we used sort values to rank teams by their disciplinary records.

##Taks 3
The last part used a drinks dataset to show data aggregation. We used groupby to split the data by continent. We calculated the mean and median for each group. We used numeric only equals true to avoid errors with text columns. We also used the agg method to find the minimum and maximum values at the same time.

Authors
Aleksandra Kowalewska, Joanna Kowalewska, Karolina Masiak, Alicja Zacharzewska.