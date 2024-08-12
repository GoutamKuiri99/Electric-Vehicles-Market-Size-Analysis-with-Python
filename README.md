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
   1. [Data Cleaning](#data-cleaning)
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
```
## Methodology
### Data Cleaning

**(i) Identifying Missing Values**

In this step, we identify missing values in the dataset. Below is the summary of missing values in each column:

```python
# Identifying missing values
missing_values = ev_data.isnull().sum()
print("Missing values in each column:\n", missing_values)
```


**Missing Values Summary:**

| Column                                               | Missing Values |
|------------------------------------------------------|-----------------|
| VIN (1-10)                                           | 0               |
| County                                               | 8               |
| City                                                 | 8               |
| State                                                | 0               |
| Postal Code                                          | 8               |
| Model Year                                           | 0               |
| Make                                                 | 0               |
| Model                                                | 249             |
| Electric Vehicle Type                                | 0               |
| Clean Alternative Fuel Vehicle (CAFV) Eligibility    | 0               |
| Electric Range                                       | 1               |
| Base MSRP                                            | 1               |
| Legislative District                                | 312             |
| DOL Vehicle ID                                       | 0               |
| Vehicle Location                                    | 10              |
| Electric Utility                                     | 8               |
| 2020 Census Tract                                    | 8               |

This table provides a clear view of the number of missing values for each column in the dataset.

 **2. Handling Missing Values**

 **Strategy: Impute with Mode or Common Value**

For categorical columns with missing values, we fill in the missing values using the mode (most frequent value) for each column. This approach ensures that the imputation is based on the most common category, which helps maintain data consistency.

**Example: Imputing Missing Values in 'County' Column**

First, we identify the mode for the 'County' column:

```python
# Calculate mode for the 'County' column
mode_county = ev_data["County"].mode()[0]
```
### Verifying Missing Value Handling

After applying the appropriate strategies to handle missing values, it's important to verify that all missing values have been successfully addressed. We can check this by using the `.isnull().sum()` function, which returns the count of missing values in each column.

```python
# Verify missing values in the dataset
ev_data.isnull().sum()
```

After handling the missing values, the following table shows the count of missing values in each column:

| Column Name                                          | Missing Values |
|------------------------------------------------------|----------------|
| VIN (1-10)                                           | 0              |
| County                                               | 0              |
| City                                                 | 0              |
| State                                                | 0              |
| Postal Code                                          | 0              |
| Model Year                                           | 0              |
| Make                                                 | 0              |
| Model                                                | 0              |
| Electric Vehicle Type                                | 0              |
| Clean Alternative Fuel Vehicle (CAFV) Eligibility    | 0              |
| Electric Range                                       | 0              |
| Base MSRP                                            | 0              |
| Legislative District                                 | 0              |
| DOL Vehicle ID                                       | 0              |
| Vehicle Location                                     | 0              |
| Electric Utility                                     | 0              |
| 2020 Census Tract                                    | 0              |

All columns now have `0` missing values, indicating that the missing value handling process was successful.

## Outlier Detection and Handling for Numerical Columns

Outliers in numerical columns can significantly skew the results of any analysis, so it's essential to detect and handle them appropriately. We use the Interquartile Range (IQR) method to identify and count outliers in the numerical columns of our dataset.

### Methodology: IQR Method for Outlier Detection

The IQR method calculates the range between the 1st quartile (Q1) and the 3rd quartile (Q3) of the data. Outliers are defined as data points that fall below `Q1 - 1.5 * IQR` or above `Q3 + 1.5 * IQR`.

### Python Code for Outlier Detection

Below is the Python code used to detect and count outliers in numerical columns using the IQR method:

```python
import pandas as pd

# Function to handle outliers using the IQR method and return the count of outliers
def count_outliers_iqr(df, column):
    data = df[column]
    Q1 = data.quantile(0.25)
    Q3 = data.quantile(0.75)
    IQR = Q3 - Q1

    # Define outlier bounds
    lower_bound = Q1 - 1.5 * IQR
    upper_bound = Q3 + 1.5 * IQR

    # Identify outliers
    outliers = df[(data < lower_bound) | (data > upper_bound)]
    
    return len(outliers)

# List of numerical columns to process
numerical_columns = ['Model Year', 'Electric Range', 'Base MSRP', 'Legislative District', 'DOL Vehicle ID', '2020 Census Tract']

# Initialize a dictionary to store the count of outliers for each column
outliers_count = {}

# Count outliers for each numerical column
for col in numerical_columns:
    outliers_count[col] = count_outliers_iqr(ev_data, col)

# Print outliers count for each column
print("Outliers count for each column:")
for col, count in outliers_count.items():
    print(f"{col}: {count}")

# Calculate the total number of outliers across all columns
total_outliers = sum(outliers_count.values())
print(f"\nTotal number of outliers across all columns: {total_outliers}")
```

### Outliers Count

The table below shows the count of outliers for each numerical column:

| Column Name               | Outliers Count |
|---------------------------|----------------|
| Model Year                | 876            |
| Electric Range            | 0              |
| Base MSRP                 | 3425           |
| Legislative District      | 0              |
| DOL Vehicle ID            | 14122          |
| 2020 Census Tract         | 343            |

### Total Outliers

The total number of outliers across all columns is **18,766**.

### Conclusion

Handling outliers is crucial to maintaining the quality and reliability of the data. By identifying and managing outliers, we ensure that the dataset is clean and the results of any subsequent analysis are accurate and meaningful.
