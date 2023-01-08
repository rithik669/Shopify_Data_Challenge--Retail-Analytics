# Shopify_Data_Challenge

# Question-1 (Python)

On Shopify, we have exactly 100 sneaker shops, and each of these shops sells only one model of shoe. We want to do some analysis of the average order value (AOV). When we look at orders data over a 30-day window, we naively calculate an AOV of $3145.13. Given that we know these shops are selling sneakers, a relatively affordable item, something seems wrong with our analysis. 

a.	Think about what could be going wrong with our calculation. Think about a better way to evaluate this data. 

 1.	Upon observing the data, the AOV seems to be high because of the orders involving high amounts. Some heavy transactions were associated with shop_id: 42 and user_id: 607. These transactions took place quite frequently with the same amount and mode of payment. 

 2.	If observed closely, few transactions are reported again with different order_id. It is very much unlikely to make multiple transactions by the same user at one time (In the precision of seconds) for purchasing the same item. With this assumption, those duplicate transactions are removed.

 3. Additionally, the price of a Sneaker at shop_id:42 was the highest ($25,725). As Sneakers are relatively affordable, there can be a mistake in entering the order_amount for this shop. Probably in Cents. The amounts associated with this shop are converted into Dollars.

 4. Upon doing these, the AOV value significantly reduced to $1994.89

 5. If the intention is to know the average value per Sneaker, it can get done by doing the average Sneaker value per unit (By also considering total_items). Its value is $153.240.
                                                                                                                                                                                                        

b.	What metric would you report for this dataset?

Ans: It is essential to have an appropriate metric to report for data. The right metric  aids businesses in understanding their process and growth. For this dataset, my choice of metric would be the measure of Sales growth over a biweekly period. This measure can help to analyze the trend of sales. Additionally, there is a possibility of drilling down this measure to weeks, days, and rolling up to months, quarters, and years.
                                                                                                                                                                               

c.	What is its value?

Ans: 35.416%
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
# Question 2: - (SQL)

For this question you’ll need to use SQL. Follow this link to access the data set required for the challenge. Please use queries to answer the following questions. Paste your queries along with your final numerical answers below.

a.	How many orders were shipped by Speedy Express in total?

Ans: Speedy Express shipped total 54 orders. The following are the query and the result.  

# The Query:

SELECT s.ShipperName,COUNT(DISTINCT(o.OrderID)) AS OrdersShipped                                                                                            
FROM Shippers s JOIN Orders o                                                                                                                                       
ON s.ShipperID = o.ShipperID                                                                                                                                         
WHERE s.ShipperName = "Speedy Express"                                                                                                                               
GROUP BY s.ShipperName;                                                                                                                                            

![image](https://user-images.githubusercontent.com/89163061/169714452-e461e43e-5e60-4b7b-81cf-8a150a0a977b.png)


b.	What is the last name of the employee with the most orders?

Ans: Peacock is the last name of the employee with the highest number of orders- 40. 
The following are the query and its result. 

# The Query:

SELECT e.LastName,COUNT(DISTINCT(o.OrderID)) AS NumOrders                                                                                                           
FROM Employees e JOIN Orders o                                                                                                                                       
ON e.EmployeeID = o.EmployeeID                                                                                                                                       
GROUP BY e.LastName                                                                                                                                                 
ORDER BY NumOrders DESC                                                                                                                                            
LIMIT 3;

![image](https://user-images.githubusercontent.com/89163061/169714437-a01d9bd8-c703-4185-b966-c835fb2a0af1.png)



c.	What product was ordered the most by customers in Germany?

Ans: In terms of orders, Gorgonzola Telino was ordered 5 times which was highest by customers in Germany. In terms of quantity, it was clearly Boston Crab Meat.

# The Query:                                                                                                                                                           
SELECT p.ProductName, COUNT(DISTINCT(o.OrderID))                                                                                                                     
AS NumOrders,SUM(o.Quantity) AS TotalQty                                                                                                                             
FROM ((Products p JOIN OrderDetails o                                                                                                                               
ON p.ProductID = o.ProductID) JOIN Orders q                                                                                                                         
ON q.OrderID = o.OrderID) JOIN Customers c                                                                                                                          
ON c.CustomerID = q.CustomerID                                                                                                                                       
WHERE c.Country = "Germany"                                                                                                                                         
GROUP BY p.ProductName                                                                                                                                              
ORDER BY NumOrders DESC,TotalQty DESC                                                                                                                               
LIMIT 5;                                                                                                                                                             

![image](https://user-images.githubusercontent.com/89163061/169714483-f23ce741-4768-4752-93eb-30c8f2a4f7a4.png)

