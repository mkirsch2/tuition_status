# Tuition_Status

## Background

In New York City there is a small post-secondary vocational school that is licensed by the the New York State Education Department (NYSED) Bureau of Proprietary School Supervision (BPSS), accredited by the Council on Occupational Education (COE), and approved by both the United States Department of Education (USDE) and Department of Veterans Affairs (VA).

As the Director of Financial Aid Compliance & Veterans Affairs, part of my role is to oversee students' tuition plans and to identify trends in payment history. Being a school of this size, which graduates less than 150 of students per fiscal year, students who default on their tuition payments can drastically affect the financial performance of the school.

The school, which has requested its name to remain anonymous for this analysis, offers two main programs that will be included within the analysis - a 150-hour part-time program and a 600-hour full-time program.

## Topic Selection

This analysis will consider the following factors and determine if any have a significant influence on whether students who have graduated will default on their tuition payments.

- Program
- Age
- Gender
- Previous post-secondary experience
- Race / ethnicity
- GED vs high school diploma
- Years between completing GED / high school and starting a program at this school
- Final attendance percentage
- Final GPA

## Source of the Data

The datasets used for this project are directly from the school and are not publically available elsewhere. To ensure privacy of student information, personally identificable information (PII) has been removed from the dataset. This includes, but is not limited to, SSNs, names, and street addresses.

The data has been extracted from the school's student information system (Diamond SIS), and exported as several CSVs.

## Database

Prior to creating a database, an entitity relationship diagram (ERD) was created to visualize the various tables and to identify the primary and foreign keys.

<img src="https://github.com/mkirsch2/tuition_status/blob/main/images/QuickDBD-export.png" width="700" height="400" />

Pgadmin was then used to create a database to house the data for this analysis. Tables were created for each CSV file to be imported into. The primary and foreign keys were used to join the tables into one final table (prepped_data.csv) to use for the exploratory data analysis.

## Exploratory Data Analysis and Preliminary Feature Engineering

Using Jupyter Notebook, the following dependencies were imported to EDA.ipynb to assist with the cleaning and analysis of the data:

<img src="https://github.com/mkirsch2/tuition_status/blob/main/images/dependencies.png"/>

The combined CSV file (prepped_data.csv) was read in using Pandas and exploratory data analysis was completed - 

- Viewed samples of the data using df.head() and df.tail()
- Identified and dropped null values using df.dropna()
- Identified the data types using df.dtypes()
- Used Sklearn's LabelEncoder to transform objects into numeric values
- Created two factors called years_between_education and age_at_grad<sup>1</sup>
- Used np.timedelta64 to convert the new variables to years
- Dropped unneeded columns - grad_date, hs_ged_grad_date, date_of_birth, hours_attended, hours_scheduled<sup>2</sup>
- Reviewed descriptive statistics using df.describe()
- Created a box plot for years_between_education, age_at_grad, and gpa to view outliers
- Determined that the outliers for gpa were errors in the original data, due to 70 being the minimum GPA for students to graduate
- Removed the four rows with gpa outliers from the dataframe
- Reviewed descriptive statistics again using df.describe()
- Confirmed the total number of rows and columns using df.shape
- Exported the cleaned data to a new cleaned_data.csv

<sup>1</sup> years_between_education was engineered from two features that were in the original dataset - hs_ged_grad_date and grad_date - by calculating the difference in years between the two values. For this analysis, knowing the timeframe between students completing their secondary education and completing the full-time or part-time programs was desired, but the original data source did not have this information in the necessary format. Similarly, age_at_grad was calculated by subtracting the date_of_birth from grad_date to determine how old students were when they completed their programs.

<sup>2</sup> hs_ged_grad_date, grad_date, and date_of_birth were no longer needed due to the creation of the two new factors. hours_attended and hours_scheduled were dropped because attendance_percentage already captured the attendance data that was needed.

## Machine Learning Model

This analysis deals with classificiation - whether or not a student will default on their tuition payments. There are only two outcomes - yes or no. A logistic regression model was first used, but due to the type of data being analyized, there is potential for overfitting.

Instead, a random forest model was implemented, as this type of model is powerful against overfitting. After running the first model, the nine factors were ranked by importance and the top four factors were selected and input back into the model.

<img src="https://github.com/mkirsch2/tuition_status/blob/main/images/phase_1.png" width="525" height="300" />



## Definitions
The following are commonly used words or phrases used throughout the analysis.
