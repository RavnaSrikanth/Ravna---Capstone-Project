# DataCo Supply Chain Analytics Dataset📊

<p align="center">
 <img width="266" height="205" alt="image_1e16842e_edited" src="https://github.com/user-attachments/assets/699034ae-2410-4f06-ae9d-66dd5003594f" />
</p>

<h1 align="center">DataCo Supply Chain Analytics Dataset</h1>

This repository contains a comprehensive supply chain dataset that captures end-to-end order fulfillment activities across customers, products, orders, payments, shipping operations, and global markets. The dataset supports business analytics, supply chain optimization, logistics performance evaluation, customer behavior analysis, profitability reporting, and predictive analytics.

It serves as an excellent resource for Exploratory Data Analysis (EDA), supply chain performance analysis, customer segmentation, delivery risk prediction, logistics optimization, and machine learning applications in business operations

Research Objectives
Objective 1: Customer Analysis

To analyze customer characteristics, purchasing patterns, and market segments to understand their relationship with order volume, delivery performance, and sales outcomes.

Objective 2: Product and Category Performance Analysis

To evaluate the sales and profitability performance of products, categories, and departments and identify high-performing and low-performing product groups.

Objective 3: Order Fulfillment Analysis

To examine order processing and fulfillment performance by analyzing order status, delivery status, and order completion trends.

Objective 4: Shipping Performance Analysis

To assess shipping efficiency by comparing actual shipping times with scheduled shipping times and identifying factors contributing to late deliveries.

Objective 5: Geographic and Market Analysis

To investigate variations in sales performance, profitability, and delivery outcomes across different countries, regions, cities, and markets.

Objective 6: Payment Method Analysis

To analyze payment method usage and determine whether payment types are associated with differences in order characteristics and delivery performance.

Objective 7: Profitability Analysis

To evaluate the impact of discounts, product pricing, order quantities, and shipping performance on overall profitability.

Objective 8: Late-Delivery Risk Prediction

To develop predictive models that identify orders with a high risk of late delivery using customer, product, order, shipping, payment, and geographic factors.

Objective 9: Business Recommendation Development

To provide data-driven recommendations that improve supply chain efficiency, reduce delivery delays, enhance profitability, and increase customer satisfaction.



<img width="1317" height="742" alt="image" src="https://github.com/user-attachments/assets/fd2d0b2f-b7d0-4953-8c8b-868132c2485a" />

## 📋 Dataset Overview

* **File Name:** `product_sales_practice.csv`
* **Time Horizon:** January 2026 – June 2026
* **Target Category:** Electronics
* **Key Entities:** Products, Sales Team, Regional Markets, Revenue Metrics

  Link to Jupyter Notebook in Google Colab:
  https://colab.research.google.com/drive/1zdPR2ig9qFp6Q1gPrZvky3Ac7UITW3Mv?usp=sharing
   
## 🗂️ Data Dictionary

The dataset consists of the following 10 features:

| Column Name | Data Type | Description | Example Value |
| :--- | :--- | :--- | :--- |
| **Order_ID** | String | A unique alphanumeric identifier for each transaction. | `ORD078` |
| **Date** | Date | The transaction date formatted as `YYYY-MM-DD`. | `2026-04-09` |
| **Product** | String | The name of the electronic item sold. | `Laptop`, `Mouse`, `Webcam` |
| **Category** | String | The high-level category classification. | `Electronics` |
| **Region** | String | The geographic sales territory. | `North`, `East`, `West`, `South` |
| **Salesperson** | String | The name of the account representative. | `Alice`, `Bob`, `Charlie`, `Diana`, `Ethan` |
| **Quantity** | Integer | The total units purchased in the order. | `7.0` |
| **Unit_Price** | Float | The retail price per single unit of the product. | `997.67` |
| **Discount** | Float | The promotional deduction percentage applied (0.0 to 0.15). | `0.15` (equivalent to 15%) |
| **Sales** | Float | The final calculated gross revenue earned from the order. | `6983.69` |

## 🔍 Data Quality & Cleaning Notes

If you are using this dataset for data cleaning projects, please note that it intentionally contains realistic real-world data anomalies:
* **Missing Values (NaNs):** Features like `Region`, `Salesperson`, `Unit_Price`, `Discount`, and `Sales` contain scattered missing fields (e.g., missing revenue values or unattributed regional boundaries).
* **Calculated Columns:** The `Sales` column follows the general formula:  
  \[\text{Sales} = (\text{Quantity} \times \text{Unit\_Price}) \times (1 - \text{Discount})\]
  This relationship can be exploited to programmatically restore missing metrics.
* **Empty Rows:** The raw structure contains blank structural divider rows (`,,,,,,,,,`) that should be filtered out during preprocessing.

## 🛠️ Usage Example (Python & Pandas)

Get started analyzing this dataset quickly using Python:

```python
import pandas as pd

# Load the dataset and drop completely empty structural lines
df = pd.read_csv('sales_data.csv').dropna(how='all')

# Convert date column to datetime object
df['Date'] = pd.to_datetime(df['Date'])

# Quick view of total sales revenue by product
revenue_by_product = df.groupby('Product')['Sales'].sum().sort_values(ascending=False)
print("Revenue by Product:\n", revenue_by_product)
