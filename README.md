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

## Analysis & Findings

The nine factors were imput into a random forest model and then ranked by importance. The top four factors were then selected and input back into the model.

Random Forest Model #1

<img src="https://github.com/mkirsch2/tuition_status/blob/main/images/model_1_imortance.png" width="275" height="150" />

Random Forest Model #2

<img src="https://github.com/mkirsch2/tuition_status/blob/main/images/model_2_imortance.png" width="275" height="75" />

## Definitions of Factors

- gpa: final grade point average at the completion of a student's program

- attendance_percentage: total hours attended divided by total hours scheduled in a student's program

- years_between_education: years between graduating high school (or receiving a GED) and completing a program at this school

- age_at_grad: student's age as of the date they completed their program

- ethnic_description: Hispanic or Latino; American Indian or Alaska Native, Asian, Black or African American, Native Hawaiian or Other Pacific Islander, White

- program: 150-hour program or 600-hour program

- gender: male, female

- previous_college: any post-secondary education beyond high school (or receiving a GED)

- hs_ged: whether a student received a high school diploma or a GED
