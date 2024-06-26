# PRODIGY_DS_01
# Data Science Internship Task 01 at Prodigy Infotech Company - Histogram/Bar chart Analysis

This repository contains the first task of my data science internship at Prodigy Infotech Company. The task involves analyzing a dataset and visualizing key insights using Python.

## Table of Contents

- [Introduction](#introduction)
- [Installation](#installation)
- [Dataset](#dataset)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Visualizations](#visualizations)
- [Code and Analysis](#code-and-analysis)
- [Conclusion](#conclusion)
- [Acknowledgements](#acknowledgements)

## Introduction

This project is part of my data science internship at Prodigy Company. The task focuses on analyzing population data from the World Bank and visualizing the trends over the years for different countries.

## Installation

To run the notebook and perform the analysis, you need to install the following Python libraries:

- pandas
- matplotlib
- seaborn

You can install these libraries using pip:

```bash
pip install pandas matplotlib seaborn
```

## Dataset
The dataset used in this project is sourced from the World Bank and contains population data for various countries from 1960 to 2020.

 -  Source: World Bank
 -  File: API_SP.POP.TOTL_DS2_en_csv_v2_498834.csv
 -  Description: The dataset includes population data for different countries from the year 1960 to 2020. It contains columns like Country Name, Country Code, Indicator Name, Indicator Code, and yearly population values.

## Exploratory Data Analysis
The notebook includes steps to load and explore the dataset. Key steps include:

 - 1. Loading the dataset using pandas.
 - 2. Displaying the first few rows to understand its structure.
 - 3. Cleaning and preprocessing the data.

## Visualizations
Several visualizations are created to analyze the population trends:

 - Line plots showing the population growth of different countries.
 - Bar charts comparing the population of the top 5 most populous countries.
 - Heatmaps to visualize the population distribution across different years.

## Code and Analysis
Below is an excerpt of the code used for analysis and visualizations:

```bash
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

file = '/content/API_SP.POP.TOTL_DS2_en_csv_v2_498834.csv'
df = pd.read_csv(file, skiprows=4, encoding='ISO-8859-1')

# Display the first few rows of the dataframe
print(df.head())

# Basic statistics of the dataset
print(df.describe())

# Line plot of population growth
plt.figure(figsize=(10, 6))
for country in ['China', 'India', 'United States', 'Indonesia', 'Brazil']:
    plt.plot(df['Year'], df[country], label=country)
plt.xlabel('Year')
plt.ylabel('Population')
plt.title('Population Growth Over Time')
plt.legend()
plt.show()

# Bar chart of the population of top 5 countries in the latest year
latest_year = df['Year'].max()
top_countries = df.loc[df['Year'] == latest_year, ['Country Name', 'Value']].sort_values(by='Value', ascending=False).head(5)
plt.figure(figsize=(10, 6))
sns.barplot(x='Country Name', y='Value', data=top_countries)
plt.xlabel('Country')
plt.ylabel('Population')
plt.title('Top 5 Most Populous Countries in ' + str(latest_year))
plt.show()

# Heatmap of population distribution
plt.figure(figsize=(12, 8))
heatmap_data = df.pivot('Country Name', 'Year', 'Value')
sns.heatmap(heatmap_data, cmap='YlGnBu', cbar_kws={'label': 'Population'})
plt.xlabel('Year')
plt.ylabel('Country')
plt.title('Population Distribution Across Years')
plt.show()
```
## Conclusion
The analysis provides insights into how the population has changed over the years for various countries. The visualizations help in understanding the trends and identifying significant patterns. For instance, we observe consistent population growth in countries like China and India, while the population growth in developed countries like the United States shows a slower rate.

## Acknowledgements
I would like to thank Prodigy Company for providing this opportunity to work on real-world data and enhance my data science skills.

You can copy this content into your `README.md` file in your GitHub repository to provide a detailed and comprehensive overview of your project.





