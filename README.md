# Case Study 1- Danny's Diner 
## Introduction 
Danny seriously loves Japanese food so in the beginning of 2021, he decides to embark upon a risky venture and opens up a cute little restaurant that sells his 3 favourite foods: sushi, curry and ramen.
Danny’s Diner is in need of your assistance to help the restaurant stay afloat - the restaurant has captured some very basic data from their few months of operation but have no idea how to use their data to help them run the business.

## Problem Statement
Danny wants to use the data to answer a few simple questions about his customers, especially about their visiting patterns, how much money they’ve spent and also which menu items are their favourite. Having this deeper connection with his customers will help him deliver a better and more personalised experience for his loyal customers.

He plans on using these insights to help him decide whether he should expand the existing customer loyalty program - additionally he needs help to generate some basic datasets so his team can easily inspect the data without needing to use SQL.

Danny has provided you with a sample of his overall customer data due to privacy issues - but he hopes that these examples are enough for you to write fully functioning SQL queries to help him answer his questions!

Danny has shared with you 3 key datasets for this case study: <br />

**sales  <br />
menu    <br />
members**

**Table 1: sales** <br  />
The sales table captures all customer_id level purchases with an corresponding order_date and product_id information for when and what menu items were ordered.

customer_id	order_date	product_id  <br />
A	2021-01-01	1  <br />
A	2021-01-01	2   <br />
A	2021-01-07	2   <br />
A	2021-01-10	3 <br />
A	2021-01-11	3  <br />
A	2021-01-11	3 <br />
B	2021-01-01	2 <br />
B	2021-01-02	2 <br />
B	2021-01-04	1 <br />
B	2021-01-11	1 <br />
B	2021-01-16	3 <br />
B	2021-02-01	3 <br />
C	2021-01-01	3 <br />
C	2021-01-01	3  <br />
C	2021-01-07	3 <br />

**Table 2: menu**   <br />
The menu table maps the product_id to the actual product_name and price of each menu item.

product_id	product_name	price  <br />
1	sushi	10  <br />
2	curry	15 <br />
3	ramen	12 <br />

**Table 3: members**  <br />
The final members table captures the join_date when a customer_id joined the beta version of the Danny’s Diner loyalty program.

customer_id	join_date  <br />
A	2021-01-07  <br />
B	2021-01-09 <br />


# Case Study 2- Pizza Runner
## Introduction
Danny was scrolling through his Instagram feed when something really caught his eye - “80s Retro Styling and Pizza Is The Future!”

Danny was sold on the idea, but he knew that pizza alone was not going to help him get seed funding to expand his new Pizza Empire - so he had one more genius idea to combine with it - he was going to Uberize it - and so Pizza Runner was launched!

Danny started by recruiting “runners” to deliver fresh pizza from Pizza Runner Headquarters (otherwise known as Danny’s house) and also maxed out his credit card to pay freelance developers to build a mobile app to accept orders from customers.

# Available Data
Because Danny had a few years of experience as a data scientist - he was very aware that data collection was going to be critical for his business’ growth.

He has prepared for us an entity relationship diagram of his database design but requires further assistance to clean his data and apply some basic calculations so he can better direct his runners and optimise Pizza Runner’s operations.

All datasets exist within the pizza_runner database schema - be sure to include this reference within your SQL scripts as you start exploring the data and answering the case study questions. <br />

**Table 1: runners** <br />
The runners table shows the registration_date for each new runner.

runner_id	registration_date <br />
1	2021-01-01 <br />
2	2021-01-03<br />
3	2021-01-08<br />
4	2021-01-15<br />

**Table 2: customer_orders** <br />
Customer pizza orders are captured in the customer_orders table with 1 row for each individual pizza that is part of the order.

The pizza_id relates to the type of pizza which was ordered whilst the exclusions are the ingredient_id values which should be removed from the pizza and the extras are the ingredient_id values which need to be added to the pizza.

Note that customers can order multiple pizzas in a single order with varying exclusions and extras values even if the pizza is the same type!

The exclusions and extras columns will need to be cleaned up before using them in your queries.

order_id	customer_id	pizza_id	exclusions	extras	order_time <br />
1	101	1	 	 	2021-01-01 18:05:02<br />
2	101	1	 	 	2021-01-01 19:00:52<br />
3	102	1	 	 	2021-01-02 23:51:23<br />
3	102	2	 	NaN	2021-01-02 23:51:23<br />
4	103	1	4	 	2021-01-04 13:23:46<br />
4	103	1	4	 	2021-01-04 13:23:46<br />
4	103	2	4	 	2021-01-04 13:23:46<br />
5	104	1	null	1	2021-01-08 21:00:29<br />
6	101	2	null	null	2021-01-08 21:03:13<br />
7	105	2	null	1	2021-01-08 21:20:29<br />
8	102	1	null	null	2021-01-09 23:54:33<br />
9	103	1	4	1, 5	2021-01-10 11:22:59<br />
10	104	1	null	null	2021-01-11 18:34:49<br />
10	104	1	2, 6	1, 4	2021-01-11 18:34:49<br />

**Table 3: runner_orders** <br />
After each orders are received through the system - they are assigned to a runner - however not all orders are fully completed and can be cancelled by the restaurant or the customer.

The pickup_time is the timestamp at which the runner arrives at the Pizza Runner headquarters to pick up the freshly cooked pizzas. The distance and duration fields are related to how far and long the runner had to travel to deliver the order to the respective customer.

There are some known data issues with this table so be careful when using this in your queries - make sure to check the data types for each column in the schema SQL!

order_id	runner_id	pickup_time	distance	duration	cancellation <br />
1	1	2021-01-01 18:15:34	20km	32 minutes	 <br />
2	1	2021-01-01 19:10:54	20km	27 minutes	 <br />
3	1	2021-01-03 00:12:37	13.4km	20 mins	NaN<br />
4	2	2021-01-04 13:53:03	23.4	40	NaN<br />
5	3	2021-01-08 21:10:57	10	15	NaN<br />
6	3	null	null	null	Restaurant Cancellation <br />
7	2	2020-01-08 21:30:45	25km	25mins	null<br />
8	2	2020-01-10 00:15:02	23.4 km	15 minute	null<br />
9	2	null	null	null	Customer Cancellation<br />
10	1	2020-01-11 18:50:20	10km	10minutes	null<br />

**Table 4: pizza_names** <br />
At the moment - Pizza Runner only has 2 pizzas available the Meat Lovers or Vegetarian!

pizza_id	pizza_name <br />
1	Meat Lovers<br />
2	Vegetarian<br />

**Table 5: pizza_recipes** <br />
Each pizza_id has a standard set of toppings which are used as part of the pizza recipe.

pizza_id	toppings <br />
1	1, 2, 3, 4, 5, 6, 8, 10 <br />
2	4, 6, 7, 9, 11, 12 <br />

**Table 6: pizza_toppings** <br />
This table contains all of the topping_name values with their corresponding topping_id value

topping_id	topping_name <br />
1	Bacon<br />
2	BBQ Sauce<br />
3	Beef<br />
4	Cheese<br />
5	Chicken<br />
6	Mushrooms<br />
7	Onions<br />
8	Pepperoni<br />
9	Peppers<br />
10	Salami<br />
11	Tomatoes<br />
12	Tomato Sauce<br />
