# Table of Contents
1. [Project Overview](#ch1)
1. [Step 1: Data Exploration and Cleaning](#ch3)
1. [Step 2: Data Transformation](#ch4)
1. [Step 3: Data Insights](#ch5)

<a id="ch1"></a>
# Project Overview
On this project the data from different booking websites is represented. 
I performed a comprehensive data analysis for AtliQ Grands using Python.
# **Project Summary:**
AtliQ Grands is a prominent hospitality group operating a chain of five-star hotels across major Indian cities, 
including Delhi, Mumbai, Hyderabad, and Bangalore. With over 20 years in the industry, the company offers 
a diverse portfolio of properties such as AtliQ Seasons, AtliQ Exotica, AtliQ Bay, and AtliQ Palace.
# Attribute information:

<a id="ch3"></a>
# Step 1: Data Exploration and Cleaning
We have 5 different .CSV format files and we'll explore them one by one. 
Using the example of the fact_booking.csv dataset, I demonstrated the process of data exploration and cleaning. 
The handling and analysis of the other datasets are detailed in the accompanying code file. 
```
#Read data
df_bookings = pd.read_csv('data/fact_bookings.csv')
df_bookings.head()
```
![Data head](./images/1.df_booking_head.png)


I inspected several issues. 'no_guests' column has error values, in our case on the table below we can see the -17.000, but number of guests cannot be zero or less than zero, it has to be a positive number. Furthermore, the 'revenue_generated' column has some issues as well.

```
#quick statistics on the numeric columns in this particular data frame
df_bookings.describe()
```
![Data describe](./images/2.df_booking_describe.png)

Checking the negative values of 'no_guests' column gave me around 10 rows which can be ignored in this particular case as the total records number is 134590.
```
#checking how many negative values are in the column no_guests
df_bookings[df_bookings.no_guests<=0]
```
![Data cleaning](./images/3.df_booking_no_guests_negative.png)

After checking the highest and the lowest revenues for the single booking, the maximum value looks not realistic as the number is so big.
```
#checking the revenue_generated column
df_bookings.revenue_generated.min(), df_bookings.revenue_generated.max()
```
![Data cleaning](./images/4.df_booking_revenue.png)

For fixing the outlier issues I am using the standard deviation to detect the lower and higher limits. 
On the table below we can see all the huge numbers for the 'revenue_generated' column which is non-realistic, 
because no one will pay that much for one-night stay.
```
#if the value is more than this it's considered as an outlier
higher_limit = avg + 3*std
higher_limit

#checking the negative values to detect the higher_limits
df_bookings[df_bookings.revenue_generated>higher_limit]
```
![Data cleaning](./images/5.df_booking_higher_limit.png)

Below I checked the total null values in the dataset and only the 'ratings_given' column has such values. 
In this case I didn't assume this as the error because in reality not every single guest is leaving a rating.
```
#handling NA values
df_bookings.isnull().sum()
```
![Data cleaning](./images/6.df_bookings_NA.png)

<a id="ch4"></a>
# Step 2: Data Transformation
In this step, I demonstrated how I added an additional column for occupancy percentage using the 
fact_aggregated_bookings.csv dataset. 
The occupancy percentage was calculated by dividing the number of successful bookings by the total capacity.
```
#new column for the occupancy percentage
df_agg_bookings.loc[:, 'occ_pct'] = df_agg_bookings['successful_bookings'] / df_agg_bookings['capacity']

#occupancy in percent form
df_agg_bookings.loc[:, 'occ_pct'] = df_agg_bookings['occ_pct'].apply(lambda x: round(x*100, 2))
df_agg_bookings.head(3)
```
![Data transformation](./images/7.occ_ptg.png)

<a id="ch5"></a>
# Step 3: Data Insights
![Data insights](./images/8.booking count.png)
![Data insights](./images/9.avg_occ_rate.png)
![Data insights](./images/10.avg_room_occ.png)
![Data insights](./images/11.avg_occ_daytype.png)
![Data insights](./images/12.occ_trends_byweek.png)
![Data insights](./images/13.occ_daytype.png)
![Data insights](./images/14.total_capacity.png)
![Data insights](./images/correlation matrix.png)