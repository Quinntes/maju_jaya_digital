# Sales Performance Analysis for Maju Jaya Digital Technology

## Background & Problem Statement

### Background

Maju Jaya Digital Technology has experienced steady sales growth, but the overall profitability and long-term revenue sustainability remain uncertain. While the company has access to raw performance data, decisions are often made without fully leveraging insights from customer behavior, product trends, and regional differences.

**Source:** [Maju Jaya Digital Technology - Project Guidelines]([https://path/to/project/guide](https://github.com/Quinntes/maju_jaya_digital/blob/main/guideline.pdf))

### Problem Statement

The objective of this analysis is to assist Maju Jaya Digital in understanding sales patterns, customer behaviors, and product performance based on the available data. The insights generated will help the management make more informed decisions regarding marketing strategies, pricing, inventory, and product management to maximize profit, strengthen competitive advantage, and build a sustainable business model.

By answering targeted business questions, the company can align its strategies and operations to enhance profitability and ensure future growth.

---

## Data Preparation

The analysis will start by cleaning and merging data from various sources to provide a comprehensive view of the company's sales performance.

### Import Libraries

```python
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
from scipy.stats import kruskal
```

| Library             | Purpose                                                                                  |
| ------------------- | ---------------------------------------------------------------------------------------- |
| `pandas`            | For data manipulation and analysis.                                                      |
| `numpy`             | For numerical operations such as calculations and data transformations.                  |
| `seaborn`           | For advanced data visualization like heatmaps and boxplots.                              |
| `matplotlib.pyplot` | For basic plotting like line charts, bar charts, etc.                                    |
| `scipy.stats`       | For statistical tests such as Kruskal-Wallis test to identify differences across groups. |

### Load Dataset

Data is sourced from Google Sheets, and contains three tables: Sales Data, Customer Data, and Product Data.

```python
# Sales Data
df_sales = pd.read_csv('https://docs.google.com/spreadsheets/d/xxxxxx/export?format=csv&gid=xxxxxx')

# Customer Data
df_customers = pd.read_csv('https://docs.google.com/spreadsheets/d/xxxxxx/export?format=csv&gid=xxxxxx')

# Product Data
df_products = pd.read_csv('https://docs.google.com/spreadsheets/d/xxxxxx/export?format=csv&gid=xxxxxx')
```

### Data Cleaning & Feature Engineering

The raw data will be cleaned by handling missing values, correcting data types, and removing duplicates. Afterward, new features such as profit per item and total sales will be created for deeper analysis.

* **Handling Missing Values**: Rows with missing critical information like customer or product ID will be removed.
* **Outlier Detection**: Outliers in the sales and pricing data will be reviewed and handled.
* **Feature Engineering**: New columns like `total_sales`, `profit_per_item`, and `total_profit` will be calculated.

```python
df['total_sales'] = df['quantity_sold'] * df['unit_price'] * (1 - df['discount'])
df['profit_per_item'] = df['unit_price'] - df['cost_price']
df['total_profit'] = df['profit_per_item'] * df['quantity_sold']
```

---

## Exploratory Data Analysis (EDA)

Key findings from the data analysis:

1. **Sales Trends**

   * A significant increase in total revenue starting from 2023, peaking in Q1 2024.
   * Total profit has grown more slowly compared to total revenue, indicating issues with margin management.

2. **Customer Behavior**

   * Millennial customers tend to purchase more compared to other generations, with a notable preference for products like laptops and PCs.
   * Gender analysis shows that women purchase more office equipment (e.g., keyboards, monitors) than men, while men focus more on PCs.

3. **Product Performance**

   * High-profit products include custom PCs and laptops. Low-profit products like keyboards and speakers contribute less to overall revenue.
   * Discounts are not significantly boosting profitability and often reduce margins.

4. **Regional Analysis**

   * Jakarta leads in both total revenue and profit, while cities like Bandung and Tangerang show lower performance.

### Visualizations

* **Sales by Product Type**

  ```python
  sns.barplot(data=product_profit, x='product_type', y='profit_per_item', palette='coolwarm')
  ```

* **Revenue and Profit by Region**

  ```python
  sns.barplot(data=city_sales_profit, x='city', y='total_revenue', palette='Blues_d')
  ```

---

## Recommendations

1. **Pricing Strategy**

   * Focus on high-margin products like custom PCs and laptops.
   * Reevaluate the discount strategy as high discounts do not correlate with improved profits.

2. **Targeted Marketing**

   * Millennials are the largest consumer group. Marketing efforts should focus on appealing to this demographic, especially for tech products.
   * Tailor products like keyboards and monitors to women in specific regions.

3. **Seasonal Trends**

   * Q4 consistently shows the highest revenue. Prepare inventory and marketing strategies to capitalize on this seasonal demand spike.
    
4. **Etc.**  

---

## Statistical Testing

* **Kruskal-Wallis Test**: Used to determine if there is a significant difference in median profits between cities.

  ```python
  stat, p = kruskal(*profit_by_city)
  ```

  Conclusion: There is a statistically significant difference in median profits between cities (p-value < 0.05).

---

## Tableau Dashboard

A detailed interactive Tableau dashboard will be provided at the end of the project, featuring visualizations like:

* Annual profit by type of goods.
* Profit and revenue by city.
* Total profit by generation.
* etc.

---

## Deliverables

1. **Jupyter Notebook**: `final_portofolio_uriel_lutfi_hezkiel.ipynb`
2. **Tableau Dashboard**: [Link to Tableau Dashboard]([https://public.tableau.com/views/sales_dashboard](https://public.tableau.com/views/MajuJayaDigital/Dashboard1?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link))

---

Let me know if you need more details or adjustments!
