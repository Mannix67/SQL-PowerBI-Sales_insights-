# SQL-PowerBI-Sales_insights-

# Please click raw power bi file .pbix above to interact with final power bi dashboard. If this is not possible, i have attached screenshots down below.  



# Data Analysis Using SQL 

Show all customer records

    SELECT * FROM customers;

Show total number of customers

    SELECT count(*) FROM customers;

Show transactions for Chennai market (market code for chennai is Mark001

    SELECT * FROM transactions where market_code='Mark001';

Show distrinct product codes that were sold in chennai

    SELECT distinct product_code FROM transactions where market_code='Mark001';

Show transactions where currency is US dollars

    SELECT * from transactions where currency="USD"

Show transactions in 2020 join by date table

    SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;

Show total revenue in year 2020,

    SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r"     or transactions.currency="USD\r";

Show total revenue in year 2020, January Month,

    SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January"     and (transactions.currency="INR\r" or transactions.currency="USD\r");

Show total revenue in year 2020 in Chennai

    SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and                        t         transactions.market_code="Mark001";  

# Data Analysis Using Power BI
Formula to create norm_amount column
     = Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)
     
Dax Query for Revenue :

     Revenue = SUM('sales transactions'[sales_amount])
     
Dax Query for Sales QTY

    Sales Qty = SUM('sales transactions'[sales_qty])



# ----

![Screenshot (259)](https://user-images.githubusercontent.com/84920516/166907942-3d9f52c9-3e7a-40a2-addb-667e35805ba8.png)

![Screenshot (260)](https://user-images.githubusercontent.com/84920516/166907996-469df2e0-5456-4934-84a5-3e99a33b992f.png)

![Screenshot (261)](https://user-images.githubusercontent.com/84920516/166908034-8fd19528-ee9a-4578-9662-6f2c66cb9d16.png)
