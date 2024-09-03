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
Data visualization is crucial in data analysis as it allows for the effective communication of complex data insights through graphical representation. Key principles of effective data visualization include:
- **Clarity:** Ensure that visualizations are easy to interpret.
- **Accuracy:** Represent data truthfully without distortion.
- **Relevance:** Use appropriate chart types for the data being presented.
- **Simplicity:** Avoid unnecessary elements that can clutter the visual.

### 2. Tableau Basics
**Main Components of Tableau:**
- **Data Connection:** Connect to various data sources.
- **Data Pane:** Manage and access data fields.
- **Shelves:** Create visualizations by dragging and dropping fields.
- **Dashboard:** Combine multiple visualizations into a single interactive view.

**Creating a Basic Dashboard:**
1. Connect to the dataset.
2. Create visualizations such as bar charts and line charts.
3. Combine these visualizations into a dashboard.
4. Add interactive elements like filters to enhance user engagement.

### 3. Power BI Fundamentals
**Main Features of Power BI:**
- **Data Import:** Import data from various sources.
- **Data Transformation:** Clean and reshape data using Power Query.
- **Visualizations:** Create reports with charts, tables, and maps.
- **Interactivity:** Add slicers and filters to enable user interactions.

**Comparison with Tableau:**
- **Integration:** Power BI integrates seamlessly with Microsoft products, while Tableau excels in advanced visualization capabilities.
- **Cost:** Power BI is generally more affordable.
- **Use Cases:** Power BI is often used for business reporting and simple dashboards, whereas Tableau is preferred for in-depth data analysis and complex visualizations.

## Practical Application

### 4. Data Cleaning and Preparation
**Script: `data_cleaning.py`**
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
