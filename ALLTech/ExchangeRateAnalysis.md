## Problem Scenario


![exchange Rate](https://user-images.githubusercontent.com/16081831/142198030-3583fe0b-be44-456d-9322-16d6f5348728.png)

ABC Organization like you to consolidate your orders along with an exchange rate for the date of the order creations. 
This way, orders prices can be unified in Canadian Dollars (CAD), the currency that the Finance department of ABC uses to report on.
For this purpose, we suggest you to use the free currency exchange rate API provided by: https://exchangeratesapi.io/.

Your first task is to implement a Python script that loads the orders, loads the exchange rate on the date of the order (via the Exchange Rate API) so each order contains
a "currency rate" property from USD to CAD.The outcome of this task is to output files one is the complete data with all the detailed information and one is the summary based only on Order_id and the final price(CAD)
and saved the files in the output folder.
In second Task,we would like you to persist the data obtained from task 1: upload your data to a SQL database of your choice (SQLite, MySQL, PostgreSQL ...).

Design the right data model for your data Create the SQL tables Import your data The outcome of this task is:

SQL statements to create tables for the data A Python script to upload the data (or the one from Task 1, extended)


Last task is to visualize the data extracted in output files you come up with in task1.Create visualizations/Dashboard
to analyze the data further.


![image](https://user-images.githubusercontent.com/16081831/142198337-35a799ca-13b0-4549-a55f-c0ba4564c5de.png)




## Challenge Task 

### TASK 1:(Data Wrangling)
Imported the JSON file(orders.json) in python pandas and so all the data cleaning and export the currency data from the provided API and create the final required file.
### TASK 2:(SQL)
Created three files Order, Customer and Product level data and upload the data through python.
### TASK 3:(Data Visualization)
Created the tableau workbook using the output file from task1.


![image](https://user-images.githubusercontent.com/16081831/142198918-339cd2cc-7d5a-4498-8700-d8cc7400c9fe.png)
