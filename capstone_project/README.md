# The Capstone Project

I explore Airbnb user data to glean insights and to create two models:

- exploratory_data_analysis.ipynb contains the initial cleaning and exploration of the data. 

- model_eager_users.ipynb contains a model that identifies users who are likely to make a booking, with high precision. These users are likely to make a booking anyway, so no special promotions necessary for these users. 

- model_hesitant_users.ipynb contains a model that identifies users who are NOT likely to make a booking, with high recall. These users may be targeted with special promotions in order to increase the conversion rate. 

- slides.pdf are the non-technical slides aimed at the general audience.

- final_report.pdf is the final report that describes the modeling process. 

(The two models are essentially the same, but are separated for the purpose of clearly communicating thresholding, precision and recall.)

The dataset is too large and is not included in this repository. It may be downloaded from here: https://www.kaggle.com/c/airbnb-recruiting-new-user-bookings/data 

This project was completed under the guidance of Ankit Jain. I would like to thank Ankit for all his help and suggestions.

Partha Solapurkar 
