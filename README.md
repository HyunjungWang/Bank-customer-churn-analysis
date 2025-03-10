# Bank-customer-churn-analysis

This document outlines the steps involved in performing Bank Customer Churn Analysis by leveraging Power BI and Azure Cloud services.
The analysis is based on the [Bank Customer Churn dataset from Kaggle](https://www.kaggle.com/datasets/radheshyamkollipara/bank-customer-churn).

It includes steps to upload customer churn data from a CSV file into Azure Blob Storage, transfer the data to an Azure SQL Database, clean the data, and then perform customer segmentation, categorization, and data formatting in Power BI using Power Query.


Additionally, it covers the creation of visualizations and KPIs in Power BI to analyze churn patterns. Key metrics such as churn rate, average tenure, and total customers are calculated using DAX. Various charts, including Line and Stacked Column Charts, are used to display distributions, while a Churn Status Slicer allows for dynamic filtering.

Finally, actionable insights are derived from the data, helping identify factors influencing churn and enabling data-driven decision-making to improve customer retention strategies.

> **Note:** I used Azure Cloud to familiarize myself with cloud-based data processing. However, you can also directly import the data from a local CSV file into Power BI. In this project, I connected Power BI with an Azure SQL Server to import the data.


## 1. Upload CSV to Azure Blob Storage

## 2. Create Data Flow and Pipeline in Azure Data Factory
1. Create an Azure Data Factory Instance:
- Go to the Azure Portal.
- Search for Azure Data Factory and create a new instance.
2. Create Linked Services for Data Source and Destination:
- Inside Azure Data Factory, create two linked services:
- Source: Azure Blob Storage where the CSV file is stored.
- Destination: Azure SQL Database to store the processed data.
3. Create Data Flow:
- Inside Azure Data Factory, create a Data Flow to perform the data transformation.
- Configure the Source as the Blob Storage CSV file and Sink as the Azure SQL Database.
- Add the necessary column mappings for transferring data to SQL.
4. Create a Pipeline:
- Create a Pipeline in Azure Data Factory and trigger the data flow to copy data from Blob Storage to the SQL Database.
- Execute the pipeline and monitor for successful data transfer.
## 3. Clean Data in SQL Database
1. Remove Duplicates in SQL Database:
- Once the data is transferred, remove duplicate records from the SQL Database based on CustomerID.
2. Remove Null Values in SQL Database:
- Remove rows with null values in essential columns such as CustomerID, Name, MonthlyCharges, and Exited.

## 4. Data Formatting in Power BI Using Power Query
1. Open Power BI Desktop:
- Launch Power BI Desktop and connect to the Azure SQL Database to pull in the data (ChurnRecords table).

2. Apply Data Formatting in Power Query:
- Use Power Query to format and clean the data based on the required business logic. The following changes can be made in Power Query:
- Format the Active Member column to show Active or Inactive based on the values of 0 and 1.
- Format the Churn column to display Churned or Remained based on the values of 0 and 1.
- Format the Credit Card column to show Yes or No based on 1 and 0.
- Replace numeric values in the Product column (e.g., 1, 2, 3, and 4) with corresponding names like Prod 1, Prod 2, etc.

## 5. Categorize Data in Power BI Using Power Query
1. Age Grouping:
- Create an age group column by categorizing customers into predefined age ranges such as 20-30, 30-40, etc.
2. Credit Score Grouping:
- Create a credit score group column by categorizing customers into groups like Low, Medium, and High based on their credit scores.
3. Points Grouping:
- Create a points group column to categorize customers into groups such as Low, Medium, and High based on their points.



## 6. Build Visualizations and KPIs in Power BI
After cleaning and categorizing the data, use Power BI to create meaningful visualizations:
1) Customer Segmentation: Visualize customers by activity, card, products, country, and gender.
2)  Key Metrics (DAX Calculations):
- Churn Rate: Calculated using DAX to measure customer retention.
- Average Tenure: Calculated using DAX to show the average length of customer relationships.
- Total Customers: Calculated using DAX to determine the total customer count.
3) Distributions and Churn Rate: Use a Line and Stacked Column Chart to show customer distributions and churn rate.
4) Churn Status Slicer: Add a slicer to allow users to filter data by churn status (e.g., churned vs. retained customers).

![Image](https://github.com/user-attachments/assets/b6a0d881-4cb0-4018-8a17-ef62f77ca946)

## 7. Insights from Bank Customer Churn Analysis
### 1. Customer Overview

The dataset consists of 10,000 customers, out of which 2,038 have churned, leading to a churn rate of 20.38%.

The average of Tenure is 5 years old.

A Churn Status filter is applied, allowing dynamic analysis of churned vs. non-churned customers.

### 2. Customer Distribution by Key Attributes
#### - Activity Level:

51.51% of customers are active, while 48.49% are inactive.

Inactive customers have a higher churn risk, indicating potential engagement issues.

#### - Credit Card Ownership:

70.55% of customers own a credit card, while 29.45% do not.

Credit card ownership does not significantly impact churn rate.

#### - Products Purchased:

Prod 1 & Prod 2 are the most popular products, with over 5K and 4.6K users, respectively.

Prod 3 & Prod 4 have significantly fewer customers, indicating lower adoption or relevance.

#### - Geographic Distribution:

Most customers are from France (~50%), followed by Germany and Spain (25% each).

Country-specific churn analysis may reveal location-based trends.

#### - Gender Breakdown:

54.57% of customers are Male, while 45.43% are Female.

Gender distribution appears balanced, with no significant churn disparity observed.

### 3. Churn Rate Analysis by Key Factors
#### - Age Group vs. Churn:

The churn rate peaks between ages 40-49, suggesting that this segment is at higher risk.

Younger customers (<30) and older customers (>60) have lower churn rates.

#### - Credit Score vs. Churn:

Customers with a credit score between 600-799 are the largest segment, but higher churn rates occur in the 400-499 range.

Better credit scores (>800) correlate with lower churn rates.
#### - Loyalty Points vs. Churn:

Customers with 300-699 loyalty points have the highest churn rate.

Customers with 900+ points churn the least, suggesting that a strong loyalty program reduces churn.




