<!-- Heading -->
<h1 align="center">🚗Electric Vehicle Market Segmentation Analysis with Python </h1>

<!-- Image upload -->
<div align="center">
    <img src="https://github.com/user-attachments/assets/a64c87a6-e576-4a07-bbf8-244c19423df9" width="600" height="450" />
</div>

## Table of Contents
1. [Introduction](#introduction)
   1. [Overview](#overview)
   2. [Objectives](#objectives)
2. [Business Problem / Stakeholder Concerns](#business-problem--stakeholder-concerns)
3. [Importing Libraries](#importing-libraries)
4. [Data Loading](#data-loading)
5. [Generating Comprehensive Data Profile Report Using Pandas Profiling](#generating-comprehensive-data-profile-report-using-pandas-profiling)
6. [Methodology](#methodology)
   1. [Data Collection](#data-collection)
   2. [Data Cleaning](#data-cleaning)
   3. [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
   4. [Outlier Detection to All Numerical Columns and Handling](#outlier-detection-to-all-numerical-columns-and-handling)
   5. [Checking or Ensuring Final Cleaned Dataset](#checking-or-ensuring-final-cleaned-dataset)
7. [Analysis](#analysis)
   1. [EV Growth Trends Over Time](#ev-growth-trends-over-time)
   2. [Regional Registration Patterns](#regional-registration-patterns)
   3. [EV Category Breakdown](#ev-category-breakdown)
   4. [Brand and Model Analysis](#brand-and-model-analysis)
   5. [Electric Range Trends](#electric-range-trends)
   6. [Market Size Growth](#market-size-growth)
8. [Conclusion or Summary](#conclusion-or-summary)


## Introduction

### Overview
The "Electric Vehicles Market Size Analysis using Python" project focuses on exploring the rapidly expanding electric vehicle (EV) market, a key area of interest due to increasing environmental concerns, regulatory pressures, and consumer demand for sustainable transportation. This analysis aims to provide valuable insights into the market's current state, trends in EV adoption, geographical distribution, and the popularity of different EV models. By leveraging data analysis techniques, the project seeks to uncover the drivers of growth in the EV market and assess its future potential, offering strategic insights for stakeholders.


### Objectives
The objectives of the analysis include tracking the growth of electric vehicle (EV) registrations over time to understand how the market is expanding. It involves identifying regional patterns to pinpoint areas with the highest density of EV registrations. The analysis will segment the data by different types of electric vehicles, such as Battery Electric Vehicles (BEVs) and Plug-in Hybrid Electric Vehicles (PHEVs), to provide insights into the distribution of vehicle categories. Additionally, it aims to determine the most popular brands and models within the EV market. Evaluating the electric range trends will help in understanding technological advancements while estimating the future growth of the EV market will offer insights into its potential trajectory.



## Business Problem / Stakeholder Concerns
The aim is to analyze the market size of electric vehicles (EVs) in Washington State (WA). The insights will help stakeholders understand the distribution, trends, and demographics of EV ownership, and identify key factors influencing the adoption of EVs. The ultimate goal is to provide actionable insights for policymakers, automotive companies, and utility providers to support and enhance the growth of the EV market.

| **Main Challenges**                       | **Description**                                                                                                                                                   |
|-------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Tracking EV Growth Trends**             | Monitoring the increase in EV registrations over the years to understand market dynamics and growth patterns.                                                      |
| **Identifying Regional Registration Patterns** | Determining regions with the highest density of EV registrations to tailor regional marketing strategies and distribution efforts.                                 |
| **Segmenting EV Categories**              | Breaking down the data by types of electric vehicles (e.g., BEVs, PHEVs) to identify market preferences and trends.                                                 |
| **Analyzing Brands and Models**           | Assessing the popularity of various EV brands and models to optimize product offerings and competitive positioning.                                                 |
| **Evaluating Electric Range Trends**      | Investigating advancements in electric vehicle range to understand technological progress and consumer demands.                                                    |
| **Estimating Market Size Growth**         | Projecting future growth of the EV market for strategic planning and investment decisions.                                                                         |


## Importing Libraries
To begin the analysis, we first need to import the necessary Python libraries for data manipulation, analysis, and visualization.


```python
  from ydata_profiling import ProfileReport
  import pandas as pd
  import numpy as np
  import matplotlib.pyplot as plt
  import seaborn as sns
```

## Data Loading

First, we load the dataset containing information on electric vehicles:

```python
# Importing the necessary library
import pandas as pd

# Loading the dataset
ev_data = pd.read_csv("Electric_Vehicle_Population_Data.csv")

# Displaying the column names
ev_data.columns
```

####  **Electric Vehicles Population Data** 📊

Explore the dataset detailing various aspects of electric vehicles registered in the United States. This analysis focuses on the information provided for each vehicle.

### **Dataset Columns**

| **Column Name**                     | **Description** |
|-------------------------------------|-----------------|
| **VIN (1-10)**                      | Partial Vehicle Identification Number. |
| **County**                          | The county where the vehicle is registered. |
| **City**                            | The city where the vehicle is registered. |
| **State**                           | The state where the vehicle is registered. It appears that this dataset may focus on Washington (WA) state. |
| **Postal Code**                     | The postal code where the vehicle is registered. |
| **Model Year**                      | The year of the vehicle model. |
| **Make**                            | The manufacturer of the vehicle. |
| **Model**                           | The model of the vehicle. |
| **Electric Vehicle Type**           | The type of electric vehicle, e.g., Battery Electric Vehicle (BEV). |
| **CAFV Eligibility**                | Eligibility status for clean alternative fuel vehicle programs. |
| **Electric Range**                  | The maximum range of the vehicle on a single charge (in miles). |
| **Base MSRP**                       | The Manufacturer’s Suggested Retail Price. |
| **Legislative District**            | The legislative district where the vehicle is registered. |
| **DOL Vehicle ID**                  | Department of Licensing Vehicle Identification. |
| **Vehicle Location**                | Geographic coordinates of the vehicle's location. |
| **Electric Utility**                | The electric utility service provider for the vehicle’s location. |
| **2020 Census Tract**               | The census tract for the vehicle's location. |



**Get Started:** Dive into the data and explore the insights that will shape the future of electric vehicles. For detailed analysis and visualizations, refer to the [project notebook](link-to-your-notebook).

---

Feel free to explore and contribute to the ongoing analysis!


##  Generating Comprehensive Data Profile Report Using Pandas Profiling

The comprehensive data profiling report for the Electric Vehicle Population dataset has been generated using Pandas Profiling. This report provides a detailed overview of the dataset, including statistics, missing values, correlations, and more.

#### 📈 **Profiling Report**

You can view the profiling report directly within the notebook or download it as an HTML file.

#### **Interactive Report in Notebook**

Below is the interactive report embedded in the notebook:

```python
from pandas_profiling import ProfileReport

# Generate the profiling report
profile = ProfileReport(ev_data, title="Electric Vehicle Population Data Profiling Report", explorative=True)

# Display the report in the notebook
profile.to_notebook_iframe()


