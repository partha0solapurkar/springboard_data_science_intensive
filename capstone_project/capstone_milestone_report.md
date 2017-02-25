# Capstone Milestone Report

This report accompanies the exploratory data analysis notebook. 

### Introduction
The dataset used is the Airbnb new user bookings dataset available from https://www.kaggle.com/c/airbnb-recruiting-new-user-bookings/data. An initial exploration shows that roughly 60 percent of the users create an account, but do not make a booking. The goal is to work with the marketing team at Airbnb in order to develop strategies to lower this number. 

### The Dataset
The dataset contains two tables, one table about user information and another table about user activity. The first table, the `train_users` table, contains information about each user account such as the user id, the date on which the account was created, the date of the first booking if the user made a booking, gender, age, signup method, language, marketing affiliate channel, signup app, signup device, browser and the country where the user made their first booking. The second table, the `sessions` table, contains user activity information such as clicks, views and so on. Not every user in the `train_users` table is present in the `sessions` table, and not every user in the `sessions` table is present in the `train_users` table. There are no repeated users in the `train_users` table, but for each user there are multiple entries in the `sessions` table. Every user in the `sessions` table is a user who signed up in `2014`, but `train_users` includes users from `2009` through mid-`2014`.

### The `train_users` table
Most freatures in the `train_users` table are categorical features. The only numerical feature is `age`. There is also some timestamp information regarding when the users created their accounts. 

A number of `first_affiliate_tracked` values are missing from the `train_users` table. A large number of `first_affiliate_tracked` values are present, but nondescriptive. This indicated that something strange may be going on with the tracking mechanisms. 

A number of `age` values are missing from the `train_users` table, but this is likely due to people choosing to withhold that information. A surprisingly large number of people have age values between 100 and 120. This indicates some problem with data collection such as non-sanitized forms or data collected in ways that are incompatible across platforms. There are also some age values that are birth years such as 1948. It would be a good idea to implement a drop down menu rather than a text field for `age`.

Roughly 60% of the users make no booking at all, roughly 30% of the users make their first booking in the USA and roughly 10% of the users make their first booking in a country other than the USA. 

A number of users choose not to divulge their `age` and their `gender`. Among such people, the conversion rate is notoriously low - 22% as opposed to 52% for the users who inform us about their `age` and their `gender`. Perhaps these users are very concerned about their privacy. It would be a good idea to target them with messages reassuring them regarding their privacy. 

### The `sessions` table
The `sessions` table contains information about user activity. Information such as clicks and views and time associated with each action may be seen here. A lot of these values are missing. It would be a good idea to record the user activity with more details. 