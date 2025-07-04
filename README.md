# MY-KMS-PROJECT-SOLUTION
KMS Projection Solution on SQL 

---- Question 1 - PRODUCT CATEGORY WITH THE HIGHEST SALES -  Using GROUP BY AND ORDER BY
SELECT TOP 1 [Product_Category], SUM(Sales) AS Total_Sales FROM [KMS Sql Case Study 1] GROUP BY [Product_Category]
ORDER BY Total_Sales DESC;  


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

---- Question 6b - TO CHECK WHAT PRODUCT CATEGORY THEY PURCHASE
SELECT [Customer_Name], [Product_Category], COUNT(*) AS Order_Count, SUM(Sales) As Total_Sales 
FROM [KMS Sql Case Study 1]
WHERE [Customer_Name] IN (SELECT TOP 5 [Customer_Name] 
	FROM [KMS Sql Case Study 1] GROUP BY [Customer_Name] 
	ORDER BY SUM(Sales) DESC  
	)
	GROUP BY [Customer_Name],[Product_Category]
	ORDER BY [Customer_Name], Total_Sales 
DESC;

---- Question 7 - WHICH SMALL BUSINESS CUSTOMER HAD THE HIGHEST SALES
SELECT TOP 1 [Customer_Name], SUM(Sales) AS Total_Sales FROM [KMS Sql Case Study 1]
WHERE [Customer_Segment] = 'Small Business' GROUP BY [Customer_Name]
ORDER BY Total_Sales DESC;

--- NUMBER 8 - CORPORATE CUSTOMER PRODUCT PLACES WITH MOST NUMBER OF ORDERS IN 2009 TO 2012
SELECT TOP 1 c.Customer_Name, COUNT(c.Order_ID) AS Order_Count FROM [KMS Sql Case Study 1] c
JOIN [dbo].[Order_Status] o ON c.Order_ID = o.Order_ID WHERE c.Customer_Segment = 'Corporate'
AND YEAR (Order_Date) BETWEEN 2009 AND  2012
GROUP BY c.Customer_Name
ORDER BY Order_Count DESC; 


---- Question 9 - THE MOST PROFITABLE CUSTOMER
SELECT TOP 1 [Customer_Name], SUM(Profit) AS Total_Profit FROM [KMS Sql Case Study 1] 
WHERE [Customer_Segment] = 'Consumer'
GROUP BY [Customer_Name] ORDER BY Total_Profit DESC;


--- 10 - TO KNOW WHICH CUSTOMER RETURNED ITEMS AND WHICH SEGMENT THEY BELONG TO
SELECT DISTINCT main.[Order_ID], main.[Customer_Name], 
main.[Customer_Segment] FROM [KMS Sql Case Study 1] AS main
JOIN [dbo].[Order_Status] AS Status ON main.[Order_ID] = status.[Order_ID] WHERE status.status = 'Returned';


--- NUMBER 11
SELECT [Order_Priority], [Ship_Mode], COUNT([Order_ID]) AS Order_Count, ROUND(SUM(Sales-Profit),2) As Estimated_Shipping_Cost,
AVG(DATEDIFF(DAY,[Order_Date], [Ship_Date])) AS Average_Ship_Days 
FROM [KMS Sql Case Study 1] 
GROUP BY [Order_Priority], [Ship_Mode]
ORDER BY [Order_Priority], [Ship_Mode] DESC;

