# marketing-analytics-bellabeat-casestudy

**Introduction**

 Bellabeat is a successful emerging company in the global smart device market. Founded by an artist Srsen, it is a high-tech company that manufactures health-focused, smart products and develops beautifully designed technology that informs and inspires women around the world. Collecting data on activity, sleep, stress and reproductive health has allowed Bellabeat to empower women with knowledge about their own health and habits. Since its emergence in 2013, Bellabeat has grown rapidly and quickly positioned itself as a tech-driven wellness company for women. Its array of product line includes:

* **Bellbeat app** : Provides users with helath data related to their activity, sleep, stress, menstrual cycle, and mindfulness habits

* **Leaf** : The classic wwellness tracker that can be worn as a bracelet, necklace, or clip. The Leaf tracker connects to the Bellabeat app to track other activity metrics

* **Time** : This wellness watch combines the timeless look of a classic timepiece with smart technology to track user activity metrics and connects with the app to provide insights into daily wellness.

* **Spring** : A water bottle that tracks daily water intake using smart technology to ensure that you are appropriately hydrated throughtout the day and also connects with the app to track hydration levels

* **Bellabeat Membership** : A subscription-based program for users that provide 24/7 access to fully personalized guidance on nutriiton, activity, sleep, health and beauty, and mindfulness based on their lifestyle and goals

**Business Task**

The founder has tasked us with analyzing usage data associated with competitive smart devices such as fitbit in order to gain insight into how people are already using their smart devices. Then, we will use this information to derive recommendations to apply to one or more products and further also use these trends to inform Bellabeat marketing strategy

**Data Sources**

[Fitbit Fitness Tracker Data](https://www.kaggle.com/datasets/arashnic/fitbit) a public domain dataset made available through [Mobius](https://www.kaggle.com/arashnic)
was used in the analysis. It contains personal fitness tracker information from thrity fitbit users. Thirty eligible Fitbit users consented to the submission of personal tracker data, including minute-level output for physical activity, heart rate, and sleep monitoring. It includes information about daily activity, steps, and heart rate that can be used to explore user's habits

**Data Cleaning and Manipulation**

**Part 1: Preliminary Analysis**

* Data pertaining to different activity metrics and daily and hourly data was available as individual tables.

* Data preparation process invloved loading in the data, viewing the column names, reformatting the column names, checking to see if common attributes across different tables have similar data format and if there are any missing values

* There was discrepency about user count across differnt tables. While most of them had 33 unique users,  sleep and weight data had 24 and 8 users respectively

* Conveted the dates from character to date format and parsed them into date and time for aggregate manipulations. 

* We also obtained summary statistics for key metrics such as daily -  sedentary minutes, total steps, calories consumed, light active minutes, fair active minutes, very active minutes, total minutes of sleep, total time in bed, MET(metobolic equivalent of task) and bmi, at the sample level as well as at the individual level

* Sleep efficiency and rest quality based on total time spend in bed and total time asleep were calculated and categorical variables were created to group indvidual based on their sleep routines

**Inital takeaways**

a. Fitness tracker usage:

While all users in our sample track metrics such as step count, distance walked, and minutes they have been active, comparatively fewer users track their sleep cycle and weight associated metrics.


b. Metrics summary:

* Average sedentary minutes is about 991 minutes which is close to 16 hours and requires reduction

* People have an average step count of 7638, which is slightly less than the CDC recommended 8000 steps to reduce all cause mortality by 50% 

* Average fairly(moderate) active minutes is about 14 minutes/day, making the weekly  recommended target of 150 - 300 minutes a far stretch

* Sleep cycle ranges form less than an hour to more than 13 hours with an average of 7 hours a day. 

* BMI values are predominantly less than the overweight cutoff with an average of 25.19 

Since most of the essential metrics for lifestyle and physical activity assessments are contained within the activity, sleep and METs table, we will merge all three using the personal id and date, to obtain daily records specific to each user

**Part 2: Exploratory Data Analysis**

* Creating new metrics

Now lets classify the overall daily activity level of a user using their active minutes across different categories - light/fair/very active.

Very active - Have >15 minutes of very active minutes and >30 minutes of moderate active minutes

Fairly active - Have either >15 minutes of very active minutes or >30 minutes of moderate active minutes

Insufficiently active - Have neither >15 minutes of very active minutes nor >30 minutes of moderate active minutes

**a. Understanding tracker usage frequency across the week**

<img src="https://github.com/Lavkar1118/AB-Testing/blob/main/Assets/hist_diff.jpeg" width="525" height="550" />

* Looks like comparatively less users wear tracker/track their daily activity between Friday - Monday.

* It might be because people are engaging less in physical activities during weekend or people do not prefer to wear their tracker during weekends.

**b. Calories metabolized vs Total steps**
