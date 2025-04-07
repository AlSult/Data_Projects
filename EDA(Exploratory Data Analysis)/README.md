![Exploratory data analysis in Hospitality Domain](/images/0.jpg)

Data science is having a huge impact on the medical field, specifically in the area of cancer studies. In this project I will work with breast cancer data. This project focuses on data analysis using a simple step-by-step explanation.

# Table of Contents
1. [Project Overview](#ch1)
1. [EDA Definition and Steps](#ch2)
1. [Step 1: Data Gathering and Exploration](#ch3)
1. [Step 2: Head and describe](#ch4)
1. [Step 3: Target distribution](#ch5)
1. [Step 4: Features distribution](#ch6)
1. [Step 5: Correlation matrix](#ch7)
1. [Step 6: Positive correlated features](#ch8)
1. [Step 7: Uncorrelated features](#ch9)
1. [Step 8: Negative correlated features](#ch10)

1. [References](#ch90)


<a id="ch1"></a>
# Project Overview

# **Project Summary from Kaggle:**

# Attribute information:

<a id="ch3"></a>
# Step 1: Data Gathering and Exploration
We have 5 different .CSV format files and we'll explore them one by one.
```
#Read data
df_bookings = pd.read_csv('data/fact_bookings.csv')
df_bookings.head(4)
```
![Data head](./images/1.df_booking_head.png)
\images

