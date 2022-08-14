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

<img src="https://github.com/Lavkar1118/marketing-analytics-bellabeat-casestudy/blob/main/Assets/weekly_traker_usage.png" width="600" height="550" />

* Looks like comparatively less users wear tracker/track their daily activity between Friday - Monday.

* It might be because people are engaging less in physical activities during weekend or people do not prefer to wear their tracker during weekends.

**b. Calories metabolized vs Total steps**

<img src="https://github.com/Lavkar1118/marketing-analytics-bellabeat-casestudy/blob/main/Assets/calories_vs_steps_n_METs.png" width="600" height="650" />

* Compared to daily steps, METs seems to be a more reliable metric to track the association between energy spent and caloeries burnt. Allowing people to set everyday fitness level goals based on daily METs seems like a more efficient method in getting them to be more active

**c. Sleep patterns and quality**

<img src="https://github.com/Lavkar1118/marketing-analytics-bellabeat-casestudy/blob/main/Assets/sleep_quality.png" width="700" height="450" />

* While only 50% of the sample seems to be well rested with atleast 7 hours of sleep, more  than 90% of the people are efficient sleepers and spend about 85%
of their time on the bed asleep

* However, for those will less than 5 hours of sleep, efficiency does not matter as they are already poorly rested

* Inconsistencies in sleep duration and quality can be addressed with custom designed notifications and help develop a healthy routine

**d. Sleep Latency**

<img src="https://github.com/Lavkar1118/marketing-analytics-bellabeat-casestudy/blob/main/Assets/sleep_latency.png" width="600" height="450" />

* This is defined as the time a person stays awake after going to bed, i.e the differnce between total time spend in bed and the time asleep. The average sleep latency period is between 10 - 20 minutes. A sleep latency of less than 8 minutes can be a sign of increased sleepiness and may be sign of tiredness from lack of sleep.

* The average latency period in our sample is around 50 minutes and timely notifications can help people to focus on reducing the time spent using gadgets or limit other distractions that is keeping them awake


**Sleep quality and Calories metabolized**

<img src="https://github.com/Lavkar1118/marketing-analytics-bellabeat-casestudy/blob/main/Assets/calories_vs_activity.png" width="600" height="450" />

* There seems to be a positive correlation between total time slept and calories burnt for those who are moderate or very active. And, an inverse relationship is observed among those are not sufficiently active

* This emphasizes the need to focus on both sleep and active minutes through out the day to attain a healthier lifestyle


**Recommendations**

Based on the analysis of Fitbit data, we have come with three recommendations in the form of design modificaitons to the tracker and the Bellabeat App to make it a more tech focused device and increase product growth via customer satisfaction

* As the device usage reduces during weekends, Bellabeat can focus on making design improvements to ensure that the product is suited for both formal and casual attire, and can be worn all through the week. This can become a huge selling point for the device and can also increase interest among buyers. While this will allow users to track their progress in an uninteruppted manner, it will also increase the quantity and quality of data when Bellabeat intends to use them for future projects or quality assessments.

* Bellabeat can work on including additional features to the Bellabeat App to provide more knowledge, and make users more familiarized about the various metrics that can be tracked using the device. This can then be followed by emphasizing the role of tracking daily METs over daily step count to track activity level and calories metabolized. The interface can even suggest users to set daily METs target if they have a planned fitness goal to achieve.

* Sleep latency was an evident finding in our sample and given today's smart phone and social media use, its likely that its common in our population. So Bellabeat  can add design provisions to the device to make it play white noise or other soothing sounds to help users reduce sleep latency. Futher, the App can suggest customized sleep schedules based on user routine and inputs.

**Other considerations**

* While we did find some interesting trends in the data, its important to acknowledge that the data is very limited in quantity both in terms of number of participants (only 33 ) and the duration (1 month). Hence there can be potential variation or other trends if the same data was observed over a longer period of time

* Another thing to note would be that, the data did not contain any demographic information such as age, sex etc. Generalizing a data without proper knowledge of the sample might lead to potential bias and the might not completely produce the intended effects from the sample to which the changes will be applied to.

