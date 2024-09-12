# PySpark Window Functions Example

This project demonstrates how to apply various **window functions** using **PySpark** on a sample dataset. It covers functions such as `row_number`, `rank`, `dense_rank`, `ntile`, `lag`, `lead`, `cume_dist`, and `percent_rank`, applied to a DataFrame of employees, their departments, and salaries.

## Project Structure:
- **window_functions_example.py**: The main script containing PySpark code to showcase window functions.
- **README.md**: This documentation file.

## Description:
Window functions allow users to perform calculations across a set of rows related to the current row within a defined window (or partition). This project showcases a variety of window functions applied to a dataset of employees categorized by department and their salaries.

### Features:
1. **row_number()**: Assigns a unique sequential number within each partition.
2. **rank()**: Assigns a rank to each row, with gaps when there are ties.
3. **dense_rank()**: Similar to `rank()`, but without gaps in the ranking sequence.
4. **ntile(n)**: Divides the rows into `n` buckets, distributing them as evenly as possible.
5. **lag()**: Fetches the previous row's value within the same partition.
6. **lead()**: Fetches the next row's value within the same partition.
7. **cume_dist()**: Computes the cumulative distribution of a value in its partition.
8. **percent_rank()**: Computes the percentage rank of a row in its partition.

## Data:
The sample data consists of employees, their department, and their salary:
```
[
    ("Alice", "Sales", 1000),
    ("Bob", "Sales", 1500),
    ("Charlie", "Sales", 1000),
    ("David", "HR", 1200),
    ("Eva", "HR", 2000),
    ("Frank", "HR", 1600),
    ("Grace", "IT", 3000),
    ("Hank", "IT", 3500),
    ("Ivy", "IT", 3000)
]
```
![image](https://github.com/user-attachments/assets/9bbbf7ac-d97b-491c-a9a5-7ddd27081b11)


### Code Highlights:
- **Window Specification**: Data is partitioned by the "Department" column and ordered by the "Salary" column in descending order.
```python
window_spec = Window.partitionBy("Department").orderBy(col("Salary").desc())
```
- **Application of Window Functions**: Each window function is applied using the `over(window_spec)` method.
```python
row_number().over(window_spec).alias("row_number")
rank().over(window_spec).alias("rank")
dense_rank().over(window_spec).alias("dense_rank")
...
```

## How to Run:

1. **Requirements**:
   - PySpark installed and configured in your environment.
   - Alternatively, this project can be run on **Databricks** for ease of setup.

2. **Run the Script**:
   - Place the `window_functions_example.py` file in your environment or Databricks workspace.
   - Execute the script in a PySpark-enabled environment.

3. **Output**:
   - The output will display the original DataFrame of employees along with additional columns showing the results of each window function.
     ![image](https://github.com/user-attachments/assets/d97a0b3c-2e61-4d3a-96c3-9cf5095e1e1a)


## Additional Notes:
- This example demonstrates advanced data partitioning and ranking operations using PySpark’s window functions.
- Modify the sample data or window specification to suit specific use cases.

---

This project provides a simple yet powerful demonstration of window functions in PySpark, showcasing how to use them for partitioning and ranking operations on structured data.
