Normalization

What is it: 
	Process of structuring a relational DB to reduce redundancy and improve data integrity
	Instead of storing same piece of info in multiple places (risking inconsistencies), normalization organizes data into related tables using well defined rules called Normal Forms

Why do it:
Eliminate data redundancy - avoid storing data multiple rows
Ensure data consistency - changes to an item of data are made in one location only
Improve query efficiency - smaller tables easier to index
Enforce data integrity - prevent anomalies when inserting, updating and deleting
Improves data maintainability - any updates or corrections require fewer locations to change data

Anomalies
	Update - occurs when there is no normalization
	Insert - when database prevents inerting new data because it lead to inconsistencies
Happens when the DB is improperly normalized - data tables rely on another table incorrectly
Deletion - when deleting a row inadvertently causes loss of info that should be retained.

Normal Forms
	1NF - each field contains only atomic (indivisible) values
		Bad: order_id, customer_id, items_ordered
			1	1		“apple, banana, pear”
		
		Good: order_id, customer_id, item
			1		1	apple
			1		1	banana
			1		1	pear
	
2NF - must be in 1NF, and every non-key must depend on the whole primary key, not part of it

	Orders: order_id, product_id, customer_name
			1	3	Tom
			2	7	Tom
	Orders: order_id, customer_name
	OderDetails: order_id, product_id
	
	3NF - must be in 2NF and no non-key column depends on another non-key column
		Orders order_id, customer_id, customer_address

		Orders: order_id, customer_id
		Customers: customer_id, customer_address

What is over-normalization? - when you break data into so many tables, that you make structure overly complex and inefficient

Customer Names: customer_id, customer_name
Customer Addresses: customer_id, customer_address


Pros/cons 
Pros (see above)
Cons - adds more complexity (queries are harder to write), increases joins (can slow performance), more challenging to understand data relationships

What's an example where normalization makes sense? 
Where data integrity is paramount, and data need to be reliant on one key
Banking Transactions
Data warehouses
Product orders


What about an example where it doesn't make sense? 

Read-Only Data sets
RaceStats
Car_num, racecar_driver, track_name, date, time, current_speed

Simple Data Sets


-> Super simple 
Building id, light_num, floor_number
1, 1
1, 4


