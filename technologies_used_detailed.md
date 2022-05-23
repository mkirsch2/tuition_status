# Technologies used

## Preparation
### Quick DBD
- Used to create a conceptual entity relationship diagram
- Identified primary and foreign keys


## Database Storage and Initial Cleaning
### Pgadmin
- Created tables to hold data from each CSV file
- Imported each CSV data into matching table
- Joined tables through use of primary and foreign keys
- Created final table to use for machine learning
- Exported final table to a CSV file


## Cleaning and Analysis
### Jupyter Notebook and Pandas
- Read in CSV file and performed exploratory data analysis using Pandas
- Viewed samples of the data using df.head() and df.tail()
- Dropped null values using df.dropna()
- Identified the data types using df.dtypes()
- Reviewed descriptive statistics using df.describe()
- Used Sklearn's LabelEncoder to transform objects into numeric values
- Exported the cleaned data to a new CSV


## Machine learning
### Jupyter Notebook
- Read in CSV file with cleaned data
- Determined the independent (Y) and dependent (X) variables
- Split X and Y into training and testing sets
- Instantiated and trained a logistic regression model
- Validated the logisitic regression model
- Assessed the performance

- Read in CSV file with cleaned data
- Determined the independent (Y) and dependent (X) variables
- -Split X and Y into training and testing sets and scaled the data
- Fit the model
- Assessed the performance
- Rank factor importance
- Re-ran the model


## Dashboard
### Tableau
- 
