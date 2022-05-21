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
As a data analyst working on the marketing analyst team, I will analyze the data set on smart devices to gain insight into how consumers are using their smart devices and focus on one of Bellabeat’s products. By outlining the process of the analysis and the key findings, high-level recommendations for marketing strategies will be presented to the key stakeholders. In this case study, I will focus on Bellabeat App and watch for recommendations.

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


 

 
![image](https://user-images.githubusercontent.com/104599847/166583977-dadcf7b0-ddb9-4885-bd88-18a271a55673.png)
The first four days recorded the highest number of users and the last five days recorded the least number of users.There is need for a strategy that will maintain consistency in the usage of the smart devices. Generally, the usage rate is impressive as the average usage rate is 91.97%
The query below shows the usage rate of the smart devices on each day of the 33days.

SELECT activitydate, customer_usage,round(customer_usage/33*100) as percentage_usage
FROM `bellabeat-case-study-348214.bellabeat.customerusage` 
 


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


The result of the query shows that less users make use of the sleep smart device compared to the smart device for daily activity.

 ![image](https://user-images.githubusercontent.com/104599847/169667784-44698b88-cf8b-4c84-8785-6a99206d0f0d.png)
The chart above shows that less than half of the customers made use of the smart device most of the days.  Having 14 as the number that showed up most. 


The query below joins the daily activity table and the sleep table.
select d.id, activitydate, totalsteps, totaldistance, sedentaryminutes, calories, sleepday, TotalMinutesAsleep, TotalTimeInBed
from `bellabeat-case-study-348214.bellabeat.dailyactivity` as d
inner join `bellabeat-case-study-348214.bellabeat.sleepday` as s
on d.id=s.id


The query below finds the total time awake by subtracting the total time asleep from the time in bed.
select *, (totaltimeinbed-totalminutesasleep) as totaltimeawake
from
(
 select d.id, activitydate, totalsteps, totaldistance, sedentaryminutes, calories, sleepday, TotalMinutesAsleep, TotalTimeInBed
 from `bellabeat-case-study-348214.bellabeat.dailyactivity` as d
 inner join `bellabeat-case-study-348214.bellabeat.sleepday` as s
 on d.id=s.id
)

To get the relationship between steps, distance, calories and sleep
Order by clause is added to the query
select *, (totaltimeinbed-totalminutesasleep) as totaltimeawake
from
(
 select d.id, activitydate, totalsteps, totaldistance, sedentaryminutes, calories, sleepday, TotalMinutesAsleep, TotalTimeInBed
 from `bellabeat-case-study-348214.bellabeat.dailyactivity` as d
 inner join `bellabeat-case-study-348214.bellabeat.sleepday` as s
 on d.id=s.id
) 
order by totalsteps desc, calories desc, totalminutesasleep desc

The query below calculates the average total steps, average total distance and average sleep in hour, all in two decimal places. 
select round(avg(totalsteps) as avg_steps, avg(totaldistance) as avg_distance, avg(calories) as avg_calories, avg(totalminutesasleep)/60 as avg_sleep/hr),2)
from
(

 select *, (totaltimeinbed-totalminutesasleep) as totaltimeawake
 from
 (
 select d.id, activitydate, totalsteps, totaldistance, sedentaryminutes, calories, sleepday, TotalMinutesAsleep, TotalTimeInBed
 from `bellabeat-case-study-348214.bellabeat.dailyactivity` as d
 inner join `bellabeat-case-study-348214.bellabeat.sleepday` as s
 on d.id=s.id
))

The query below joins daily activity table, sleep table and weight info table
select d.id, activitydate, totalsteps, totaldistance, sedentaryminutes, calories, sleepday, TotalMinutesAsleep/60 as sleep_hr, TotalTimeInBed,
BMI, WeightKg
from `bellabeat-case-study-348214.bellabeat. dailyactivity` as d
inner join `bellabeat-case-study-348214.bellabeat.sleepday` as s
on d.id=s.id
inner join `bellabeat-case-study-348214.bellabeat.weightloginfo` as w
on d.id=w.id


6. Share
Below is the summary of the insight gotten from the analysis 
 
![image](https://user-images.githubusercontent.com/104599847/169667851-e16c1118-0bba-4901-9040-a7f92470daff.png)


Key insights
•	Not all users fully utilized the devices/trackers. All unique users used the device for step/distance/calories tracking but wasn’t consistent throughout the 31days. 24 unique IDs used the sleep tracking function. 8 unique IDs used their devices to track their weight. And one user utilized the heartrate tracker
•	Calories are burnt by steps taken daily and co-related to distance covered
•	Frequency of spending more time asleep was found to be highest with users burning high number of calories.
•	Surprisingly, users that took light active distance spent more time asleep
•	Users that had light active burnt more calories than other users
•	A lot of users spent more of their time sedentary
•	Line graph comparing the relationship between steps and time spent asleep showed inconsistency in the positive correlation. This can be inferred to be as a result of the fact that light active distance gives a better sleep result than others




7. Limitations
The dataset is limited to just a sample size of 33 users which is very small to use in making an absolute correct data driven decision.
The time frame of just 31days is also short.
And there was no data giving information on the sex of the users from Fitbit. Bellabeat is a fitness company for women, making analysis with data gotten from male Fitbit users will give wrong decisions
The inconsistency in the data limited the insights and analysis, for example I couldn’t get the trend between heart rate and other features such as steps, calories and weight. Because just one (1) user gave information on heartrate. Analysis made from just one same is not enough to make a decision
If this was to be a personal project, and opportunity given to gather the needed data these limitations can be avoided.
 
8. Recommendations

From the analysis and insights gotten from the data set, most people prefer to use a smart device that will track steps, calories, weight and sleep. Therefore, I will recommend bellabeat company to lay emphases in the product and services of her applications, and also employ efficient strategies in marketing its product to the correct target group.

To guide bellabeat’s product offerings and marketing effort I will recommend;

Notifications: Bellabeat application should send notifications to its users at intervals, this will ensure consistency in users who would like to use the application for exercise(steps) in other to burn calories and reduce weight. There should be alerts for users when the app identifies that they are experiencing high or low heartrate, high or low weight etc. Also, there should an alert that serves as a reminder for daily activities such as sleep.

Reward for frequent and consistent users: There should be a sort of reward such as unlocking pro dashboards at a subsidized rate for users that are consistent throughout the month or year.

Introduction of other forms of exercise aside steps: This will attract not just users that want to maintain a healthy lifestyle but also users that want to lose or add weight as the routine alongside the bellabeat application products and services will keep record of their progress while recommending different workout plans and routines.

Health tips: Bellabeat app should have a section that gives health awareness and education which should also be included during marketing. Customers understanding the need to keep fit, sleep well, burn calorie and maintain a healthy weight will captivate their interest in bellabeat product offerings and will also make them to be consistent with the usage and be diligent in achieving their fitness goals. With health tips customers will spend more time active than sedentary because they understand the dangers of a sedentary lifestyle.

Referrals: Bellabeat company can introduce referral method to grow its customer base. An incentive could be awarded to users who refer people to the app. Incentives such as access to premium version of the application.



