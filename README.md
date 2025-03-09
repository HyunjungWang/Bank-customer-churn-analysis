# Bank-customer-churn-analysis

This document outlines the steps involved in performing Bank Customer Churn Analysis by leveraging Power BI and Azure Cloud services. It includes steps to upload customer churn data from a CSV file into Azure Blob Storage, transfer the data to an Azure SQL Database, clean the data, and then perform customer segmentation, categorization, and data formatting in Power BI using Power Query.

## 1. Upload CSV to Azure Blob Storage
1. Create an Azure Blob Storage Container:

- Go to the Azure Portal.
- Navigate to Storage Accounts and select your account.
- Create a new Blob Container in your storage account for storing the CSV file.
2. Upload CSV File to Blob Storage:
- In your Blob Container, click Upload.
- Select and upload the CSV file that contains customer churn data to Azure Blob Storage.

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



## Step 6: Build Visualizations and KPIs in Power BI
Create Visualizations:

After cleaning and categorizing the data, use Power BI to create visualizations:
Churn Rate: Show the churn rate as a percentage of customers who left versus total customers.
Age Group Distribution: Create a pie chart to display the distribution of customers in different age groups.
Credit Score Distribution: Use bar charts to show the breakdown of customers by credit score.
Churn vs Tenure: Visualize how churn correlates with customer tenure (duration).
Add KPIs:

Use the following KPIs in Power BI to show the performance metrics:
Churned Customers: Count the number of customers who have exited.
Average Age: Display the average age of customers.
Average Tenure: Show the average customer tenure in the bank.



Conclusion
This process covers the entire workflow for Bank Customer Churn Analysis using Azure Cloud and Power BI:

Data Upload: CSV data is uploaded to Azure Blob Storage.
Data Transfer: Data is transferred to Azure SQL Database using Azure Data Factory.
Data Cleaning: Duplicate and null values are removed within the SQL database.
Data Categorization & Formatting: Data is categorized and formatted using Power Query in Power BI (e.g., age groups, credit scores, churn status).
Visualization: Final KPIs and data visualizations are built in Power BI for churn analysis.
By following this process, you can gain insights into customer churn, segment customers, and monitor KPIs such as churn rate, average age, and tenure, providing valuable information for business decision-making.


