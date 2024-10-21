java cAssignment 1, Commerce 3DA3 C02 - Predictive Data Analytics
To complete this assignment, please create a Jupyter notebook. The code in your jupyter notebook should provide answers to questions asked in the assignment. Please submit the assignment by uploading the file(s) into the "Assignment 1" folder on Avenue to Learn. You can find this folder under "Assessments>Assignments" on the course page. The deadline for submission is 11:59PM on Monday Oct. 21.
Background
In the past decade, we witnessed the rise of online grocery shopping. With the convenience of ordering groceries from the comfort of home, more people are turning to digital platforms for their everyday needs. This shift has been further fueled by factors such as busy lifestyles, the increasing use of mobile devices, and the covid-19 pandemic, which underscored the importance of contactless shopping.
For online grocery platforms, conducting data analysis on sales records is critical for understanding customer behavior, enhancing the overall shopping experience, and make data-driven decisions that lead to higher customer satisfaction and profitability.
Data: We will make use of two datasets from the transaction records of an online grocery delivery platform, stored in the files orders.csv (click to download) and order_products.csv (click to download).
The dataset in orders.csv includes the following columns:
order_id: This is the unique identifier of every customer order
customer_id: This is the unique identifier of every customer who placed the order order_dow: This indicates the day of the week, on which the order took place. 0 stands for Sunday, 1-5 indiates Monday-Friday, and 6 indicates a Saturday. order_hour_of_day: This indicates during which hour the order took place; for example, 14 indicates that the order was placed between 14:00 and 14:59. days_since_prior_order: This indicates how many days have passed since the customer's last order
coupon_use: This shows if the customer used a coupon to (partially) pay for the order
The dataset in order_products.csv records which products are purchased in an order. It

 includes the following columns:
order_id: This is the order idenfitier (same as in order.csv).
product_id: This is the identifier of a product that is purchased in the corresponding order.
quantity: This is the quantity of the product purchased in the corresponding order. unit_price: This is the unit price (in dollars) of the product purchased in the corresponding order.
customer_id: This is the identifier of the customer who purchased the product.
Please note that order_id in order_products.csv does not need to be unique. If two rows in order_products.csv share the same order_id, it means that in the same order, the products in those two rows are both purchased.
For example, suppose that the following row exists in order.csv:
order_id customer_id order_dow order_hour_of_day days_since_prior_order coupon_u
O1234 C6217 2 10 11 yes and the following two rows exist in order_products.csv:
         order_id
O1234
O1234
product_id quantity
P0217 1
P0219 2
unit price customer_id
9.99 C6217
19.99 C6217
         then we know that in the same order (order_id O1234), 1 unit of product P0217 and 2 units of product P0219 are purchased. And this order O1234 is the same order as the order O1234 in order.csv.
Imagine that you are a data analyst at the grocery delivery platform. Based on the datasets, please answer the following questions/tasks.
Questions 0.
In the first cell of your Jupyter notebook, please create the following as markdown. Add your first and last name, and your Student ID.
se

  Important: For the remaining questions, please make sure to create a markdown cell before you answer each question and in it indicate the question number, e.g., Question 1, Question 2, etc.
For each question, you should use one or more code cells to present your codes. Please make sure that you run each cell and display all the requested results. Please also ensure that you will use markdown cells to provide necessary explanations of your codes and results.
The Jupyter notebook should be a easy-to-read report that presents your analysis and results. The grading will be based on both the correct代 写program、Java/python
代做程序编程语言ness of your coding and the readability of your notebook.
Question 1.
Import the two .csv files and assign them to a dataframe called df_orders and df_order_products , respectively. Then,
use a line of codes to review the first few rows of the dataframes. The result should be clearly displayed in the notebook after you run the code cells.
get the structures of the dataframes (number of rows, column types, etc.) using the
info() function. Review the first few rows of the dataframe.
In a markdown cell,explain the results returned by this function as comprehensive as you
can..
Question 2.
For the DataFrame df_orders loaded from orders.csv, perform the following steps in the given order.
1. Find how many missing value each column contains.
2. For any missing value in the column   , replace it with 'unknown_order'
3. For any missing value in the column   , replace it with
     'unknown_customer'
order_id
customer_id

 4. For any missing value in the column   , replace it with the mean value of the column
5. After completing the above steps, repeat the codes in Step 1 to check again the number of missing values in each column
6. For any remaining missing values, drop all rows containing a missing value
Question 3.
The grocery delivery platform is interested in assessing if offering coupons will increase customers' purchase frequency. To that end, let us again make use of the DataFrame
df_orders (loaded from orders.csv) to perform the following tasks.
1. Select all rows in df_orders where use of a coupon is yes , and assign those rows as a new DataFrame named df_orders_coupon .
2. Calculate the mean value of 'days_since_prior_order' in df_orders_coupon .
3. Select all rows in where use of a coupon is no , and assign those rows
as a new DataFrame named .
4. Calculate the mean value of 'days_since_prior_order' in df_orders_no_coupon .
Based on your findings of the above steps, answer the following question in a markdown cell:
Is the use of coupon associated with higher/lower order frequency? Please briefly explain your answer in the markdown cell.
Questions 4.
The platform is also interested in measuring the total number of orders received on each day of the week. To do this, they would like you to complete the following tasks.
Divide the order id's in the 'order_id' column of the DataFrame df_orders (loaded from orders.csv) into groups, based on the day of the week ('order_dow') when the order is placed. The result should be a Groupby object.
Construct and display the content of a pandas Series, which should show the total number of orders for each day of the week.
Question 5.
As observed, each row of the data in order_products.csv is the sales information of a product in a certain order. The information includes the per-unit price and number of units ordered, but it does not directly provide the revenue.
     df_orders
 df_orders_no_coupon
   days_since_prior_order

 Let us now create a new column named 'revenue' in the DataFrame df_order_products constructed from order_products.csv. For each row, the
column should contain the corresponding revenue, calcuated as 'quantity'×'unit price'. See the following two-row example for a demonstration.
order_id product_id quantity unit_price customer_id revenue
O1234 P0217 1 9.99 C6217 9.99
O1234 P0219 2 19.99 C6217 39.98
After you have added the new column, further complete the following tasks:
Display the first few rows of the updated df_order_products DataFrame. Calculate the total revenue by summing up revenues in each row.
Question 6
From time to time, there will be customers who would like to review their purchase record. To do that, they will need to supply their customer id.
Suppose a customer with the id '0421MWMT' just contacted Customer Service and would like to see all their purchases. Perform the following tasks for the customer.
Select all rows related to this customer's purchases in the DataFrame df_order_products (loaded from order_products.csv), and assign them to a
new DataFrame named 'df_cust_inquiry'. Display the content of this DataFrame. Calculate the customer's total purchase in dollar amount.
              
         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
