## Introduction to Pandas

Pandas is a powerful Python library built on top of NumPy and is widely used for data analysis, data science, and machine learning. It provides a structured, tabular format similar to Excel, making it much easier to work with labeled datasets compared to raw NumPy arrays. Unlike NumPy, which focuses on numerical computation with arrays, Pandas is designed to handle real-world data that often contains different types of variables, missing values, and labeled columns. This makes it a fundamental tool in data cleaning, manipulation, and analysis workflows.

<br><br><br>





## Data Importing and Exporting

Pandas supports reading and writing data from multiple formats:

- CSV: `pd.read_csv()`
- JSON: `pd.read_json()`
- Excel: `pd.read_excel()`

During import, users can:

- Set index column using index_col
- Convert data formats automatically (e.g., strings to datetime using pd.to_datetime())

Exporting data is also supported for saving processed datasets.

<br><br><br>





## Creating Data in Pandas (Series and DataFrame)

Pandas provides two core data structures: Series and DataFrame.

A Series is a one-dimensional labeled array that represents a single column of data. It can be created using pd.Series() from Python lists or dictionaries. A Series supports custom indexing and automatically assigns a default integer index if none is provided.

A DataFrame is a two-dimensional tabular structure made up of rows and columns, similar to a spreadsheet or SQL table. It is commonly created using dictionaries where keys become column names and values become lists of data. New columns can also be added dynamically by assigning values to a new column name.

Pandas also allows adding rows using pd.concat() since the older .append() method is deprecated.

<br><br><br>





## Pandas Data Structures and Their Structure

A Series contains a single column of data with labels (index) and supports metadata such as:

- `dtype` (data type of elements)
- `index` (labels of each element)
- `values` (actual data)
- `name` (optional label of the Series)

A DataFrame is a structured collection of multiple Series sharing the same index. Each column in a DataFrame can have a different data type (heterogeneous structure).

Important inspection tools include:

- `.head()` → preview first rows
- `.tail()` → preview last rows
- `.info()` → structure and missing values summary
- `.describe()` → statistical summary of numerical columns

<br><br><br>





## Indexing and Slicing

Pandas provides two main indexing methods:

- Label-based indexing (.loc): uses row/column labels. In slicing, both start and end labels are included.
- Position-based indexing (.iloc): uses integer positions. Slicing follows standard Python rules (end excluded).

For Series, indexing can also be done directly using labels or integer positions. For DataFrames, both row and column selection can be specified using [rows, columns].

Example usage:

- df.loc['row_label', 'column_name']
- df.iloc[0:2, 0:3]

<br><br><br>






## Filtering and Conditional Selection

Pandas allows filtering data using boolean conditions. This creates a boolean mask (True/False values) that is applied to the DataFrame or Series.

Examples:

- df[df['Age'] > 20]
- df[(df['Type1'] == 'Fire') & (df['Type2'] == 'Flying')]

Multiple conditions can be combined using:

- & (AND)
- | (OR)
- ~ (NOT)

Filtering is widely used to extract meaningful subsets of data from large datasets.

<br><br><br>






## Aggregation and Statistical Functions

Pandas provides built-in aggregation functions to summarize data:

- mean()
- sum()
- min()
- max()
- count()

These functions can be applied to entire DataFrames or individual columns. For numerical-only operations, numeric_only=True is often used.

Pandas also supports group-based aggregation using groupby(), which allows data to be grouped by a specific column and then analyzed separately.

Example:

- df.groupby('Occupation')['Salary'].mean()

<br><br><br>





## Data Exploration and Understanding (NEW SECTION)

Pandas provides tools to understand the structure and distribution of data before analysis.

- `value_counts()` → counts frequency of each category
- `unique()` → returns all unique values in a column
- `nunique()` → returns number of unique values
- `sample()` → randomly selects rows from the dataset

These functions are commonly used in Exploratory Data Analysis (EDA).

<br><br><br>






## Pivot Tables and Correlation Analysis

Pandas supports advanced analytical summaries:

pivot_table() → creates Excel-style summary tables
corr() → calculates correlation between numerical variables

These are widely used in data science for pattern discovery and relationship analysis.

<br><br><br>






## Reshaping and Modifying Data

Pandas allows flexible modification of datasets:

- New columns can be added directly using `df['Salary'] = [...]`
- Rows can be added using `pd.concat()`
- Columns can be renamed using `df.rename(columns={'old': 'new'}, inplace=True)`

These operations make it easy to reshape and evolve datasets during analysis.

<br><br><br>






## Advanced Column Operations

Pandas provides powerful tools for transforming data:

- `apply()` → applies custom functions to columns or rows
- `map()` → replaces values using a mapping dictionary

These functions are widely used for data transformation and feature engineering.

<br><br><br>





## Index Management

Pandas allows full control over DataFrame indexing:

- `set_index()` → sets a column as the index
- `reset_index()` → restores default numeric index

This is important when working with structured or hierarchical datasets.

<br><br><br>






## Views vs Copies (Data Modification Behavior)

In Pandas, operations may return either a view or a copy of the original data. A view reflects changes in the original DataFrame, while a copy is independent. This distinction is important when modifying filtered or sliced data, as unintended changes may occur if working with views instead of explicit copies.

<br><br><br>





## Data Copy Safety

When modifying datasets, it is important to avoid unintended changes:

- `.copy()` → creates an independent copy of a DataFrame

This prevents accidental modification of the original dataset during analysis.

<br><br><br>






## Broadcasting in Pandas

Broadcasting allows operations between a scalar value and an entire column. The scalar value is automatically applied to each element in the column.

Example: `df['Salary'] + 5000`

This simplifies large-scale transformations without the need for explicit loops.

<br><br><br>







## Data Cleaning

Data cleaning is one of the most important tasks in Pandas and includes handling missing, duplicate, or inconsistent data.

Handling Missing Values:
- `df.isnull().sum()` → detect missing values
- `dropna()` → remove missing values
- `fillna()` → replace missing values
- forward fill (`ffill`) and backward fill (`bfill`) for sequential data


Handling Duplicates:
- `df.duplicated()` → detect duplicates
- `df.drop_duplicates()` → remove duplicates


Fixing Data Issues:
- `replace()` → replace incorrect values
- `str.lower()` → standardize text
- `astype()` → convert data types

<br><br><br>






## Sorting Data

Pandas allows sorting data to organize or rank values.

- `sort_values()` → sorts data by column values
- `sort_index()` → sorts data by index labels

Sorting is useful for ranking data such as salaries, scores, or performance metrics.

<br><br><br>





## Data Types and Column Selection

Understanding data types is essential for correct analysis:

- `dtypes` → shows data types of each column
- `select_dtypes()` → selects columns by type (numeric, object, etc.)

These tools help separate numerical and categorical data for analysis.

<br><br><br>





## String Processing in Pandas

Pandas provides vectorized string operations for text data:

- `.str.upper() / .str.lower()` → standardize text case
- `.str.contains()` → checks if text contains a pattern

These are important for cleaning and analyzing categorical or text data.

<br><br><br>







## Joins and Merging Data

Pandas supports combining datasets using different methods:

- `Concat`: stacks DataFrames vertically or horizontally
- `Merge`: combines DataFrames based on a common key (similar to SQL joins)

Supports:
- inner join
- outer join
- left join
- right join

These operations are essential when working with multiple datasets.

<br><br><br>






## Conclusion

Pandas is a core library for data manipulation and analysis in Python. It provides flexible and efficient tools for handling structured data, making it essential for data science, machine learning, and bioinformatics. Mastering Pandas enables users to clean, transform, analyze, and visualize data efficiently, forming a strong foundation for advanced analytical workflows.
