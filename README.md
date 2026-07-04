# Task 3: Exploratory Data Analysis (EDA) using Python

## Overview

This project performs basic Exploratory Data Analysis (EDA) on the **ApexPlanet Data Analytics Dataset** using Python. The analysis includes loading the dataset, inspecting its structure, checking for missing values, generating summary statistics, and calculating total sales.

## Technologies Used

* Python
* Pandas
* Matplotlib

## Dataset

**File Name:** `ApexPlanet_DataAnalytics_Dataset.xlsx`

The dataset contains sales-related information such as:

* Order Date
* Sales Data
* Customer Information
* Product Details

## Steps Performed

### 1. Import Required Libraries

```python
import pandas as pd
import matplotlib.pyplot as plt
```

### 2. Load Dataset

The Excel file is loaded into a Pandas DataFrame.

```python
df = pd.read_excel("ApexPlanet_DataAnalytics_Dataset.xlsx")
```

### 3. Display First Five Rows

Used to understand the dataset structure.

```python
print(df.head())
```

### 4. Dataset Information

Displays column names, data types, and non-null values.

```python
print(df.info())
```

### 5. Summary Statistics

Provides statistical information such as mean, median, minimum, maximum, and standard deviation.

```python
print(df.describe())
```

### 6. Check Missing Values

Identifies null or missing values in each column.

```python
print(df.isnull().sum())
```

### 7. Convert Date Column

Converts the `Order_Date` column into datetime format.

```python
df["Order_Date"] = pd.to_datetime(df["Order_Date"])
```

### 8. Create Month Column

Extracts the month name from the order date.

```python
df["Month"] = df["Order_Date"].dt.month_name()
```

### 9. Calculate Total Sales

Calculates the overall sales value from the dataset.

```python
total_sales = df["Total_Sales"].sum()
print("Total Sales:", total_sales)
```

## Output

The program generates:

* Dataset preview
* Dataset structure information
* Statistical summary
* Missing value report
* Month-wise data preparation
* Total sales calculation

## Conclusion

This EDA project helps understand the dataset's structure and quality before performing advanced analysis or creating business intelligence dashboards in tools such as Power BI.

# KPI Analysis and Sales Distribution Visualization

## Overview

This project calculates key business performance indicators (KPIs) and visualizes sales distribution across different cities using Python, Pandas, and Matplotlib.

## Technologies Used

* Python
* Pandas
* Matplotlib

## Objectives

* Calculate Total Sales
* Calculate Total Orders
* Visualize Sales Distribution by City
* Generate business insights from sales data

## KPI Calculations

### Total Sales

Calculates the sum of all sales values in the dataset.

```python
total_sales = df['Total_Sales'].sum()
```

### Total Orders

Calculates the number of unique orders.

```python
total_orders = df['Order_ID'].nunique()
```

### Display KPI Summary

```python
print("===== KPI SUMMARY =====")
print("Total Sales :", total_sales)
print("Total Orders:", total_orders)
```

## Sales Distribution by City

The dataset is grouped by city, and total sales for each city are calculated.

```python
city_sales = df.groupby('City')['Total_Sales'].sum()
```

### Pie Chart Visualization

A pie chart is created to show the percentage contribution of each city to overall sales.

```python
plt.figure(figsize=(6,6))
city_sales.plot(
    kind='pie',
    autopct='%1.1f%%'
)
plt.title("Sales Distribution by City")
plt.ylabel("")
plt.tight_layout()
plt.show()
```

## Output

### KPI Summary

Displays:

* Total Sales
* Total Orders

### Pie Chart

Shows:

* Sales contribution of each city
* Percentage share of total sales
* Easy comparison of city-wise performance

## Business Insights

* Identifies cities generating the highest sales.
* Helps understand market distribution across locations.
* Supports decision-making for regional sales strategies.

## Conclusion

This analysis provides a quick overview of business performance through KPIs and a visual representation of sales distribution by city. It serves as a foundation for deeper sales and regional performance analysis.


# Sales Analysis by Category

## Overview

This project analyzes sales performance across different product categories and visualizes the results using a bar chart. The chart helps identify which categories generate the highest and lowest sales.

## Technologies Used

* Python
* Pandas
* Matplotlib

## Objective

To calculate total sales for each product category and display the results in a bar chart for easy comparison.

## Code Explanation

### 1. Group Data by Category

The dataset is grouped based on the `Category` column, and total sales are calculated for each category.

```python
category_sales = df.groupby('Category')['Total_Sales'].sum()
```

### 2. Create Bar Chart

A bar chart is generated to visualize category-wise sales.

```python
plt.figure(figsize=(7,5))
category_sales.plot(kind='bar')
```

### 3. Add Chart Labels and Title

Chart elements are added to improve readability.

```python
plt.title("Total Sales by Category")
plt.xlabel("Category")
plt.ylabel("Sales")
```

### 4. Rotate Category Labels

Rotates x-axis labels to prevent overlapping.

```python
plt.xticks(rotation=45)
```

### 5. Display Chart

Adjusts layout and displays the chart.

```python
plt.tight_layout()
plt.show()
```

## Output

The program generates a bar chart showing:

* Product Categories on the X-axis
* Total Sales on the Y-axis
* Comparison of sales performance across categories

## Business Insights

* Identifies top-performing product categories.
* Highlights categories with lower sales.
* Supports inventory and marketing decisions.
* Helps businesses focus on profitable product segments.

## Conclusion

The category-wise sales analysis provides a clear understanding of product performance. The bar chart makes it easy to compare sales across categories and uncover valuable business insights.


# Sales Distribution by Gender (Donut Chart)

## Overview

This analysis visualizes the distribution of total sales across different genders using a donut chart. The chart helps understand the contribution of each gender segment to overall sales.

## Technologies Used

* Python
* Pandas
* Matplotlib

## Objective

To calculate total sales by gender and present the results in a donut chart for better visualization of sales distribution.

## Code Explanation

### 1. Group Data by Gender

The dataset is grouped by the `Gender` column, and total sales are calculated for each gender.

```python
gender_sales = df.groupby('Gender')['Total_Sales'].sum()
```

### 2. Create Pie Chart

A pie chart is generated to show the percentage share of sales by gender.

```python
plt.figure(figsize=(5,5))
plt.pie(
    gender_sales,
    labels=gender_sales.index,
    autopct='%1.1f%%'
)
```

### 3. Create Donut Hole

A white circle is added to the center of the pie chart to convert it into a donut chart.

```python
centre_circle = plt.Circle((0,0), 0.70, fc='white')
fig = plt.gcf()
fig.gca().add_artist(centre_circle)
```

### 4. Add Title and Display Chart

The chart title is added and the visualization is displayed.

```python
plt.title("Sales Distribution by Gender")
plt.tight_layout()
plt.show()
```

## Output

The program generates a donut chart showing:

* Gender categories
* Percentage contribution of each gender
* Overall sales distribution

## Business Insights

* Identifies which gender segment contributes more to sales.
* Helps businesses understand customer demographics.
* Supports targeted marketing and promotional strategies.
* Assists in customer segmentation analysis.

## Conclusion

The donut chart provides a clear and visually appealing representation of gender-wise sales distribution. It helps businesses analyze customer purchasing patterns and make informed marketing decisions.


# Monthly Sales Trend Analysis

## Overview

This project analyzes sales performance over time by calculating monthly sales totals and visualizing them using a line chart. The visualization helps identify sales trends, growth patterns, and seasonal fluctuations.

## Technologies Used

* Python
* Pandas
* Matplotlib

## Objective

To analyze monthly sales performance and display sales trends over time using a line chart.

## Code Explanation

### 1. Convert Order Date to Datetime

The `Order_Date` column is converted into datetime format to enable time-based analysis.

```python
df['Order_Date'] = pd.to_datetime(df['Order_Date'])
```

### 2. Calculate Monthly Sales

The data is grouped by month, and total sales are calculated for each month.

```python
monthly_sales = df.groupby(
    df['Order_Date'].dt.to_period('M')
)['Total_Sales'].sum()
```

### 3. Convert Period Index to String

The monthly period values are converted to strings for better display on the chart.

```python
monthly_sales.index = monthly_sales.index.astype(str)
```

### 4. Create Line Chart

A line chart is generated to visualize sales trends over time.

```python
plt.figure(figsize=(8,5))
monthly_sales.plot(kind='line', marker='o')
```

### 5. Add Labels and Title

Chart labels and title are added for better readability.

```python
plt.title("Monthly Sales Trend")
plt.xlabel("Month")
plt.ylabel("Sales")
```

### 6. Add Grid and Display Chart

A grid is added to improve trend visibility, and the chart is displayed.

```python
plt.grid(True)
plt.tight_layout()
plt.show()
```

## Output
The program generates a line chart showing:
* Months on the X-axis
* Total Sales on the Y-axis
* Sales growth and decline patterns over time

## Business Insights
* Identifies high-performing and low-performing months.
* Detects seasonal sales trends.
* Helps forecast future sales performance.
* Supports strategic business planning and decision-making.

## Conclusion
The Monthly Sales Trend Analysis provides valuable insights into how sales change over time. The line chart makes it easy to track performance, identify trends, and support data-driven business decisions.

