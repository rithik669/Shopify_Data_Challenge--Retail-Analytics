# Shopify_Data_Challenge

On Shopify, we have exactly 100 sneaker shops, and each of these shops sells only one model of shoe. We want to do some analysis of the average order value (AOV). When we look at orders data over a 30-day window, we naively calculate an AOV of $3145.13. Given that we know these shops are selling sneakers, a relatively affordable item, something seems wrong with our analysis. 

a.	Think about what could be going wrong with our calculation. Think about a better way to evaluate this data. 

 1.	Upon observing the data, the AOV seems to be high because of the orders involving high amounts. Some heavy transactions were associated with shop_id: 42 and user_id: 607. These transactions took place quite frequently with the same amount and mode of payment. 

 2.	If observed closely, few transactions are reported again with different order_id. It is very much unlikely to make multiple transactions by the same user at one time (In the precision of seconds) for purchasing the same item. With this assumption, those duplicate transactions are removed.

 3. Additionally, the price of a Sneaker at shop_id:42 was the highest ($25,725). As Sneakers are relatively affordable, there can be a mistake in entering the order_amount for this shop. Probably in Cents. The amounts associated with this shop are converted into Dollars.

 4. Upon doing these, the AOV value significantly reduced to $1994.89

 5. If the intention is to know the average value per Sneaker, it can get done by doing the average Sneaker value per unit (By also considering total_items). Its value is $153.240.



b.	What metric would you report for this dataset?

  It is essential to have an appropriate metric to report for data. The right metric  aids businesses in understanding their process and growth. For this dataset,     my choice of metric would be the measure of Sales growth over a biweekly period. This measure can help to analyze the trend of sales. Additionally, there is a       possibility of drilling down this measure to weeks, days, and rolling up to months, quarters, and years.


c.	What is its value?
Ans: 35.416%

