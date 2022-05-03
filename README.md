# BELLABEAT-CASE-STUDY
TABLE OF CONTENT
1.	Company background
2.	Ask
2.1The business task
2.1	Key stakeholders
3.	Prepare
3.1	Data set
3.2	Accessibility and privacy
3.3	Data organization
3.4	Data credibility and integrity
4.	Process
4.1	Upload and view the data sets
4.2	 Remove duplicates
4.3	 Clean some variables
4.4	Merge the data frames
4.5	Remove unnecessary variables
5.	Analyze
6.	Share
7.	Limitations
8.	Recommendation

1.COMPANY BACKGROUND
Bellabeat is a high-tech company developing wellness tracking device for women. Bella beat was founded in 2012.  By 2016, Bellabeat launched multiple products and expanded their business globally. The products became available on their own e-commerce channel, as well as online retailers. Bellabeat focuses on digital marketing extensively, including Google Search, video ads, and consumer engagement on social media platforms.
Bellabeat has launched 5 products:
•	Bellabeat app: The Bellabeat app provides users with health data related to their activity, sleep, stress, menstrual cycle, and mindfulness habits. It helps users better understand their current habits and make healthy decisions.
•	Leaf: Bellabeat's classic wellness tracker can be worn as a bracelet, necklace, or clip. It connects to the Bellabeat app to track activity, sleep, and stress.
•	Time: This wellness watch combines the timeless look of a classic timepiece with smart technology to track user activity, sleep, and stress. It connects to the Bellabeat app to provide you with insights into your daily wellness.
•	Spring: This is a water bottle that tracks daily water intake using smart technology to ensure that you are appropriately hydrated throughout the day. It connects to the Bellabeat app to track your hydration levels.
•	Bellabeat membership: Bellabeat also offers a subscription-based membership program for users. It gives users 24/7 access to fully personalized guidance on nutrition, activity, sleep, health and beauty, and mindfulness based on their lifestyle and goals.
2. ASK
For this study, the following questions will be asked 1. What are some trends in smart device usage? 2. How could these trends apply to Bellabeat customers? 3. How could these trends help influence Bellabeat marketing strategy?
2.1	THE BUSINESS TASK
As a data analyst working on the marketing analyst team, I will analyze the data set on smart devices to gain insight into how consumers are using their smart devices and focus on one of Bellabeat’s products. By outlining the process of the analysis and the key findings, high-level recommendations for marketing strategies will be presented to the key stakeholders. In this case study, I will focus on Bellabeat App for recommendations.
2.1.1 KEY STAKE HOLDERS
•	UrškaSršen: cofounder and Chief Creative Officer.
•	Sando Mur: cofounder and a key member of the Bellabeat executive team.
•	Bellabeat marketing analytics team.
3	PREPARE 
3.1	Accessibility and privacy
The data set used for the purpose of this analysis is a public dataset that explores smart device users’ daily habits.          ● Fitbit Fitness Tracker Data (CC0: Public Domain, dataset made available through Mobius): This Kaggle data set contains personal fitness tracker from thirty Fitbit users. Thirty eligible Fitbit users consented to the submission of personal tracker data, including minute-level output for physical activity, heart rate, and sleep monitoring. It includes information about daily activity, steps, and heart rate that can be used to explore users’ habits. 
PERSONAL RESEARCH ON FITBIT
Fitbit devices use a 3-axis accelerometer to count your steps. This sensor also allows your device to determine the frequency, duration, intensity, and patterns of your movement.Fitbit devices combine your basal metabolic rate (BMR)—the rate at which you burn calories at rest to maintain vital body functions (including breathing, blood circulation, and heartbeat)—and your activity data to estimate your calories burned. Your BMR is based on the physical data you entered in to your Fitbit account (height, weight, sex, and age) and accounts for at least half the calories you burn in a day.
3.2 Data organization 
The data is available as 15 csv files, organized in both narrow and wide format, each containing different data. Entries record a unique ID, date/time, and quantitative health data. The length of time within the dataset is 31 days from 4/12/2016 to 5/9/2016.
3.3 Data credibility and integrity
The data is limited and prone to sampling bias due to the sample size of 33 users and no demographic data. Additionally, the data is 5 years old and only collected from a limited time frame of 31 days.

4. Process
4.1 What tool I’m using and why.
For the purpose of this case study and analysis I will be using SQL (Big Query) because of the volume of the data set. Sql will load and query the date for analysis and insights. I will usedata studio cloud to create the tables and charts for a well explained detailed analysis. For the visualization I will make use of power Bi.
4.2 Load and view the data set
![image](https://user-images.githubusercontent.com/104599847/166582447-d420337c-6471-4847-9567-04031f9f95d0.png)

Table Name	Type	Description
dailyActivity_merged	Microsoft Excel CSV	Daily Activity for 31 days of 33 users. Tracking daily: Steps, Distance, Intensities, Calories
dailyCalories_merged	Microsoft Excel CSV	Daily Calories for 31 days of 33 users
dailyIntensities_merged	Microsoft Excel CSV	Daily Intensity for 31 days of 33 users. Measured in Minutes and Distance, dividing groups in 4 categories: Sedentary, Lightly Active, Fairly Active, Very Active
dailySteps_merged	Microsoft Excel CSV	Daily Steps for 31 days of 33 users
heartrate_seconds_merged	Microsoft Excel CSV	Exact day and time heartrate logs for just 7 users
hourlyCalories_merged	Microsoft Excel CSV	Hourly Calories burned for 31 days of 33 users
hourlyIntensities_merged	Microsoft Excel CSV	Hourly total and average intensity for 31 days of 33 users
hourlySteps_merged	Microsoft Excel CSV	Hourly Steps for 31 days of 33 users
minuteCaloriesNarrow_merged	Microsoft Excel CSV	Calories burned every minute for 31 days of 33 users (Every minute in single row)
minuteCaloriesWide_merged	Microsoft Excel CSV	Calories burned every minute for 31 days of 33 users (Every minute in single column)
minuteIntensitiesNarrow_merged	Microsoft Excel CSV	Intensity counted by minute for 31 days of 33 users (Every minute in single row)
minuteIntensitiesWide_merged	Microsoft Excel CSV	Intensity counted by minute for 31 days of 33 users (Every minute in single column)
minuteMETsNarrow_merged	Microsoft Excel CSV	Ratio of the energy you are using in a physical activity compared to the energy you would use at rest. Counted in minutes
minuteSleep_merged	Microsoft Excel CSV	Log Sleep by Minute for 24 users for 31 days. Value column not specified
minuteStepsNarrow_merged	Microsoft Excel CSV	Steps tracked every minute for 31 days of 33 users (Every minute in single row)
minuteStepsWide_merged	Microsoft Excel CSV	Steps tracked every minute for 31 days of 33 users (Every minute in single column)
sleepDay_merged	Microsoft Excel CSV	Daily sleep logs, tracked by: Total count of sleeps a day, Total minutes, Total Time in Bed
weightLogInfo_merged	Microsoft Excel CSV	Weight track by day in Kg and Pounds for 30 days. Calculation of BMI.5 users report weight manually 3 users not iN total there are 8 users

3.3Clean the data frames
•	Clean column names
•	Remove duplicates
•	Remove missing values
•	Remove irrelevant columns
•	Make arithmetic calculations and add relevant column
![image](https://user-images.githubusercontent.com/104599847/166583122-5e4d2b1c-5745-4a1e-be78-d0a9c14a0926.png)
4. Analyze
Key findings from the daily activities of the customers.
select distinct ActivityDate, count(ID) as customer_usage
 from `bellabeat-case-study-348214.bellabeat.dailyactivity`
 group by ActivityDate 
 order by ActivityDate asc


The query above shows that not all customer made use of the smart devices on a daily basis for the 31 days. 
Every customer started but skipped some days. The table below shows the result of the query.


 
Row	ActivityDate	customer_usage
 1 	 2016-04-12 	 33 
 2 	 2016-04-13 	 33 
 3 	 2016-04-14 	 33 
 4 	 2016-04-15 	 33 
 5 	 2016-04-16 	 32 
 6 	 2016-04-17 	 32 
 7 	 2016-04-18 	 32 
 8 	 2016-04-19 	 32 
 9 	 2016-04-20 	 32 
 10 	 2016-04-21 	 32 
 11 	 2016-04-22 	 32 
 12 	 2016-04-23 	 32 
 13 	 2016-04-24 	 32 
 14 	 2016-04-25 	 32 
 15 	 2016-04-26 	 32 
 16 	 2016-04-27 	 32 
 17 	 2016-04-28 	 32 
 18 	 2016-04-29 	 32 
 19 	 2016-04-30 	 31 
 20 	 2016-05-01 	 30 
 21 	 2016-05-02 	 29 
 22 	 2016-05-03 	 29 
 23 	 2016-05-04 	 29 
 24 	 2016-05-05 	 29 
 25 	 2016-05-06 	 29 
 26 	 2016-05-07 	 29 
 27 	 2016-05-08 	 27 
 28 	 2016-05-09 	 27 
 29 	 2016-05-10 	 26 
 30 	 2016-05-11 	 24 
 31 	 2016-05-12 	 21 
 
![image](https://user-images.githubusercontent.com/104599847/166583977-dadcf7b0-ddb9-4885-bd88-18a271a55673.png)
The first four days recorded the highest number of users and the last five days recorded the least number of users.There is need for a strategy that will maintain consistency in the usage of the smart devices. Generally, the usage rate is impressive as the average usage rate is 91.97%
The query below shows the usage rate of the smart devices on each day of the 33days.

SELECT activitydate, customer_usage,round(customer_usage/33*100) as percentage_usage
FROM `bellabeat-case-study-348214.bellabeat.customerusage` 
 
Row	activitydate	customer_usage	percentage_usage
 1 	 2016-04-12 	 33 	 100.0 
 2 	 2016-04-13 	 33 	 100.0 
 3 	 2016-04-14 	 33 	 100.0 
 4 	 2016-04-15 	 33 	 100.0 
 5 	 2016-04-16 	 32 	 97.0 
 6 	 2016-04-17 	 32 	 97.0 
 7 	 2016-04-18 	 32 	 97.0 
 8 	 2016-04-19 	 32 	 97.0 
 9 	 2016-04-20 	 32 	 97.0 
 10 	 2016-04-21 	 32 	 97.0 
 11 	 2016-04-22 	 32 	 97.0 
 12 	 2016-04-23 	 32 	 97.0 
 13 	 2016-04-24 	 32 	 97.0 
 14 	 2016-04-25 	 32 	 97.0 
 15 	 2016-04-26 	 32 	 97.0 
 16 	 2016-04-27 	 32 	 97.0 
 17 	 2016-04-28 	 32 	 97.0 
 18 	 2016-04-29 	 32 	 97.0 
 19 	 2016-04-30 	 31 	 94.0 
 20 	 2016-05-01 	 30 	 91.0 
 21 	 2016-05-02 	 29 	 88.0 
 22 	 2016-05-03 	 29 	 88.0 
 23 	 2016-05-04 	 29 	 88.0 
 24 	 2016-05-05 	 29 	 88.0 
 25 	 2016-05-06 	 29 	 88.0 
 26 	 2016-05-07 	 29 	 88.0 
 27 	 2016-05-08 	 27 	 82.0 
 28 	 2016-05-09 	 27 	 82.0 
 29 	 2016-05-10 	 26 	 79.0 
 30 	 2016-05-11 	 24 	 73.0 
 31 	 2016-05-12 	 21 	 64.0 
 
The table above shows that for the 31days the rate at which the customers used the smart devices was above 50% for each day.
The query below shows the average usage rate

select round(avg(percentage_usage),2) as average_usage_rate
from
(
 SELECT activitydate,customer_usage,round(customer_usage/33*100) as percentage_usage
 FROM `bellabeat-case-study-348214.bellabeat.customerusage` 
)
Row	average_usage_rate
 1 	 91.97 

Key findings relating steps, distance, calories lost and use of the smart device
The query below calculated the total number of steps, distance, light active distance, moderately active distance, very active distance and calories for 31 days.

select id, sum(totalsteps) as id_Totalsteps, sum(totaldistance) as id_Totaldistance, sum(veryactivedistance)as veryactivedistance, 
sum(moderatelyactivedistance) as moderatelyactivedistance, sum(lightactivedistance)as lightactivedistance,
sum(calories)as calories
from
(
 select * except(LoggedActivitiesDistance)
 from `bellabeat-case-study-348214.bellabeat.dailyactivity`
 where totalsteps is not null
)
group by id
order by id_totalsteps desc, calories desc




Result of Query
Row	id	id_Totalsteps	id_Totaldistance	veryactivedistance	moderatelyactivedistance	lightactivedistance	calories
 1 	 8877689391 	 497241 	 409.59999729599997 	 205.760000234 	 10.469999980000004 	 191.84999990599997 	 106028 
 2 	 8053475328 	 457662 	 355.72999717600015 	 263.960000992 	 13.139999907 	 78.549999597 	 91320 
 3 	 1503960366 	 375619 	 242.09999895100006 	 88.61000048999999 	 24.619999751 	 128.740000485 	 56309 
 4 	 2022484408 	 352490 	 250.60999822499997 	 75.069999398000022 	 22.320000095999998 	 153.21999978600002 	 77809 
 5 	 4388161847 	 335232 	 260.190002682 	 53.299999873000004 	 27.959999812000003 	 167.280000448 	 95910 
 6 	 3977333714 	 329537 	 225.509998319 	 48.449999474000009 	 82.529999375999992 	 94.030000328 	 45410 
 7 	 6962181067 	 303639 	 204.16000080300003 	 50.110000195999994 	 29.759999798000003 	 124.05000066699999 	 61443 
 8 	 7007744171 	 294409 	 208.39999937699997 	 62.789999664000007 	 19.199999779 	 126.399999618 	 66144 
 9 	 7086361926 	 290525 	 198.02999974 	 86.220000087000031 	 23.969999946999994 	 87.379999528999988 	 79557 
 10 	 8378563200 	 270249 	 214.32000232499996 	 77.610000461000013 	 16.0899999 	 120.56999945399997 	 106534 
 11 	 5553957443 	 266990 	 174.830000951 	 45.390000017000006 	 20.740000159000004 	 108.63999897100003 	 58146 
 12 	 4702921684 	 265734 	 215.60999978400005 	 12.939999997 	 40.44999999 	 161.990001561 	 91932 
 13 	 5577150313 	 249133 	 186.39999914000003 	 93.409999671000008 	 19.740000143000003 	 72.839999675 	 100789 
 14 	 4558609924 	 238239 	 157.50000047700001 	 17.030000010000002 	 21.150000051999996 	 119.28000032800003 	 63031 
 15 	 2873212765 	 234229 	 158.14999866499997 	 20.959999957 	 8.560000002999999 	 128.450000822 	 59426 
 16 	 4319703577 	 225334 	 151.65999945799996 	 8.6200000030000012 	 15.570000006 	 116.82999878900002 	 63168 
 17 	 8583815059 	 223154 	 174.07999849 	 24.7400003 	 31.639999740000004 	 81.139999748000008 	 84693 
 18 	 1644430081 	 218489 	 158.86000061700005 	 21.900000028000004 	 28.530000056000002 	 108.27000063800003 	 84339 
 19 	 6117666160 	 197308 	 149.580001593 	 3.5899999730000003 	 2.350000024 	 135.610000371 	 63312 
 20 	 1624580081 	 178061 	 121.36000061499999 	 29.120000126 	 11.180000021999998 	 80.809999589000029 	 45984 
 21 	 2026352035 	 172573 	 107.100000177 	 0.189999998 	 0.349999994 	 106.52000025300003 	 47760 
 22 	 2347167796 	 171354 	 114.399999647 	 19.069999793999997 	 19.349999846 	 75.990000751999986 	 36782 
 23 	 6290855005 	 163837 	 123.90000033300004 	 2.480000019 	 3.720000028 	 117.41000056299998 	 75389 
 24 	 4445114986 	 148693 	 100.619999646 	 16.220000140000003 	 2.33999998 	 81.990000008999985 	 67772 
 25 	 2320127002 	 146223 	 98.819999037999992 	 3.309999984 	 3.029999971 	 92.38999956699999 	 53449 
 26 	 3372868164 	 137233 	 94.140000821999976 	 12.589999946 	 3.059999969 	 78.199999332 	 38662 
 27 	 8253242879 	 123161 	 88.6800009 	 42.069999306999996 	 13.220000058999998 	 33.340000062000009 	 33972 
 28 	 1844505072 	 79982 	 52.890000142000005 	 0.259999998 	 1.51999995 	 51.069999492000008 	 48778 
 29 	 4020332650 	 70284 	 50.410000206999996 	 4.409999892 	 4.019999922 	 40.559999540999996 	 73960 
 30 	 6775888955 	 65512 	 47.149999420000007 	 18.439999934 	 9.990000009 	 18.500000111 	 55426 
 31 	 8792009665 	 53758 	 34.409999787 	 0.72000001 	 1.690000016 	 31.999999850000002 	 56907 
 32 	 1927972279 	 28400 	 19.669999818 	 2.9699999760000004 	 0.97000001199999986 	 15.719999829000002 	 67357 
 33 	 4057192912 	 15352 	 11.450000048 	 0.209999993 	 0.25999999 	 10.75 	 7895 

 ![image](https://user-images.githubusercontent.com/104599847/166584790-9b6c898a-0e06-48fe-a61e-ca298f5c437f.png)
 ![image](https://user-images.githubusercontent.com/104599847/166584806-944d2537-3e4d-423a-bf80-46414da68d3f.png)
 ![image](https://user-images.githubusercontent.com/104599847/166584824-12e9d8be-acf6-4f5c-a12a-d08379fcf4e7.png)
 ![image](https://user-images.githubusercontent.com/104599847/166584867-8414db47-9b77-4c15-ad03-d09cddc8fed9.png), 
The above table and chart shows that increase in distance and steps leads to an increase in the number of calories burnt.


Key findings on the use of sleep smart device
The query below shows the smart device usage by the customers

select distinct SleepDay, count(ID) as customer_usage
 from `bellabeat-case-study-348214.bellabeat.sleepday`
 group by sleepday 
 order by sleepday asc


 

