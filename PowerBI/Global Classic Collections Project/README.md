

## **Power Query Data Extraction and Transformation**
### **1. Data Extraction:**
#### **1.1 Connecting to the MySQL Database:**
• Connected Power BI to the MySQL database containing the “classicmodels” schema.

• Selected relevant tables: customers, employees, offices, orderdetails , orders, payments, productlines, and products.

#### **1.2 Steps followed:**
• Opened Power BI Desktop and navigated to Home > Get Data > More….

• Selected MySQL Database as the data source.

• Entered the server’s name as 127.0.0.1 and database details as “classicmodels” to connect to the classicmodels database.

• Selected and loaded the required tables (customers, employees, offices, orderdetails , orders, payments, productlines, and products) into Power Query.
        
### **2. Data Transformation:**
Once the data was extracted, I performed the following transformations in Power Query to prepare the data for analysis.

#### **2.1 Merging Tables:**
Combined data from related tables to create a dataset for analysis.

• Merged payments with customers:

Merged the payments table with the customers table using customerNumber to get salesRepEmployeeNumber in the payments table.
![image1](https://github.com/DataBySwapna/My-Portfolio/blob/main/PowerBI/Images/Data_Transformation-1.png)
