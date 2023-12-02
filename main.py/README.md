# Project 1 Assignment

## Introduction

## Datasets Analyzed

## Analysis and write up

### 1. Does gender affect pricing?
### 2. Does insurance provider or geography affect pricing rates?
### 3. What trends can be discovered by analyzing the age of patients across the dataset?
   In the healthcare world a patient’s age can be used to make a large number of predictions. Knowing a patient’s age can assist healthcare professionals in a number of ways including medical diagnosis, provided treatment, and estimated recovery time. We wanted to analyze the information based on a patient’s age to see if we could uncover trends to help inform decisions. For this analysis we mainly used our Healthcare Dataset

* To start our analysis of this question we created bins for the various age ranges we wanted to analyze. The bins we chose for our analysis were 18-30, 30-45, 45-60, 60-75, 75-90. We chose those age ranges because our dataset didn't have any records for patients less than 18 and greater than 90 years old. Once we added these bins to our dataframe we performed a quick analysis to identify the age ranges with the most and least records. The age range with the most records was 45-60 (2225 records), while the age range with the least records was 75-90 (1446 records). We just highlighted the age ranges that had the most and least number of records, but this information could be used by healthcare professionals to predict the number of patients per age range they may receive in a given period. 
  
Age Ranges | Total Patients | 
--- | --- |
18-30 | 1739 |
30-45 | 2211 |
45-60 | 2225 |
60-75 | 2215 |
75-90 | 1446 |

* The next thing we were interested in analyzing was the average time spent in the hospital per age range. This information could be useful to predict how long a patient may stay in the hospital given their age and some other factors. Our Healthcare Dataset included data for both the patient's admission date and discharge date at the hospital. We took these columns and converted them to datetime format. From there we calculated the patient's stay at the hospital by subtracting the discharge date from the admission date. This gave us the number of days the patient stayed in the hospital. We grouped by the age ranges we had created earlier and calculated the average stay at hospital per age range. We then plotted the results on a bar chart to compare the results (see Figure 3 below). \
![alt text](https://github.com/Handro4/Bootcamp-Project1/blob/main/Images/Average_Stay_vs_Age_Range.png) \
As you can see from looking at this chart there is hardly a difference between the average stay per age range. We were hoping to see a more noticeable difference between the age groups, but there's only a slight difference. What we can take from this chart is that age does not play a large role in a patient's length of stay at the hospital. This probably means there are better factors to determine the length of a patient's stay from (ex. medical condition, medication, etc.). One thing to reiterate here is that this is a synthetic dataset. I would expect a patient's age to play a larger role in their length of stay at the hospital.

* The third thing we were interested in analyzing was the relationship between age range and medical condition. The Healthcare Dataset included information about the medical condition for each patient. We grouped our dataset by age range and then took the value_counts() of that groupby in order to see the total count per medical condition for age group. We plotted the results on a bar chart to see the relationship between medical condition count and age range (see Figure 4 below). \
![alt text](https://github.com/Handro4/Bootcamp-Project1/blob/main/Images/Medical_Condition_Per_Age_Range.png) \
The first thing we can infer from this chart is the most commonly seen medical condition per age group (18-30 Hypertension, 30-45 Hypertension, 45-60 Cancer, 60-75 Asthma, 75-90 Cancer). On the flip side of things we are also able to see the least commonly seen medical condition per age range (18-30 Arthritis, 30-45 Diabetes, 45-60 Hypertension, 60-75 Cancer, 75-90 Arthritis). Interestingly enough we can see that Cancer is the most common medical condition for the 45-60 and 75-90 age groups, but is the least common for patients in the 60-75 age range. This could be something medical researchers would want to explore further to see if they can determine why the 60-75 age group sees the smallest amount of patients for cancer.

* The fourth thing we wanted to look at was the relationship between age and medication prescribed. The Healthcare Dataset included information about the medication prescribed for each patient. We thought it would be interesting to look at the breakdown of medication prescribed per age range. To obtain the desired results we once again grouped the dataframe by Age Range and then took the value_counts() of medication. We plotted the rsults on a bar chart to see the relationship between medication and age range (see Figure 5 below). \
![alt text](https://github.com/Handro4/Bootcamp-Project1/blob/main/Images/Medication_Count_Per_Age_Range.png) \
What stands on this chart is the most commonly medication used per age range (18-30 Ibuprofein, 30-45 Pencillin, 45-60 Penicillin, 60-75 Lipitor, 75-90 Penicilin). We can see that Penicillin is probably the most commonly used medication across all age groups. We can also easily identify the least used medication per age range (18-30 Paracetamol, 30-45 Ibuprofein, 45-60 Aspirin, 60-75 Paracetamol, 75-90 Lipitor). What's interesting is that Lipitor is the most commonly used medication for patients aged 60-75, while it's the least commonly used medication in the next age range of 75-90. This could mean that Lipitor looses it's effectiveness the older a patient gets. Based on these findings hospitals will most likely want to stock up on Penicillin, and we can assume that Penicillin has the greatest effect across all age ranges. Finally, the most noticeable gap between the top medication and other medications used across the age ranges is for the 30-45 group. Hospitals could use this information to identify the best medication used per age range. There are obviously other factors that need to be taken into account before a decision is made on the medication, but age could be a contributing factor.

* The final 

### 4. How does smoking affect billing?

![alt text](https://github.com/Handro4/Bootcamp-Project1/blob/main/Images/Age_vs_Amount_Charged.png)
