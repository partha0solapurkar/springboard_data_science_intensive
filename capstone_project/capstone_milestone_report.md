# Capstone Milestone Report

This report accompanies the exploratory data analysis notebook located at https://github.com/partha0solapurkar/springboard_data_science_intensive/blob/master/capstone_project/exploratory_data_analysis.ipynb

### Introduction
The dataset used is the Airbnb new user bookings dataset available from https://www.kaggle.com/c/airbnb-recruiting-new-user-bookings/data. An initial exploration shows that roughly 60 percent of the users create an account, but do not make a booking. The goal is to work with the marketing team at Airbnb in order to develop strategies to lower this number. 

### The Dataset
The dataset contains two tables, one table about user information and another table about user activity. The first table, the `train_users` table, contains information about each user account such as the user id, the date on which the account was created, the date of the first booking if the user made a booking, gender, age, signup method, language, marketing affiliate channel, signup app, signup device, browser and the country where the user made their first booking. The second table, the `sessions` table, contains user activity information such as clicks, views and so on. Not every user in the `train_users` table is present in the `sessions` table, and not every user in the `sessions` table is present in the `train_users` table. There are no repeated users in the `train_users` table, but for each user there are multiple entries in the `sessions` table. Every user in the `sessions` table is a user who signed up in `2014`, but `train_users` includes users from `2009` through mid-`2014`.

### The `train_users` table
Most features in the `train_users` table are categorical features. The only numerical feature is `age`. There is also some timestamp information regarding when the users created their accounts, and when the user made their first booking, if the user made a booking. All the timestamp information was converted into features that are more convenient for analysis, such as `year`, `month`, `dayofweek`, `quarter` and `hour`. `signup_flow` appears to have numerical values, but it is the page from which the user signs up. This was converted into a categorical feature. 

A number of `first_affiliate_tracked` values are missing from the `train_users` table. A large number of `first_affiliate_tracked` values are present, but nondescriptive. This indicates that something strange may be going on with the tracking mechanisms. 

A number of `age` values are missing from the `train_users` table, but this is likely due to people choosing to withhold that information. A surprisingly large number of people have age values between 100 and 120. This indicates some problem with data collection such as non-sanitized forms or data collected in ways that are incompatible across platforms. There are also some age values that are birth years such as 1948. It would be a good idea to implement a drop down menu rather than a text field for `age`. 

Since most of the features are categorical, five-year age buckets are created to keep track of the rough age group as a categorical feature as opposed to the actual age as a numerical feature. The users with a missing age value are assigned age bucket `0.0` in order to not lose the information, and then their age was assigned to the mean age of all the users. This ensures that the information about missing age values is not lost, while also having a numerical age feature with the most likely age value filled in for missing age values. 

Roughly 58% of the users make no booking at all, roughly 29% of the users make their first booking in the USA and roughly 13% of the users make their first booking in a country other than the USA. 

A number of users choose not to divulge their `age` and their `gender`. Among such people, the conversion rate is notoriously low - 22% as opposed to 52% for the users who inform us about their `age` and their `gender`. Perhaps these users are very concerned about their privacy. It would be a good idea to target them with messages reassuring them regarding their privacy. 

The age group of people who are around age 30 and those who are around age 65-70 have the higest conversion rate. No particular reason to offer promotions to such users. There are significant number of middle aged users around ages 40-55 who have somewhat lower conversion rate. It would be a good idea to offer more promotions to this group of people.

People really like traveling when it's warm at their destination. This suggests that promotions should be offered in winter, but in spring and summer, it's a good idea to just send out emails without any discounts. 

### The `sessions` table
The `sessions` table contains information about user activity. Information such as clicks and views and time associated with each action may be seen here. A lot of these values are missing. It would be a good idea to record the user activity with more details.

Users spend up to 20 days on the website after creating an account, but the number of days spent starts to fall off very fast after the first day. The conversion rate for the users who spend at least five days is significantly higher than the number of users who spend less than five days. It is possible that some users simply forget about the service. It would be a good idea to email the users twice or thrice in the first week after they create an account. 