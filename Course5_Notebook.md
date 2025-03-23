## <span style="color: gold;">Module 1</span>

### Let's get organized  

**Course Content:**   
- Irganize data to begin analysis.  
- Format and adjust data.  
- Aggregate data for analysis.  
- Perform data calculation.  
---
### Organize data for analysis
> [!NOTE]
> **`Analysis`**:
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
   > In the course, it is instructed to access the *Advanced Options* menu to allow the use of parentheses in column names by setting *'Column name character map'* to *'V2'*. However, this parameter does not exist in the *bigquery* library, so the "()" in the 'CSV' file were removed. 

> [!NOTE]
> **`Sorting`**:
> &emsp;When you arrange data into a meaningful order to make it easier to understand, analyze, and visualiza.
>
> **`Filtering`**:
> &emsp;Showing only the data taht meets a specific criteria while hiding the rest

&emsp; 1. Aplicar um filtro para selecionar apenas os registros que contenham o Gênero como comédia

##### Test your knowledge on organizing data for analysis
1. Fill in the blank: The goal of analysis is to identify _____ within data in order to accurately answer questions and solve problems.
trends and relationships
    Correct
    The goal of analysis is to identify trends and relationships within data in order to accurately answer questions and solve problems. 

2. A data analyst organizes a database to show only the 100 most recent real estate sales in Stamford, Connecticut. What steps do they take?
Add a filter to return only sales in Stamford, Connecticut, then sort the most recent sales at the top of the list.
    Correct
    The data analyst adds a filter for only sales in Stamford, Connecticut, then sorts the most recent sales at the top of the list.

3. What term describes data points that are very different from similarly collected data and, therefore, might not be reliable values?
Outliers
    Correct
    Outliers are data points that are very different from similarly collected data and might not be reliable values.

4. In what way is the SQL WHERE clause similar to filtering in spreadsheets?
Both the WHERE clause and spreadsheet filters return a subset of data based on specified criteria. 
    Correct
    The WHERE clause is similar to filtering in spreadsheets because both return a subset of data based on specified criteria. 