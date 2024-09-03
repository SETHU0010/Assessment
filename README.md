# Data Analyst Assessment

## Objective
This repository contains solutions for the Data Analyst role assessment, focusing on data analysis, visualization, and reporting using Python, Tableau, and Power BI.

## Table of Contents
1. [Theoretical Knowledge](#theoretical-knowledge)
2. [Practical Application](#practical-application)
   - [Data Cleaning and Preparation](#data-cleaning-and-preparation)
   - [Tableau Visualization](#tableau-visualization)
   - [Power BI Report](#power-bi-report)
3. [Advanced Analytics](#advanced-analytics)
   - [Statistical Analysis](#statistical-analysis)
   - [Predictive Analytics](#predictive-analytics)
4. [Scenario-Based Questions](#scenario-based-questions)

## Theoretical Knowledge

### 1. Understanding Data Visualization
Data visualization is crucial in data analysis as it helps to interpret complex data sets through graphical representation. Effective data visualization principles include:
- **Clarity:** Make sure the visualizations are easy to understand.
- **Accuracy:** Represent the data accurately without distortion.
- **Relevance:** Use the right type of chart for the data being presented.
- **Simplicity:** Avoid clutter and focus on key insights.

### 2. Tableau Basics
**Main Components:**
- **Data Connection:** Connect to various data sources.
- **Data Pane:** Manage dimensions and measures.
- **Shelves:** Drag and drop fields to create visualizations.
- **Dashboard:** Combine multiple visualizations into an interactive dashboard.

**Creating a Basic Dashboard:**
1. Connect to the dataset.
2. Drag relevant fields to create visualizations (e.g., bar charts, line charts).
3. Combine these visualizations into a dashboard.
4. Add interactivity using filters and actions.

### 3. Power BI Fundamentals
**Main Features:**
- **Data Import:** Connect and import data from various sources.
- **Data Transformation:** Clean and transform data using Power Query.
- **Visualizations:** Create reports using different visualizations like charts and maps.
- **Interactivity:** Add slicers and filters to make reports interactive.

**Comparison with Tableau:**
- **Integration:** Power BI integrates well with Microsoft tools, while Tableau offers more advanced visualization capabilities.
- **Cost:** Power BI is generally more cost-effective.
- **Use Cases:** Power BI is often used for business reporting, while Tableau is preferred for more complex data visualizations.

## Practical Application

### 4. Data Cleaning and Preparation
The data cleaning script is provided in `data_cleaning.py`. It includes:
- Loading the dataset.
- Handling missing values by filling with mode (for categorical) or median (for numeric).
- Standardizing categorical values.
- Removing duplicates.
- Saving the cleaned dataset.

```python
import pandas as pd

# Load dataset
data = pd.read_csv('dataset.csv')

# Display initial data
print("Initial Data:")
print(data.head())

# Handling missing values
for column in data.columns:
    if data[column].dtype == 'object':  # Categorical column
        data[column] = data[column].fillna(data[column].mode()[0])
    else:  # Numeric column
        data[column] = data[column].fillna(data[column].median())

# Handling inconsistencies
if 'Category' in data.columns:
    data['Category'] = data['Category'].str.lower().str.strip()

# Check for duplicates and remove them
data = data.drop_duplicates()

# Display cleaned data
print("Cleaned Data:")
print(data.head())

# Save cleaned data
data.to_csv('cleaned_dataset.csv', index=False)
