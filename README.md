# MY-KMS-PROJECT-SOLUTION
KMS Projection Solution on SQL 

---- Question 1 - PRODUCT CATEGORY WITH THE HIGHEST SALES -  Using GROUP BY AND ORDER BY
~~~SQL SELECT TOP 1 [Product_Category], SUM(Sales) AS Total_Sales FROM [KMS Sql Case Study 1] GROUP BY [Product_Category]
ORDER BY Total_Sales DESC;~~~  

---- Question 2a - TOP 3 REGIONS BY SALES
~~~SQL SELECT TOP 3 Region, SUM(Sales) AS Total_Sales FROM [KMS Sql Case Study 1] GROUP BY Region ORDER BY Total_Sales DESC;~~~


--- Question 2b -  BOTTOM 3 REGIONS BY SALES
SELECT TOP 3 Region, SUM(Sales) AS Total_Sales FROM [KMS Sql Case Study 1] 
GROUP BY Region ORDER BY Total_Sales ASC;

--- Question 3 - TOTAL SALES OF APPLIANCES IN ONTARIO
SELECT SUM(Sales) AS Total_Appliances FROM [KMS Sql Case Study 1] 
WHERE [Product_Sub_Category] = 'Appliances' AND Region = 'Ontario';

--- Question 4 - TO INCREASE THE REVENUE FROM THE BOTTOM 10 CUSTOMERS - BOTTOM 10 CUSTOMERS
SELECT TOP 10 [Customer_Name], SUM(Sales) AS Total_Sales FROM [KMS Sql Case Study 1] GROUP BY [Customer_Name]
ORDER BY Total_Sales ASC;

---- Question 5 - SHIPPING METHOD WITH THE HIGHEST SHIPPING COST
SELECT TOP 1 [Ship_Mode], SUM([Shipping_Cost]) AS Total_Shipping_Cost FROM [KMS Sql Case Study 1] 
GROUP BY [Ship_Mode] 
ORDER BY Total_Shipping_Cost DESC;


--- Question 6a - MOST VALUABLE CUSTOMERS AND THE PRODUCTS THEY PURCHASE
SELECT TOP 5 [Customer_Name], SUM(Sales) AS Total_Sales FROM [KMS Sql Case Study 1] GROUP BY [Customer_Name] 
ORDER BY Total_Sales DESC;

