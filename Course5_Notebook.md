# <span style="color: gold;">Module 1</span>

## Let's get organized  

**Course Content:**   
- Irganize data to begin analysis.  
- Format and adjust data.  
- Aggregate data for analysis.  
- Perform data calculation.  
---
## Organize data for analysis
### The analysis process
> [!NOTE]
> **Analysis**:  
> &emsp;The process used to make sense of the data collected 

The goal of analysis is to idnetify trends and relationships with data so you can accurately answer the question you're asking.  

**The 4 phases of analysis:**  
1. Organize data  
2. Format and adjust data  
3. Get input from others  
4. Transform data  

#### Upload of the Dataset to BigQuery  
1. Create a dataset named 'movie_data'.  
2. Create the table 'movies'.  
3. Populate the table with data from the file `course5_asstes\Course_05-Movie_Data.csv`.  
   > _In the course, it is instructed to access the *Advanced Options* menu to allow the use of parentheses in column names by setting *'Column name character map'* to *'V2'*. However, this parameter does not exist in the *bigquery* library, so the "()" in the 'CSV' file were removed._

### Filter data with SQL
> [!NOTE]
> **Sorting**:  
> &emsp;When you arrange data into a meaningful order to make it easier to understand, analyze, and visualiza.
>
> **Filtering**:  
> &emsp;Showing only the data taht meets a specific criteria while hiding the rest

1. Use the *Where* clause to filter the database and narrow down the list to movies in the comedy genre.
    **Sintaxe:**
    ```sql
    SELECT <columns>
    FROM <table>
    WHERE <filter>
    ```
### Test your knowledge on organizing data for analysis
1. Fill in the blank: The goal of analysis is to identify _____ within data in order to accurately answer questions and solve problems.  
_`trends and relationships`_  
    > Correct  
    > The goal of analysis is to identify trends and relationships within data in order to accurately answer questions and solve problems. 

2. A data analyst organizes a database to show only the 100 most recent real estate sales in Stamford, Connecticut. What steps do they take?  
_`Add a filter to return only sales in Stamford, Connecticut, then sort the most recent sales at the top of the list.`_  
    > Correct  
    > The data analyst adds a filter for only sales in Stamford, Connecticut, then sorts the most recent sales at the top of the list.

3. What term describes data points that are very different from similarly collected data and, therefore, might not be reliable values?  
_`Outliers`_  
    > Correct  
    > Outliers are data points that are very different from similarly collected data and might not be reliable values.

4. In what way is the SQL WHERE clause similar to filtering in spreadsheets?  
_`Both the WHERE clause and spreadsheet filters return a subset of data based on specified criteria. `_  
    > Correct  
    > The WHERE clause is similar to filtering in spreadsheets because both return a subset of data based on specified criteria.  

## Sort data in spreadsheets

### Sort data in spreadsheet
1. 


> [!TIP]
>**Question:**  
> Which menu sort function is used to keep data together across rows?  
> _`Sort Sheet is the menu sort function that keeps data together  across rows. It also sorts all the data in the sheet, based on the ranking of a specified column.`_

### Using the SORT function in spreadsheets
> [!NOTE]
> **Costumized sort order**  
> &emsp;When you sort data in a spreadsheet using multiple conditions.

> [!TIP]
>**Question:**  
> Which of the following statements accurately describe differences between the sort from a spreadsheet's Data tab and a written SORT function? Select all that apply.  
> _`The sort from a spreadsheet's Data tab overwrites the cells containing the unsorted data with the sorted data, while a written SORT function inserts the sorted data in a different cell range.`_
> _`The sort from a spreadsheet's Data tab can exclude a header row in the data range from being sorted, while the data range for a written SORT function should never contain a header row.`_

1. 
2. 
3. 

### Test your knowledge on sorting data in spreadsheets
1. Which menu function sorts all spreadsheet data by the ranking of a specific sorted column?  
_`Sort sheet`_  
    > Correct  
    > Sort sheet sorts all spreadsheet data by the ranking of a specific sorted column.

2. When using the SORT function in spreadsheets, which statement will return the data in ascending order?  
_`TRUE`_  
    > Correct  
    > When using the SORT function in spreadsheets, a TRUE statement will return the data in ascending order.  

3. Fill in the blank: A customized sort order involves sorting data in a spreadsheet using _____ conditions.  
_`Multiple`_  
    > Correct  
    > A customized sort order involves sorting data in a spreadsheet using multiple conditions. This means that the sorting will be based on the order of the conditions selected.  

4. Why would a data professional select Data has a header row when sorting data in a spreadsheet?  
_`To ensure the first row of data is treated as header labels instead of data points`_  
    > Correct  
    > A data professional selects Data has a header row when sorting data in a spreadsheet to ensure the first row of data is treated as header labels instead of data points.

## Sort data using SQL
The ORDER BY command sorts data by column in a database. By default, the data is sorted in ascending order.

**Syntax:**  
Example 1 - Ascending Sort 
```sql
IMPORT *
FROM <data_set>
ORDER BY <field>;
```
Example 2 - Descending Sort
```sql
IMPORT *
FROM <data_set>
ORDER BY <field> DESC; --DESC returns data in descending order
```
Example 3 - Filter and Sort
```sql
IMPORT *
FROM <data_set>
WHERE <condityion>
ORDER BY <field> DESC; --The ORDER BY command is the last line to ensure all data is sorted.
```
Example 4 - Filter on two condiditions and sort in descending order
```sql
IMPORT *
FROM <data_set>
WHERE <condition_1> AND <condition_2>
ORDER BY <field> DESC; 
```

### Hands-On Activity: SQL sorting queries
_Was changed to be executed remotely with Python!_
#### <span style="color: gold;">Step 1: Load the CDC Births Data dataset</span>
1. Initialize the BigQuery Client.
2. Define the Dataset as _"bigquery\-public\-data.sdoh\_cdc\_wonder\_natality"_.  
    ```python
    project_id = "bigquery-public-data"
    dataset_id = "sdoh_cdc_wonder_natality"
    ```
3. Examnine the tables available within the dataset.
    ```python
    client.list_tables(client.dataset(<dataset_ID>, project=<project_ID>)
    # This will return a list of tables in the dataset.
    ```
4. Select the table county_natality and explore this table’s schema, details, and preview.
    ```python
    # Select the table
    client.get_table(f"<project_ID>.<dataset_ID>.<table_ID>")
    ```
    ```sql
    --- Explore table's schema
    SELECT
        column_name, data_type, is_nullable
    FROM
        `<project_ID>.<dataset_ID>.INFORMATION_SCHEMA.COLUMNS`
    WHERE
        table_name = '<table_ID>'
    ```
    ```sql
    --- Explore table's details
    SELECT
        column_name, data_type, is_nullable
    FROM
        `<project_ID>.<dataset_ID>.INFORMATION_SCHEMA.TABLES`
    WHERE
        table_name = '<table_ID>'
    ```
        ```sql
    --- Explore table's preview
    SELECT
        column_name, data_type, is_nullable
    FROM
        `<project_ID>.<dataset_ID>.<table_ID>`
    LIMIT 10
    ```
#### <span style="color: gold;">Step 2: Load the CDC Births Data dataset</span>

1. Display the first 1,000 rows of the county_natality table. 

#### <span style="color: gold;">Step 3: Use ORDER BY to sort relevant data</span>
1. ORDER BY Births field.
2. ORDER BY Births field, ascending explicit
3. ORDER BY Births field, largest to lowest

#### <span style="color: gold;">Step 4: Use sorted data to answer questions</span>
1. Exploring whether the birth rate trends in several counties in upstate New York have been increasing or decreasing—and whether they follow the same pattern.  
    To answer this, you’ll need the following information:
    - Results from Erie, Niagara, and Chautauqua counties in New York state.
    - Results ordered by county of residence and year to find the trend.  
      
    Based on the results of this query, are births in these three counties following the same trend? 

#### <span style="color: gold;">Reflection</span>
1. The last query you ran returned births in three counties, sorted by year and county. Now, you want to identify the greatest number of births in Erie, Chautauqua, or Niagara counties between 2016 and 2018. Modify the previous query to order the data by Births in descending order to make this easy to identify.
    1.1 How many births occurred in the county with the highest number of births in one year?
    _`9916`_

2. In this activity, you practiced sorting data using SQL queries with ORDER BY and filtering data with WHERE clauses. In the text box below, write 2-3 sentences (40-60 words) in response to each of the following questions:

    2.1. How can the ORDER BY clause help you organize and structure your data?
    _`The ORDER BY clause allows you to arrange data in a specific order, either ascending or descending. This helps in structuring the data in a way that makes it easier to analyze trends, identify patterns, or compare values, such as sorting sales data by highest to lowest revenue.`_
    
    2.2. Why is it helpful to use the ORDER BY and WHERE clauses together when analyzing data?
    _`Using ORDER BY with WHERE allows you to first filter the data to focus on specific conditions, and then organize it in a meaningful order. This combination helps you to narrow down results and view them in the most relevant sequence, improving the efficiency of data analysis.`_
    
    2.3. Describe a business question that you could answer using the ORDER By and WHERE clauses together. How would this method help you answer the question?
    _`A business question could be, "What are the top 5 products with the highest sales in the last quarter?" By using WHERE to filter sales data for the last quarter and ORDER BY to sort the results by sales, this method allows you to quickly identify the top performers and make informed decisions about inventory or marketing strategies.`_