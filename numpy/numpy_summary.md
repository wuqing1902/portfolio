## Introduction to NumPy

NumPy (Numerical Python) is one of the most important libraries in Python for scientific computing. It provides support for multi-dimensional arrays and efficient mathematical operations. Compared to Python lists, NumPy arrays are significantly faster, more memory-efficient, and allow vectorized operations without the need for explicit loops. This makes NumPy a foundational tool in fields such as data science, machine learning, and bioinformatics.

<br><br><br>

## Creating Arrays in NumPy

NumPy provides multiple ways to create arrays. The most basic method is using `np.array()` with Python lists. In addition, NumPy provides built-in functions such as `np.zeros()` and `np.ones()` for initializing arrays with default values. For numerical sequences, `np.arange()` generates evenly spaced values within a range, while `np.linspace()` creates a specified number of evenly distributed points between two values. These tools are commonly used when preparing data structures for scientific computation.

<br><br><br>

## NumPy Arrays and Their Structure

A NumPy array is an object that stores data in a structured grid format. These arrays can exist in different dimensions, including 1D vectors, 2D matrices, and higher-dimensional tensors. Each array has important attributes such as `ndim` (number of dimensions), `shape` (structure of the array), and `size` (total number of elements). These attributes help us understand the structure of the data before performing any computation.

<br><br><br>

## Indexing and Slicing

NumPy allows efficient access to elements using indexing and slicing. In one-dimensional arrays, elements can be accessed using their position, while multi-dimensional arrays require row and column indexing. Slicing follows the standard `[start:stop:step]` format, allowing flexible selection of data subsets. Unlike Python lists, slicing in NumPy returns a view instead of a copy, meaning changes to the sliced array may affect the original dataset unless explicitly copied.

<br><br><br>

## Mathematical and Element-wise Operations (Universal Functions)

NumPy supports element-wise operations, meaning mathematical operations are applied directly to each element of an array. This includes addition, subtraction, multiplication, division, and exponentiation. In addition, NumPy provides universal functions such as `np.sqrt()`, `np.exp()`, `np.sin()`, and `np.cos()` for efficient mathematical computation. These operations eliminate the need for loops and significantly improve performance.

<br><br><br>

## Reshaping and Flattening Data

NumPy provides powerful tools for changing the structure of arrays without changing their data.

reshape() is used to change the dimensions of an array (e.g., converting 1D data into 2D matrices).
ravel() or flatten() is used to convert multi-dimensional arrays into a single 1D array.

These operations are commonly used in machine learning preprocessing, where data must be converted into specific input formats for models.

<br><br><br>

## Array Views vs Copies

Understanding the difference between views and copies is critical in NumPy. A view shares memory with the original array, meaning modifications affect both structures. A copy, created using `.copy()`, is independent and does not affect the original array. This distinction is important when manipulating large datasets, especially in scientific and bioinformatics applications where unintended data modification can lead to incorrect results.

<br><br><br>

## Broadcasting in NumPy

Broadcasting is a powerful feature that allows NumPy to perform operations between arrays of different shapes. When dimensions are not equal, NumPy automatically expands the smaller array to match the larger one under specific compatibility rules. This feature simplifies matrix operations and is widely used in machine learning and data processing tasks.

<br><br><br>

## Aggregation and Statistical Functions

NumPy provides several aggregation functions such as `np.sum()`, `np.mean()`, `np.max()`, `np.min()`, `np.std()`, and `np.var()` to summarize data. These functions can also operate along specific axes, allowing calculations across rows or columns in multi-dimensional arrays. This is particularly useful when analyzing structured datasets such as gene expression tables.

<br><br><br>

## Filtering and Conditional Selection

NumPy allows efficient filtering of data using boolean conditions. Expressions such as `array[array > value]` return elements that satisfy a condition. Multiple conditions can be combined using logical operators like `&` and `|`. Additionally, `np.where()` can be used to replace values based on conditions, making it a powerful tool for data cleaning and preprocessing.

<br><br><br>

## Concatenation and Sorting Data

NumPy provides tools for combining and organizing datasets.

np.concatenate() is used to join multiple arrays along an existing axis.
np.sort() is used to sort elements in ascending or descending order.

These operations are useful when merging datasets or analyzing ranked biological or numerical values.

<br><br><br>

## Handling Missing Data

Real-world datasets often contain missing or undefined values. NumPy represents these using np.nan (Not a Number). Since missing values cannot be processed directly in most computations, NumPy provides tools such as np.isnan() to detect missing values and functions like np.nan_to_num() to replace them with valid numerical values. Proper handling of missing data is essential in scientific computing and bioinformatics.

<br><br><br>

## Random Number Generation

NumPy provides a modern random number generator using `np.random.default_rng()`. This allows generation of random integers, floating-point numbers, and selections from arrays. These functions are widely used in simulations, machine learning initialization, and statistical modeling.

<br><br><br>



<!--
## Real-World Application in Bioinformatics

NumPy is widely used in bioinformatics for representing and analyzing biological data such as gene expression matrices, DNA sequences, and protein features. For example, gene expression data can be stored as a matrix where rows represent genes and columns represent samples. Statistical operations such as mean and variance can then be applied efficiently across biological datasets.

<br><br><br>
-->

## Conclusion

NumPy is a fundamental library for numerical computing in Python. Its efficiency, flexibility, and powerful mathematical capabilities make it essential for data-driven fields such as machine learning and bioinformatics. Mastery of NumPy provides a strong foundation for more advanced tools such as Pandas, Scikit-learn, and deep learning frameworks.
