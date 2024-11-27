# **Project Name: Global Classic Collections Product Analysis**
## **This Repository contains:**

|                     |                                             |
|---------------------|---------------------------------------------|
| **Data Source**    | [Click Here for Data Source]()             |
| **Process followed to transform data** | [Power Query Data Extraction and Transformation](#power-query-data-extraction-and-transformation) |
| **Power BI Analysis** | [Power BI Report File (.pbix)]()                 |
| **Insights & Recommendations** | [Power Point Presentation](https://view.officeapps.live.com/op/view.aspx?src=https%3A%2F%2Fraw.githubusercontent.com%2FDataBySwapna%2FMy-Portfolio%2Frefs%2Fheads%2Fmain%2FPowerBI%2FGlobal%2520Classic%2520Collections%2520Project%2FClassicModels-PowerBI-Project.pptx&wdOrigin=BROWSELINK)    |




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
![image1](https://github.com/DataBySwapna/My-Portfolio/blob/main/PowerBI/Global%20Classic%20Collections%20Project/Images/Data_Transformation-1.png)

• Merged payments with employees:

Merged the updated payments table with employees using salesRepEmployeeNumber to get officeCode field from the employees table.
![image2](https://github.com/DataBySwapna/My-Portfolio/blob/main/PowerBI/Global%20Classic%20Collections%20Project/Images/Data_Transformation-2.png)

• Merge payments with offices:

Merged the updated payments table using officeCode with the offices table to get country from the offices table.
![image3](https://github.com/DataBySwapna/My-Portfolio/blob/main/PowerBI/Global%20Classic%20Collections%20Project/Images/Data_Transformation-3.png)

#### **2.2. Calculating Total Revenue**
Calculated the total revenue for each order and aggregated it by office, product line, and region.

• Created a custom column in the orderdetails table to calculate revenue per order line:

Formula: Total Revenue(Sales) = quantityOrdered * priceEach.
![image4](https://github.com/DataBySwapna/My-Portfolio/blob/main/PowerBI/Global%20Classic%20Collections%20Project/Images/Data_Transformation-4.png)

• Merged orderdetails with products using productCode to get productLine.
![image5](https://github.com/DataBySwapna/My-Portfolio/blob/main/PowerBI/Global%20Classic%20Collections%20Project/Images/Data_Transformation-5.png)

• Created report for revenue by offices (country) and revenue by productlines (productLine) using measure Shippedorders:

        Shippedorders = calculate([TotalRevenue(Sales)], 
        'classicmodels orders'[status]="Shipped")

#### **2.3. Grouping and Aggregating Data**

a. Summarized data to analyse office performance.

• Group by Office:

Created a table “classicmodels orders unique” by duplicating the orders table and grouped the data by officeCode to calculate:

Total Orders: Count of rows.

Unique Customers: Count of distinct customerNumber.
![image6](https://github.com/DataBySwapna/My-Portfolio/blob/main/PowerBI/Global%20Classic%20Collections%20Project/Images/Data_Transformation-6.png)

b.	Summarized data to analyse Customer segment purchase frequency.

• Created a table “classicmodels Purchase Frequency” by duplicating the orders table.

• Created year, Month columns by using Date functions on orderDate.

• Created Order Quarter Continuous by using Date.StartOfQuarter([orderDate]).

• Grouped the data by customerNumber, year, Month, to calculate:

• Purchase count: Count of rows.

• Merged the table with customers table using customerNumber to get country.
![image7](https://github.com/DataBySwapna/My-Portfolio/blob/main/PowerBI/Global%20Classic%20Collections%20Project/Images/Data_Transformation-7.png)

### **3. Closing and Applying Changes**
After completing the data transformations, all changes were applied by selecting Close & Apply in Power Query. This loaded the prepared data into Power BI for visualization and analysis.





