#small raport

## 1. Data Ingestion and Structural Analysis (Exercise 1)
The first excerisise involved handling a pipe-separated (`|`) user dataset to establish a baseline for structural data exploration.



* Custom Indexing: Utilized `set_index('user_id')` to transform a standard column into a functional index, optimizing row-level lookups.
* Metadata Inspection: Leveraged `.info()`, `.columns`, and `.dtypes` to identify data types (integers vs. objects) and ensure memory efficiency.
* Descriptive Statistics: Applied the `.describe(include='all')` method to generate a statistical overview of both numerical and categorical distributions.

## 2. Advanced Filtering and Coordinate-Based Selection (Exercise 2)
This exercise focused on the Euro 2012 dataset, emphasizing conditional logic and the difference between label-based and integer-based indexing.



* Boolean Indexing: Implemented complex filters (e.g., `df[df['Goals'] > 6]`) to create subsets of the data based on performance criteria.
* Vectorized String Operations: Used `.str.startswith()` for efficient pattern matching within the "Team" series.
* Subsetting with .loc and .iloc: * Demonstrated label-based selection** with `.loc` to extract specific metrics.
    * Demonstrated positional slicing with `.iloc` to select specific column ranges.

## Exercise 3
This task utilized a global drinks dataset to demonstrate powerful data aggregation techniques via the GroupBy object.



* Data Aggregation: Used `.groupby('continent')` to partition the dataset and applied aggregate functions like `.mean()` and `.median()`.
* Handling Non-Numeric Data: Explicitly passed `numeric_only=True` to aggregation methods to prevent `TypeErrors` in Pandas 2.0+.
* Custom Aggregations: Utilized the `.agg()` method to compute multiple statistics (min, max, mean) simultaneously.

---
Prepared by: Aleksandra Kowalewska, Joanna Kowalewska, Karolina Masiak, Alicja Zacharzewska.