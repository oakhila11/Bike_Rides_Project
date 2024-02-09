# Case study: How does a bike-share navigate speedy success? </br> (Capstone project of the Google Data Analytics Professional Certificate)
## Table of Contents
## Summary
Data processing and analyzing will primary occur in RStudio using the R programming language with supplement visualizations done via Tableau.
## Introduction
This case study is a part of my Google Data Analytics Certification. I work with an imaginary comapny called Cyclistic for this project. With training concentrated on essential analytical abilities (data cleansing, analysis, and visualisation) and technologies (R Programming, Tableau), the programme equips learners for a career in data analytics. I used the 6 basic steps (ASK, PREPARE,PROCESS,ANALYSE,SHARE,ACT) to complete this capstone project.
#### Scenario
In this scenario, I are a junior data analyst working on the marketing analyst team at Cyclistic, a bike-share company in Chicago. The director of marketing believes the company’s future success depends on maximizing the number of annual memberships. This is why, the team wants to understand how the member and the casual riders of the company use their bikes differently. From these insights, your team will design a new marketing strategy to convert casual riders into annual members. </br>
All details for this project can be found [here](https://d3c33hcgiwev3.cloudfront.net/33sjlhw5SEKkX5eNNAa-cQ_5ac6ed67e08943078d4fd97e2fdfa5f1_V2-FOR-PDF_C8M2L2R2_Reading_Case-Study-1_-How-does-a-bike-share-navigate-speedy-success_.pdf?Expires=1707609600&Signature=fWwd7AXtRYk5BNBI3gSF5QZl9HmUAjk6LtZnSVCbCi9VDN0~GIb2RFTq5Uz6GQJV0JUAa8D31KXTlNdbmzflGtV6F-MaLJO4fWzPnOpswi9dXtnmM92uqdDssunE1TeIbithkuIZpPFzzV8e4vf~XaWXOSsnqJdNh1zJ4wlUGBI_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)
#### About the company
In 2016, Cyclistic launched a successful bike-share offering. Since then, the program has grown to a fleet of 5,824 bicycles that are geotracked and locked into a network of 692 stations across Chicago. The bikes can be unlocked from one station and returned to any other station in the system anytime.

## Tools and Techniques used
The analysis made use of the following tools and techniques:
- R programming language and libraries; ggplot2, tibble, tidyr, readr, purrr, dplyr, stringr, lubridate and forcats </br>
- Data transformations: joins, visualizations, summary statistics </br>
- Data inspection: removal of duplicate/unnessary data, change format/datatype, verify unique values </br>

## ASK (Guiding Question)
The designated business task is to look into any usage discrepancies between annual members and casual riders in the bike share data. The Cyclistic marketing team will be informed of the insights obtained. The marketing director wants to increase the number of yearly subscriptions by creating focused advertising efforts to turn casual riders into yearly members. </br>
Essentially, we have to identify the behavior of the annual members and the casual riders and highlight the difference between their usage.

## PREPARE
- The data used for this project is publically available [here](https://divvy-tripdata.s3.amazonaws.com/index.html) provided by Motivate International, Inc. under [this](https://divvybikes.com/data-license-agreement) license. </br>
- The dataset provided is updated monthly. For my project here, I used the data spanning from January 2022 to December 2022 (1 year). </br>
- Since the company collected their own data as a first party, the credibility is high and it has a very low chance of getting biased. This data is reliable, original, comprehensive, current, and cited, therefore it has ROCCC. </br>
- Verifing the integrity of data : The dataset I used in this analysis is consistent as column names and data types are not varied. </br>
#### Data Description
The data contains the following columns: </br>
1. ride_id (categorical): Unique number assigned to a ride trip.
2. rideable_type (categorical): Type of bike used during trip; standard two-wheel bike, reclining bike, hand tricycle, or cargo bike.
3. started_at (datetime): Start date and time for the trip
4. ended_at (datetime): End data and time for the trip
5. start_station_name (categorical): Name of the station where the trip started
6. start_station_id (categorical): Unique identification code assigned to the start station.
7. end_station_name (categorical): Name of the station where the trip ended.
8. end_station_id (categorical): Unique identification code assigned to the end station.
9. start_lat (numeric): Latitude coordinate of where the trip started.
10. start_lng (numeric): Longitude coordinate of where the trip started.
11. end_lat (numeric): Latitude coordinate of where the trip ended.
12. end_lng (numeric): Longitude coordinate of where the trip ended.
13. member_casual (categorical): Customer type; “member” = annual member, “casual” = casual rider.
#### Limitations of the data provided
Some information has been classified to protect users' privacy. This specifically means that it is not possible to know if casual passengers reside in the service area or have purchased several single passes, or to link credit card numbers to previous transactions. This causes the inability to determine the number of unique riders the company has.
#### Combining 12 months data
The data provided was added onto RStudio and was combined into one huge dataset sent using <b>rbind</b> and was renamed as <b>bike_rides</b> </br>
![image](https://github.com/oakhila11/Bike_Rides_Project/assets/159274121/b3e606aa-0a28-4e8f-808b-f5711fd7f791)

## PROCESS 
- The data provided to us is raw and unclean. In this step the data is cleaned and formatted to make it ready for instant calculations. </br>
- After any changes or manipulation to the dataset, I always checked the columns and data types of them to ensure the consistency. This ensures integrity of data.
#### Installing all the libraries

#### Cleaning and Formatting the data
- The RStudio packages <b>janitor</b> and <b>lubridate</b> are used here.
- Janitor is a simple Tools for Examining and Cleaning Dirty Data. It is used to remove all empty firlds in our dirty data.
- Lubridate makes it easier to work with dates and times. Here, it is used to easily pull month, and time for our calculations.
![image](https://github.com/oakhila11/Bike_Rides_Project/assets/159274121/2cffdbdf-7b8f-4ec0-b56f-065376997120)
#### Add Columns for Date, Weekday name, Ride Length, Start hour, End hour, Month and Convert Ride Length from Factor to Numeric
![image](https://github.com/oakhila11/Bike_Rides_Project/assets/159274121/fec59fe9-4a91-40fd-851a-fd82c6239814)
![image](https://github.com/oakhila11/Bike_Rides_Project/assets/159274121/66ef9bd9-9212-4a02-b1a7-661aa31cad66)
![image](https://github.com/oakhila11/Bike_Rides_Project/assets/159274121/4538ccb2-eb40-4f0c-9405-a9b8044a19a2)
![image](https://github.com/oakhila11/Bike_Rides_Project/assets/159274121/53678592-1298-47f9-8b38-7de3c8b0ca0f)
#### Remove “bad” data
This removes all the negative values and the extra coloumns </br>
![image](https://github.com/oakhila11/Bike_Rides_Project/assets/159274121/73ea8760-e6cb-43ec-a20c-bf3612ada2c9)
#### Inspect the new data frame
[IMAGE]



