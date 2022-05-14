# Tuition_Status

## Background

In New York City there is a small but mighty post-secondary vocational school that is licensed by the the New York State Education Department (NYSED) Bureau of Proprietary School Supervision (BPSS), accredited by the Commission of the Council on Occupational Education (COE), and approved by both the United States Department of Education (USDE) and Department of Veteran Affairs (VA).

As the Director of Financial Aid Compliance & Veterans Affairs, part of my role is to oversee students' tuition plans and to identify trends in payment history. Being a school of this size, which graduates less than 150 of students per fiscal year, students who default on their tuition payments can drastically affect the financial performance of the school.

The school, which has requested its name to remain anonymous for this analysis, offers two main programs that will be included within this analysis - a 150-hour part-time program and a 600-hour full-time program, both of which will be described in more detail later on in the analysis.

## Topic Selection

This analysis will consider the following factors and determine if any have a significant influence on whether students default on their tuition payments.

- Gender
- Age
- Race / ethnicity
- GED vs high school diploma
- Years between completing GED / high school and starting a program at this school
- Previous post-secondary experience (yes or no)
- Full-time program (600 hours) vs part-time program (150 hours)
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

Using Jupyter Notebook, the following dependencies were imported to EDA.ipynb to assist with the cleaning and analysis of the data in 

<img src="https://github.com/mkirsch2/tuition_status/blob/main/images/dependencies.png" width="700" height="400" />

The combined CSV file (prepped_data.csv) was read in using Pandas and exploratory data analysis was completed - 

- Viewed samples of the data using df.head() and df.tail()
- Dropped null values using df.dropna()
- Identified the data types using df.dtypes()
- Reviewed descriptive statistics using df.describe()
- Used Sklearn's LabelEncoder to transform objects into numeric values
- Created two factors called years_between_education and age_at_grad<sup>1</sup>
- Used np.timedelta64 to convert the new variables to years
- Dropped unneeded columns - hs_ged_grad_date, grad_date, date_of_birth, hours_attended, hours_scheduled<sup>2</sup>
- Exported the cleaned data to a new CSV

<sup>1</sup> years_between_education was engineered from two features that were in the original dataset - hs_ged_grad_date and grad_date - by calculating the difference in years between the two values. For this analysis, knowing the timeframe between students completing their secondary education and completing the full-time or part-time programs was desired, but the original data source did not have this information in the necessary format. Similarly, age_at_grad was calculated by subtracting the date_of_birth from grad_date to determine how old students were when they completed their programs.

<sup>2</sup> hs_ged_grad_date, grad_date, and date_of_birth were no longer needed due to the creation of the two new factors. hours_attended and hours_scheduled were dropped because attendance_percentage already captured the attendance data that was needed.

## Machine Learning Model

This analysis deals with classificiation - whether or not a student will default on their tuition payments. There are only two outcomes - yes or no. A logistic regression model was first used, but due to the type of data being analyized, there is potential for overfitting.

Instead, a random forest model was implemented, as this type of model is powerful against overfitting. After running the first model, the nine factors were ranked by importance and the top four factors were selected and input back into the model.

<img src="https://github.com/mkirsch2/tuition_status/blob/main/images/phase_1.png" width="700" height="400" />



## Definitions
The following are commonly used words or phrases used throughout the analysis.
