# Tuition_Status

## Background

In New York City there is a small post-secondary vocational school that is licensed by the the New York State Education Department (NYSED) Bureau of Proprietary School Supervision (BPSS), accredited by the Council on Occupational Education (COE), and approved by both the United States Department of Education (USDE) and Department of Veterans Affairs (VA).

As the Director of Financial Aid Compliance & Veterans Affairs, part of my role is to oversee students' tuition plans and to identify trends in payment history. Being a school of this size, which graduates less than 150 students per fiscal year, students who default on their tuition payments can drastically affect the financial performance of the school.

The school, which has requested its name to remain anonymous, offers two main programs included within the analysis - a 150-hour part-time program and a 600-hour full-time program.

## Topic Selection

This analysis considers the following factors and determines if any have a significant influence on whether student completers will default on their tuition payments:

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

The datasets used for this project are directly from the school and are not publically available elsewhere. To ensure privacy of student information, personally identificable information has been removed from the dataset. This includes, but is not limited to, SSNs, names, and street addresses.

The data has been extracted from the school's student information system (Diamond SIS), and exported as several CSV files.

## Analysis & Findings

### Random Forest Models
The nine factors were imput into a random forest model and then ranked by importance. The top four factors were then selected and input back into the model.

#### Random Forest Model #1

<img src="https://github.com/mkirsch2/tuition_status/blob/main/images/model_1_imortance.png" width="275" height="150" />

#### Random Forest Model #2

<img src="https://github.com/mkirsch2/tuition_status/blob/main/images/model_2_imortance.png" width="275" height="75" />

#### Model Metrics

Random Forest Model #2 was used for the remainder of this analysis. To assess its performance, the following statistics were reviewed.

The overall accuracy of the model is 34%. However, as this dataset is imbalanced, having far less defaults than non defaults, this is not the best metric to assess the performance.

The precision for a student who has defaulted is 18%. This means out of all the defaults predicted, only 18% are actually defaults (high number of false positives).

The percentage of students who defaulted and were correctly predicted (recall) was 78%.

Having low precision and much higher recall, the F-1 score of 0.29 was analyzed.

Unfortunately, based on the model's metrics, this model does not appear to do well at predicting whether or not a completer student defaults on their tuition.

NOTE:
0 = not default
1 = default

<img src="https://github.com/mkirsch2/tuition_status/blob/main/images/model_2_metrics.png" width=35% height=35%/>


### Findings

Although the model did not perform well, the following trends were identified during the analysis.

Of the 407 student completers in this analysis, about 18% defaulted on their tuition. Based on the model, the top four factors that affect whether or not a student completer defaults on their tuition are:
- Age at graduation
- GPA
- Attendance percentage
- Years between education

The majority of defaults occur between ages 20 - 34. There may be several reasons for this:
- The youngest range of students (17 - 19 years old) may have financial assistance from their parents
- Students ages 20 - 34 may be early on in their careers and have less financial stability (for example, they may be earning or working less and have less experience with managing their finances)
- Students ages 35 - 64 may have more financial stability (for example, having a stable job and more experience managing their finances)

Most of the defaults occured for students with 0 - 14 years between completing high school or a GED program and completing a program at this school. This is fairly similar to the age of students who default.

<img src="https://github.com/mkirsch2/tuition_status/blob/main/images/default_age_vs_years_btwn_education.png" width=50% height=50%/>


The majority of defaults occur for students with GPAs between 80 and 94%, with the least amount of defaults (4) occuring for students with GPAs between 95 - 99%.

<img src="https://github.com/mkirsch2/tuition_status/blob/main/images/default_vs_gpa.png" width=75% height=75%/>


The majority of defaults occur for students with attendance falling in the 80 - 99% range. Surprisingly the lowest attendance range (75 - 79%) had zero defaults and 3 students with 100% attendance defaulted.

<img src="https://github.com/mkirsch2/tuition_status/blob/main/images/default_vs_attendance.png" width=75% height=75%/>


## Definitions of Factors and Common Terms

- gpa: final grade point average at the completion of a student's program

- attendance_percentage: total hours attended divided by total hours scheduled in a student's program

- years_between_education: years between graduating high school (or earning a GED) and completing a program at this school

- age_at_grad: student's age as of the date they completed their program

- ethnic_description: Hispanic or Latino; American Indian or Alaska Native, Asian, Black or African American, Native Hawaiian or Other Pacific Islander, White

- program: 150-hour program or 600-hour program

- gender: male, female

- previous_college: any post-secondary education beyond high school (or earning a GED)

- hs_ged: whether a student earned a high school diploma or a GED

- completers: students who graduated from the 15-hour or 600-hour program at this school
