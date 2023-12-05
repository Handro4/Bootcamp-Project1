# Project 1 Assignment

# Introduction

### Datasets Analyzed
   #### In this analysis we reviewed two different datasets we found on Kaggle. 
   
   * The first dataset we have referred to as the Healthcare Dataset
(https://www.kaggle.com/datasets/prasad22/healthcare-dataset). This dataset consists of 10,000 rows each representing a patient's healthcare record. The information included in the dataset includes patient data, admission dates, and healthcare services provided. This was the main dataset we used in our analysis. We chose this dataset because it provided a lot of depth to each healthcare record. An important thing to note is that this is a synthetic dataset that was created for analytical use. This has resulted in a lot of the data being randomized which made it difficult to draw meaningful insights.

   * The second dataset we used we have referred to as the Insurance Dataset (https://www.kaggle.com/datasets/willianoliveiragibin/healthcare-insurance/). This dataset consists of 1300+ rows each representing a medical claim. We were interested in this dataset as it contains information on the relationship between personal attributes and medical insurance charges that wasn't present in the previous dataset. We were hoping to eventually merge the datasets together, but they were ultimately unrelated. This is also a synthetic dataset that was created for analytical use. 

# Analysis and write up

## Question 1 

### What trends can we analyze based on gender?

#### Background
* Some studies suggest gender-based differences in healthcare utilization, potentially leading to variations in billing amounts. Factors include health conditions, types of healthcare services, and reproductive health needs. Our healthcare dataset focuses on chronic conditions for both genders (Figure 8). Several studies explore gender's impact on healthcare quality and costs. We aim to identify relationships between gender and billing amounts.
  
   ![alt text](https://github.com/Handro4/Bootcamp-Project1/blob/main/Images/Medical_Condition_Gender.png) 

### Analysis Question 1.A
#### How does gender affect pricing (healthcare dataset)?
* To understand higher billing amounts, we compared mean billing amounts across genders:
   * - Female: $25,484
   * - Male:   $25,550

#### How does gender affect pricing (insurance dataset)?
* No significant difference in billing amounts by gender in the healthcare dataset. Checked the insurance charges by geography dataset, finding:
   * - Female: $12,569.58
   * - Male:   $13,956.75
       
   ![alt text](https://github.com/Handro4/Bootcamp-Project1/blob/main/Images/Average_Charges_Per_Gender.png) 

### Analysis Question 1.B
#### How does insurance provider affect pricing by gender?

* As no significant gender-based billing difference was found, we explored variable cost drivers from insurance providers (Figure 1):

| Insurance Provider | Gender | Billing Amount |
|--------------------|--------|-----------------|
| Aetna              | Female | $25,335         |
|                    | Male   | $26,341         |
| Blue Cross         | Female | $26,178         |
|                    | Male   | $25,158         |
| Cigna              | Female | $25,724         |
|                    | Male   | $25,588         |
| Medicare           | Female | $25,008         |
|                    | Male   | $24,996         |
| UnitedHealthcare   | Female | $25,200         |
|                    | Male   | $25,617         |

### Figure 1
   ![alt text](https://github.com/Handro4/Bootcamp-Project1/blob/main/Images/Mean_Billing_Amount_by_Insurance_Provider_and_Gender.png) 

### Analysis Question 1.C

#### How does region and gender count affect pricing?

* Plotted gender count distribution for each region (Figure 14), with the southeast region exhibiting the highest average cost. The elevated male count in the southeast region may influence the region's elevated average cost, contributing to increased male billing charges.

   ![alt text](https://github.com/Handro4/Bootcamp-Project1/blob/main/Images/Gender_Counts_per_Region.png) 

## Question 2

### How does insurance provider and geography affect pricing rates?

#### Background

* Healthcare providers negotiate contracts with insurance companies, determining reimbursement rates. Rates vary between providers and facilities. We analyze data to explore relationships between insurance provider, geography, and billing amounts.

### Analysis Question 2.A

* Grouped by Medical Condition and Insurance Provider, calculated mean, minimum, and maximum billing amounts (head(5) info below):

| Medical Condition | Insurance Provider | Mean Billing | Min Billing | Max Billing |
|-------------------|--------------------|--------------|-------------|-------------|
| Arthritis         | Aetna              | $24,694.86   | $1,009.42   | $49,745.81  |
| ... (other conditions) | ...            | ...          | ...         | ...         |

* Continued (head(5) info):

| Medical Condition | Insurance Provider | Mean Billing | Min Billing | Max Billing |
|-------------------|--------------------|--------------|-------------|-------------|
| Arthritis         | Medicare            | $24,206.38   | $1,042.98   | $49,985.97  |
| Asthma            | Aetna               | $24,761.52   | $1,032.26   | $49,974.30  |
| ... (other conditions) | ...            | ...          | ...         | ...         |

#### How does insurance provider affect pricing rates?

* Explored maximum Billing Amount by Insurance Provider and Medical Condition, noting Aetna consistently having high billing amounts across various conditions.

### Analysis Question 2.B

#### How does geography affect pricing?

* Explored regional differences to understand the variance in billing rates. Graphed insurance dataset (Figure 10), finding highest billing in the Southeast region.
  
   ![alt text](https://github.com/Handro4/Bootcamp-Project1/blob/main/Images/Average_Charges_Per_Region.png)

### Analysis Question 2.C

#### What else could contribute to the southeast region having higher rates?

* Checked if BMI (body mass index) is a factor in billing charges by location (Figure 9). Southeast region appears to have a higher BMI.
  
   ![alt text](https://github.com/Handro4/Bootcamp-Project1/blob/main/Images/Average_BMI_per_Region.png) 

## Question 3

### How does age affect a patient's length of stay, medical condition, prescribed medication, and price?

#### In the healthcare world a patient’s age can be used to make a large number of predictions. Knowing a patient’s age can assist healthcare professionals in a number of ways including medical diagnosis, provided treatment, and estimated recovery time. We wanted to analyze the information based on a patient’s age to see if we could uncover trends to help inform decisions. For this analysis we mainly used our Healthcare Dataset

* To start our analysis of this question we created bins for the various age ranges we wanted to analyze. The bins we chose for our analysis were 18-30, 30-45, 45-60, 60-75, 75-90. We chose those age ranges because our dataset didn't have any records for patients less than 18 and greater than 90 years old. Once we added these bins to our dataframe we performed a quick analysis to identify the age ranges with the most and least records. The age range with the most records was 45-60 (2225 records), while the age range with the least records was 75-90 (1446 records). We just highlighted the age ranges that had the most and least number of records, but this information could be used by healthcare professionals to predict the number of patients per age range they may receive in a given period. 

   Age Ranges | Total Patients | 
   --- | --- |
   18-30 | 1739 |
   30-45 | 2211 |
   45-60 | 2225 |
   60-75 | 2215 |
   75-90 | 1446 |

### Analysis Question 3.A

* The next thing we were interested in analyzing was the average time spent in the hospital per age range. This information could be useful to predict how long a patient may stay in the hospital given their age and some other factors. Our Healthcare Dataset included data for both the patient's admission date and discharge date at the hospital. We took these columns and converted them to datetime format. From there we calculated the patient's stay at the hospital by subtracting the discharge date from the admission date. This gave us the number of days the patient stayed in the hospital. We grouped by the age ranges we had created earlier and calculated the average stay at hospital per age range. We then plotted the results on a bar chart to compare the results (see Figure 3 below).
  
   ![alt text](https://github.com/Handro4/Bootcamp-Project1/blob/main/Images/Average_Stay_vs_Age_Range.png) 

    As you can see from looking at this chart there is hardly a difference between the average stay per age range. We were hoping to see a more noticeable difference between the age groups, but there's only a slight difference. What we can take from this chart is that age does not play a large role in a patient's length of stay at the hospital. This probably means there are better factors to determine the length of a patient's stay from (ex. medical condition, medication, etc.). One thing to reiterate here is that this is a synthetic dataset. I would expect a patient's age to play a larger role in their length of stay at the hospital.

### Analysis Question 3.B

* The third thing we were interested in analyzing was the relationship between age range and medical condition. The Healthcare Dataset included information about the medical condition for each patient. We grouped our dataset by age range and then took the value_counts() of that groupby in order to see the total count per medical condition for age group. We plotted the results on a bar chart to see the relationship between medical condition count and age range (see Figure 4 below).
  
   ![alt text](https://github.com/Handro4/Bootcamp-Project1/blob/main/Images/Medical_Condition_Per_Age_Range.png) 

    The first thing we can infer from this chart is the most commonly seen medical condition per age group (18-30 Hypertension, 30-45 Hypertension, 45-60 Cancer, 60-75 Asthma, 75-90 Cancer). On the flip side of things we are also able to see the least commonly seen medical condition per age range (18-30 Arthritis, 30-45 Diabetes, 45-60 Hypertension, 60-75 Cancer, 75-90 Arthritis). Interestingly enough we can see that Cancer is the most common medical condition for the 45-60 and 75-90 age groups, but is the least common for patients in the 60-75 age range. This could be something medical researchers would want to explore further to see if they can determine why the 60-75 age group sees the smallest amount of patients for cancer.

### Analysis Question 3.C

* The fourth thing we wanted to look at was the relationship between age and medication prescribed. The Healthcare Dataset included information about the medication prescribed for each patient. We thought it would be interesting to look at the breakdown of medication prescribed per age range. To obtain the desired results we once again grouped the dataframe by Age Range and then took the value_counts() of medication. We plotted the rsults on a bar chart to see the relationship between medication and age range (see Figure 5 below).
  
   ![alt text](https://github.com/Handro4/Bootcamp-Project1/blob/main/Images/Medication_Count_Per_Age_Range.png) 

    What stands on this chart is the most commonly medication used per age range (18-30 Ibuprofein, 30-45 Pencillin, 45-60 Penicillin, 60-75 Lipitor, 75-90 Penicilin). We can see that Penicillin is probably the most commonly used medication across all age groups. We can also easily identify the least used medication per age range (18-30 Paracetamol, 30-45 Ibuprofein, 45-60 Aspirin, 60-75 Paracetamol, 75-90 Lipitor). What's interesting is that Lipitor is the most commonly used medication for patients aged 60-75, while it's the least commonly used medication in the next age range of 75-90. This could mean that Lipitor looses it's effectiveness the older a patient gets. Based on these findings hospitals will most likely want to stock up on Penicillin, and we can assume that Penicillin has the greatest effect across all age ranges. Finally, the most noticeable gap between the top medication and other medications used across the age ranges is for the 30-45 group. Hospitals could use this information to identify the best medication used per age range. There are obviously other factors that need to be taken into account before a decision is made on the medication, but age could be a contributing factor.

### Analysis Question 3.D

* Finally, we performed an analysis on the relationship between Age and the Amount Charged. For this analysis we used the Insurance Dataset as we wanted to see the effect age has on the amount the insured is actually billed not what is billed to insurance provider as is the case in the first dataset. We used a scatter plot to plot the difference ages we found in the dataset against the amount they were charged. On top of that we performed linear regression to see if we could find the correlation between age and the amount charged to potentially be able to predict what someone may be charged based on their age (see Figure 15 below).
  
   ![alt text](https://github.com/Handro4/Bootcamp-Project1/blob/main/Images/Age_vs_Amount_Charged.png) 

    Looking at the chart we can see Age plotted across the x-axis and Amount Charged plotted on the y-axis. You can see that the linear regression line is pretty flat and the r-value is roughly .30. This r-value would indicate that the correlation between Age and Amount Charged is slightly positive, but not very strong. The r-value is closer to 0 than it is 1 indicating that there is not a very strong correlation between Age and Amount Charged. This mean that as age increases there is a weak indication that the amount charged will also increase.This could be explained by there being a very large variety of amounts charged across age ranges that make it difficult to relate these two datapoints together. Regardless, it's clear that age does not have a large effect on the amount charged.

## Question 4

#### How does smoking affect billing?

### Analysis Question 4.A 

#### We wanted to analyze if smoking status would affect the billing rates to patients from their insurance provider and then validate whether the difference in billing rates had any statistical significance. 

* Using a t-test we analyzed the significance in difference in billings rates from insurance provider to patients who smoke and those who are non-smokers. 

   * We found that non-smokers on average were billed $8,434 per insurance claim.

   * We found that smokers on average were billed $32,050 per insurance claim.  

* The T-Test resulted in a pvalue=5.88946444671698e-103
  
   * We concluded that the T-Test results show enough significance to reject the Null Hypothesis and accept the Alternative Hypothesis

![alt text](https://github.com/Handro4/Bootcamp-Project1/blob/main/Images/Mean_Charges_Smoker_vs_Non-Smoker.png)

### Analysis Question 4.B 

* We wanted to further analyze billing rate trends for smokers and non-smokers by their insurance providers, and specifically if there is any variance by regions.
  
   * In earlier questions, (1.D and 2.C) we see an increase in billing rates for the southeast region of the united states. While in earlier questions we see an increase in the male population (1.B) as well as an increase in average patient BMI (2.C) as possible contributing factors for increased billing rates, in figure 14 we also see an increase in the overall smoking population in the southeast region as well.
     
   * This increase in smokers is a variable that may contribute to the higher patient billing rates we see in this region compared to the rest of the united states.

![alt text](https://github.com/Handro4/Bootcamp-Project1/blob/main/Images/Smoking_Status_Per_Region.png) 

## Conclusion

### Synthetic datasets made it difficult to find any meaningful insights in our analysis.

### Key takeaways: 

* There is a clear trend for increased billing rates among all ages and genders in the southeast region of the United States (insurance dataset).
  
   * Increased male population in the southeast may be a contributing factor to higher billing rates.
     
   * Higher average BMI in the population of the southeast region is another possible contributor to the higher billing rate trend seen throughout our analysis.
     
* Most of the patients (68%) in our dataset were between the ages of 32-71.
  
   * This could indicate people younger than 30 visit hospitals less frequently. (good health)
     
   * There are most likely less people over 75 due to lower population rates. (mortality)
     
* Most significant finding was the effect that smoking had on medical insurance charges.
  

