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


## Outlier Detection to All Numerical Columns and Handling

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

### Checking or Ensuring Final Cleaned Dataset

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

## Analysis
#### Data Visualization and Analysis for Electric Vehicles Market Size Analysis

To comprehensively analyze the market size of electric vehicles (EVs), we can investigate the following aspects:

| Analysis Aspect                      | Description                                                                                           |
|-------------------------------------|-------------------------------------------------------------------------------------------------------|
| **EV Growth Trends Over Time**      | Track the increase in EV registrations by model year. This analysis helps us understand the growth trajectory of the EV market and identify any significant trends or shifts in adoption over the years. |
| **Regional Registration Patterns**  | Identify areas with the highest density of EV registrations. This can reveal geographic patterns and regions where EV adoption is particularly high, which may be influenced by local policies or infrastructure. |
| **EV Category Breakdown**           | Segment the data by types of electric vehicles (e.g., Battery Electric Vehicles (BEV), Plug-in Hybrid Electric Vehicles (PHEV)). This breakdown provides insight into the different types of EVs in the market and their relative popularity. |
| **Brand and Model Analysis**        | Determine the most popular brands and models in the EV market. Analyzing this data helps to identify leading players in the market and consumer preferences for specific brands and models. |
| **Electric Range Trends**           | Evaluate the range of electric vehicles to understand advancements in technology. This analysis helps in assessing how the range of EVs has improved over time and its impact on market adoption. |
| **Estimated Growth in Market Size** | Project the future expansion and market potential of electric vehicles based on current trends. Estimating future growth helps in understanding the potential scale of the market and planning for long-term strategies. |

Each of these aspects provides valuable insights into different facets of the electric vehicle market, helping stakeholders make informed decisions and strategies.


### EV Growth Trends Over Time
Start by analyzing how the number of electric vehicles (EVs) registered has changed over different model years. By visualizing this data, we can understand the growth patterns and trends in EV adoption.

Below is the line plot showing the trend of EV adoption over time:

```plaintext
import matplotlib.pyplot as plt

# Ensure plots are rendered inline
%matplotlib inline

yearly_adoption=df_filtered['Model Year'].value_counts().sort_index()

# Visualize the trend
plt.figure(figsize=(10, 6))
yearly_adoption.plot(kind='line', marker='o', color='c', linestyle='-', linewidth=2, markersize=8)  # Customize color and style
plt.title('EV Adoption Over Time')
plt.xlabel('Model Year')
plt.ylabel('Number of EVs Registered')
plt.grid(True)

# Adding an additional color for markers
plt.scatter(yearly_adoption.index,yearly_adoption,color='m',s=100,zorder=5)
plt.show()
```

![image](https://github.com/user-attachments/assets/025dcaeb-5026-4c68-aea8-0f3e05214ad2)
The line chart illustrates a clear upward trend in EV registrations, especially from 2011 onwards. Early registrations were very low, with just 1 in 1997 and 9 in 2000. Starting in 2011, there was a significant increase, with numbers rising to 807. The growth became more pronounced from 2016, reaching 5.3K and peaking at 13.7K in 2018. The highest point was in 2022 with 27.9K registrations. In 2023, there was a slight decline to 22.5K, though the overall trend remains positive. The 2024 figure of 30 suggests preliminary or incomplete data. Overall, the chart demonstrates a strong growth trajectory in EV adoption over the years.

### Regional Registration Patterns
Examine the geographical distribution of EV registrations to identify which areas have the highest density of electric vehicles. This will highlight regional trends and preferences in EV adoption.

```plaintext
import matplotlib.pyplot as plt
import seaborn as sns

# Number of EVs by city
city_dist = df_filtered['City'].value_counts()

# Select the top 10 cities
top_10_cities = city_dist.head(10).index

# Filter the DataFrame to include only the top 10 cities
filtered_df = df_filtered[df_filtered['City'].isin(top_10_cities)]

# Create a pivot table for the heatmap
heatmap_data = filtered_df.groupby(['County', 'City']).size().unstack(fill_value=0)

# Plot heatmap
plt.figure(figsize=(12, 10))
sns.heatmap(heatmap_data, cmap='YlGnBu', annot=True, fmt='d', linewidths=0.5)
plt.title('Heatmap of Number of EVs by County for Top 10 Cities')
plt.xlabel('City')
plt.ylabel('County')
plt.xticks(rotation=45, ha='right')  # Rotate labels for better readability
plt.yticks(rotation=0)  # Keep y-axis labels horizontal
plt.show()
```
![image](https://github.com/user-attachments/assets/db0e399e-481c-4603-8640-0320cd2b0bb2)

### Heatmap Analysis of EV Registrations in Various Cities

#### Key Findings:

1. **King County Dominance:**
   - **Seattle** has the highest number of EV registrations by a significant margin, with **22,907** EVs.
   - **Bellevue** (6,757), **Kirkland** (4,076), and **Redmond** (4,850) follow Seattle with the next highest registrations.
   - Other cities within King County, such as **Sammamish** (3,848) and **Olympia** (3,433), show moderate EV registrations.

2. **Clark County:**
   - **Vancouver** has a substantial number of EVs (**4,714**), making it a notable city for EV adoption within Clark County.

3. **Snohomish County:**
   - **Everett** shows a considerable number of EVs (**3,255**), indicating it as a key area for EVs within Snohomish County.

4. **Pierce County:**
   - **Tacoma** shows a smaller but noticeable count of EVs (**2,764**), indicating moderate EV adoption.

5. **Thurston County:**
   - **Olympia** has a noteworthy count of EVs (**3,156**), making it a significant city for EV adoption within Thurston County.

6. **Sparse EV Presence:**
   - Many cities within these counties have either zero or very low counts of EVs, suggesting that EV adoption is not uniformly distributed and is heavily concentrated in certain areas.

7. **Implications for EV Market Analysis:**
   - The majority of cities shown are from King County, which dominates EV registrations among the counties.
   - EV adoption is not uniform across the cities and is more concentrated in certain areas, particularly in King County.

**Overall Analysis:**
   - EV adoption is significantly higher in King County, particularly in Seattle, with other counties like Clark and Snohomish showing significant numbers in specific cities. This distribution highlights the concentration of EV registrations in urban and suburban areas, with rural or less populated areas having lower adoption rates.

###  EV Category Breakdown
Analyze the distribution of different types of electric vehicles within the dataset to understand which types are most common. This will provide insights into the market share of each EV category.

```plaintext
# Count the number of each type of EV
ev_count=df_filtered.groupby(['Electric Vehicle Type']).size()

# Plotting a pie chart 
plt.figure(figsize=(8,5))
plt.pie(ev_count,labels=ev_count.index,autopct='%1.1f%%',startangle=90)
plt.title('Distribution of EV Types')
plt.show()
```
![image](https://github.com/user-attachments/assets/8c386575-a275-4ff8-a3b4-ec4059022231)
In the United States, the distribution of electric vehicles reveals a strong preference for Battery Electric Vehicles (BEVs), which constitute 77.3% of the total EVs registered. BEVs, known for their exclusive reliance on electric power, are leading the market, indicating a significant shift towards fully electric transportation. Meanwhile, Plug-in Hybrid Electric Vehicles (PHEVs) represent 22.7% of the EV registrations.PHEVs, which combine electric propulsion with a traditional gasoline engine, remain an important segment, catering to drivers who value the flexibility of dual power sources. This distribution underscores the growing adoption of BEVs while highlighting the continued relevance of PHEVs in the evolving landscape of electric mobility.

### Brand and Model Analysis:
Let’s now focus on the popularity of electric vehicle manufacturers and models among the registered vehicles. This analysis will help us identify which manufacturers and specific models dominate the EV market, potentially indicating consumer preferences, brand loyalty, and the success of various manufacturers’ strategies in promoting electric mobility.

So, let’s have a look at the most popular manufacturers and then drill down into the most popular models within those manufacturers:


```plaintext
# analyzing the popularity of EV manufacturers
brand_count=df_filtered['Make'].value_counts().head(10)  # Limiting to top 10 for clarity

# Plotting top 10 brands
sns.barplot(x=brand_count.values,y=brand_count.index, palette='viridis')
plt.title('Top 10 Electric Vehicle Brands by Registration')
plt.xlabel('Number of Vehicles Registrations')
plt.ylabel('Brand')
plt.show()
```
![image](https://github.com/user-attachments/assets/38de0396-e647-468f-ade6-4823f79a8928)
The chart reveals that TESLA dominates the market with the highest number of registered vehicles, far surpassing all other manufacturers. NISSAN ranks second in popularity, with CHEVROLET in third place, though both have notably fewer registrations compared to TESLA. Following these, FORD, BMW, KIA, TOYOTA, VOLKSWAGEN, VOLVO, and AUDI are listed in descending order based on the number of registered vehicles.

**Next, let’s drill down into the most popular models within these top manufacturers to get a more detailed understanding of consumer preferences at the model level:**

```plaintext
# Selecting the top 3 manufacturers based on the number of vehicles registered
top_3_makes = brand_count.head(3).index

# Filtering the dataset for these top manufacturers
top_makes_data = df_filtered[df_filtered['Make'].isin(top_3_makes)]

# Analyzing the popularity of EV models within these top manufacturers
ev_model_distribution_top_makes = top_makes_data.groupby(['Make', 'Model']).size().sort_values(ascending=False).reset_index(name='Number of Vehicles')

# Visualizing the top 10 models across these manufacturers for clarity
top_models = ev_model_distribution_top_makes.head(10)
plt.figure(figsize=(12, 8))
sns.barplot(x='Number of Vehicles', y='Model', hue='Make', data=top_models, palette="viridis")
plt.title('Top 10 Models in Top 3 Manufacturers by EV Registrations')
plt.xlabel('Number of Vehicles Registered')
plt.ylabel('Model')
plt.legend(title='Manufacturer', loc='center right')
plt.tight_layout()
plt.show()
```
![image](https://github.com/user-attachments/assets/c73dfd4e-90d9-47e7-baa1-00d1ab5219f2)

The above graph shows the distribution of electric vehicle registrations among different models from the top three manufacturers: TESLA, NISSAN, and CHEVROLET. Here are the findings:

- **TESLA’s Model Y and Model 3** are the most registered vehicles, with **Model Y** having the highest number of registrations.
- **NISSAN’s Leaf** is the third most registered model and the most registered non-TESLA vehicle.
- **TESLA’s Model S and Model X** also have a significant number of registrations.
- **CHEVROLET’s Bolt EV and Volt** are the next in the ranking with considerable registrations, followed by **Bolt EUV**.
- **NISSAN’s Ariya** and **CHEVROLET’s Spark** have the least number of registrations among the models shown.

### Electric Range Trends:
Next, we’ll explore the electric range of vehicles, which is a critical factor for analyzing the market size of electric vehicles. The electric range indicates how far an EV can travel on a single charge, and advancements in battery technology have been steadily increasing these ranges over the years. So, let’s look at the distribution of electric ranges in the dataset and identify any notable trends, such as improvements over time or variations between different vehicle types or manufacturers:


```plaintext
# Plotting the distribution of electric ranges
plt.figure(figsize=(10,6))
sns.histplot(df_filtered['Electric Range'],bins=30,kde=True,color='Blue')
plt.title('Distribution of Electric Ranges')
plt.xlabel('Electric Range (miles)')
plt.ylabel('Frequency')
plt.axvline(df_filtered['Electric Range'].mean(),color='red',linestyle='--',label=f'Mean Range:{df_filtered['Electric Range'].mean():.2f} miles')
plt.legend()
plt.tight_layout()
plt.show()
```
![image](https://github.com/user-attachments/assets/be7b38dc-a30b-4ce5-ac06-4d3607ea9347)

**The above graph shows the mean electric range. Key observations from the graph include:**

- There is a high frequency of vehicles with a low electric range, peaking just before **50 miles**.
- The distribution is right-skewed, with a long tail extending towards higher ranges, although vehicles with higher ranges are much less frequent.
- The **mean electric range** for this set of vehicles is approximately **73.31 miles**.
- Despite the presence of EVs with ranges up to around **350 miles**, the majority of vehicles have a range below the mean.
- The data suggests that while high-range EVs are available, the market is still dominated by vehicles with shorter ranges.
- The average range is skewed lower due to a substantial number of vehicles with shorter ranges.

```plaintext
  # calculating the average electric range by model year
avg_electric_range=df_filtered.groupby('Model Year')['Electric Range'].mean()

# Visualize the trend of electric ranges over model years
plt.figure(figsize=(12,5))
avg_electric_range.plot(kind='line',marker='o',color='b',linestyle='-',linewidth=2,markersize=8)
plt.title('Trend of Electric Ranges Over Model Years')
plt.xlabel('Model Year')
plt.ylabel('Average Electric Range (Miles)')
plt.grid(True)

# Adding an additional color for markers
plt.scatter(avg_electric_range.index,avg_electric_range,color='r',s=100,zorder=5)
plt.show()
```

![image](https://github.com/user-attachments/assets/bc8a1abd-3033-45b1-a227-870cc32de542)

The above graph shows the progression of the average electric range of vehicles from around the year 2000 to 2024. Key findings from the graph:

- The average electric range of EVs shows a general upward trend from 2000 to 2024, indicating technological advancements.

- The peak in average range occurs around 2020, representing the highest point in the data.
  
- After 2020, there is a sharp decline in the average range, possibly due to incomplete data or the introduction of lower-range models.
  
- A slight recovery in the average range is observed in the most recent year.
  
Despite some fluctuations, the overall trend over the last two decades reflects significant progress in increasing the electric range of EVs.


```plaintext
# Group the data by Model and Calculate the average electric range 
model_avg_range=df_filtered.groupby(['Make','Model'])['Electric Range'].mean()

# sort the models by average electric range in descending orders and select the top 10
top_10_models=model_avg_range.sort_values(ascending=False).reset_index().head(10)
top_10_models

# Visualize the top 10 models with a bar chart
plt.figure(figsize=(12,8))
barplot = sns.barplot(x='Electric Range', y='Model', hue='Make', data=top_10_models, palette="cool")
plt.title('Top 10 Models by Average Electric Range in Top Makes') 
plt.title('Top 10 Models with the Highest Average Electric Range')
plt.xlabel('Average Electric Range (Miles)')
plt.ylabel('Model')

plt.grid(True,linestyle='--',alpha=0.6)
plt.show()
```
![image](https://github.com/user-attachments/assets/21451040-c251-4b44-b5d7-6b7e2355e0f2)

### Top 10 Electric Vehicle Models with Highest Average Electric Range

#### Key Insights:

- **Hyundai KONAleads** the chart with the highest average electric range, showcasing Hyundai's strong focus on delivering long-range EVs.
- **Jaguar I-PACE** follows closely, indicating Jaguar's commitment to combining luxury with high-performance electric capabilities.
- **Tesla** is a major player, with three of its models (**Model S**, **Model X**, and **Model 3**) ranking among the top, reflecting Tesla's industry leadership in producing EVs with extended ranges.
- **Chevrolet Bolt EV** also makes a strong showing, highlighting its position as a competitive option in the affordable EV market.
- **Audi E-TRON** and **Volkswagen E-GOLF** represent the German automakers, indicating their strategic push into the electric vehicle space with models offering substantial electric ranges.
- The presence of **Toyota RAV4** and **TH!NK CITY** in the top 10 underscores the diversity in the market, with different brands offering varied models to meet consumer demands for longer-range electric vehicles.
- The bar chart not only underscores the prominence of certain automakers in the EV market but also highlights the strides made in improving the electric range across different models. This visualization effectively communicates how different manufacturers are contributing to the evolution of electric vehicles, with a clear focus on enhancing battery technology and range capabilities.

### Market Size Growth
#### Estimated Market Size Analysis of Electric Vehicles in the United States
Now, let’s move forward towards finding the estimated market size of electric vehicles in the United States. I’ll first count the number of EVs registered every year:

```
# calculate the number of EVs registered each year
ev_registration_counts = ev_data['Model Year'].value_counts().sort_index()
ev_registration_counts
```
We’ll calculate the Compound Annual Growth Rate (CAGR) between a recent year with complete data (2023) and an earlier year to project the 2024 figures. Additionally, using this growth rate, we can estimate the market size for the next five years. Let’s proceed with these calculations:

```

filtered_years = ev_registration_counts[ev_registration_counts.index <= 2023]

# Define a function for exponential growth to fit the data
def exp_growth(x, a, b):
    return a * np.exp(b * x)

# Prepare the data for curve fitting
x_data = filtered_years.index - filtered_years.index.min()  # Normalize years
y_data = filtered_years.values

# Fit the data to the exponential growth function
params, covariance = curve_fit(exp_growth, x_data, y_data)

# Use the fitted function to forecast the number of EVs for 2024 and the next five years
forecast_years = np.arange(2024, 2024 + 6) - filtered_years.index.min()  # Normalize forecast years
forecasted_values = exp_growth(forecast_years, *params)

# Create a dictionary to display the forecasted values for easier interpretation
forecasted_evs = dict(zip(forecast_years + filtered_years.index.min(), forecasted_values))

print(forecasted_evs)

```
Now, let’s plot the estimated market size data:

```
# Combine current and forecasted data
all_years = np.concatenate([filtered_years.index, forecast_years + filtered_years.index.min()])
all_values = np.concatenate([filtered_years.values, forecasted_values])

# Create DataFrame for visualization
market_df = pd.DataFrame({
    'Year': all_years,
    'Estimated EV Registrations': all_values
})

# Plot current and forecasted data
plt.figure(figsize=(10, 6))
plt.plot(filtered_years.index, filtered_years.values, 'o-', label='Current Data', color='blue')
plt.plot(forecast_years + filtered_years.index.min(), forecasted_values, 's--', label='Forecasted Data', color='red')
plt.xlabel('Year')
plt.ylabel('Estimated EV Registrations')
plt.title('Current & Estimated EV Market')
plt.legend()
plt.grid(True)
plt.show()
```
![image](https://github.com/user-attachments/assets/3d9bfbb8-6b44-4667-bbdb-329827d82be9)

**From the above graph, we can see:**

- The number of actual EV registrations remained relatively low and stable until around 2010, after which there was a consistent and steep upward trend, suggesting a significant increase in EV adoption.
  
- The forecasted EV registrations predict an even more dramatic increase in the near future, with the number of registrations expected to rise sharply in the coming years.
Given the rising trend in EV registrations and the exciting forecast data, it's clear that the EV market is set to grow significantly. The dramatic increase in predicted registrations shows that more and more people are embracing electric vehicles, and this trend is expected to continue. Overall, the data suggest a bright future for the EV industry, with a major shift in consumer preferences and a wealth of new investment and business opportunities on the horizon.


### Conclusion or Summary
Market size analysis plays a vital role in market research by estimating the potential sales volume within a specific market. It allows businesses to gauge demand, evaluate market saturation, and pinpoint growth opportunities. Our analysis of the electric vehicle market reveals a bright future, marked by a significant shift in consumer preferences and the potential for increased investment and business prospects.

I hope you found this article on Electric Vehicles market size analysis using Python insightful.

**Thank you for your interest and time. Feel free to give your valuable suggestions and connect with me**   
https://www.linkedin.com/in/goutam-kuiri-949b632a6
