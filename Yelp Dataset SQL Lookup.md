Data Scientist Role Play: Profiling and Analyzing the Yelp Dataset Coursera Worksheet

This is a 2-part assignment. In the first part, you are asked a series of questions that will help you profile and understand the data just like a data scientist would. For this first part of the assignment, you will be assessed both on the correctness of your findings, as well as the code you used to arrive at your answer. You will be graded on how easy your code is to read, so remember to use proper formatting and comments where necessary.

In the second part of the assignment, you are asked to come up with your own inferences and analysis of the data for a particular research question you want to answer. You will be required to prepare the dataset for the analysis you choose to do. As with the first part, you will be graded, in part, on how easy your code is to read, so use proper formatting and comments to illustrate and communicate your intent as required.

For both parts of this assignment, use this "worksheet." It provides all the questions you are being asked, and your job will be to transfer your answers and SQL coding where indicated into this worksheet so that your peers can review your work. You should be able to use any Text Editor (Windows Notepad, Apple TextEdit, Notepad ++, Sublime Text, etc.) to copy and paste your answers. If you are going to use Word or some other page layout application, just be careful to make sure your answers and code are lined appropriately.
In this case, you may want to save as a PDF to ensure your formatting remains intact for you reviewer.



Part 1: Yelp Dataset Profiling and Understanding

1. Profile the data by finding the total number of records for each of the tables below:
	
i. Attribute table = 10000
ii. Business table = 10000
iii. Category table = 10000
iv. Checkin table =10000
v. elite_years table =10000
vi. friend table = 10000
vii. hours table =10000
viii. photo table = 10000
ix. review table = 10000
x. tip table = 10000
xi. user table =10000
	


2. Find the total distinct records by either the foreign key or primary key for each table. If two foreign keys are listed in the table, please specify which foreign key.

i. Business =10000
ii. Hours =1562
iii. Category =2643
iv. Attribute =1115
v. Review = 10000
vi. Checkin = 493
vii. Photo =10000
viii. Tip = 537
ix. User = 10000
x. Friend = 11
xi. Elite_years =2780

Note: Primary Keys are denoted in the ER-Diagram with a yellow key icon.	



3. Are there any columns with null values in the Users table? Indicate "yes," or "no."

	Answer:
	NO
	
	SQL code used to arrive at answer:
```
select COUNT(*)
from user
where id = NULL;
```	

	
4. For each table and column listed below, display the smallest (minimum), largest (maximum), and average (mean) value for the following fields:

	i. Table: Review, Column: Stars
	
		min:1		max:	5	avg:3.7082
		
	
	ii. Table: Business, Column: Stars
	
		min:1.0		max:5.0		avg:3.6549
		
	
	iii. Table: Tip, Column: Likes
	
		min:0		max:2		avg:0.0144
		
	
	iv. Table: Checkin, Column: Count
	
		min:1		max:53		avg:1.9414
		
	
	v. Table: User, Column: Review_count
	
		min:0		max:2000		avg:24.2995
		


5. List the cities with the most reviews in descending order:

	SQL code used to arrive at answer:
```
select city, review_count
from business
order by review_count desc;
```	
	Copy and Paste the Result Below:
+------------+--------------+
| city       | review_count |
+------------+--------------+
| Las Vegas  |         3873 |
| Montréal   |         1757 |
| Gilbert    |         1549 |
| Las Vegas  |         1410 |
| Las Vegas  |         1389 |
| Las Vegas  |         1252 |
| Las Vegas  |         1116 |
| Las Vegas  |         1084 |
| Las Vegas  |          961 |
| Gilbert    |          902 |
| Las Vegas  |          864 |
| Scottsdale |          823 |
| Las Vegas  |          821 |
| Las Vegas  |          786 |
| Henderson  |          785 |
| Toronto    |          778 |
| Las Vegas  |          768 |
| Las Vegas  |          758 |
| Scottsdale |          726 |
| Cleveland  |          723 |
| Las Vegas  |          720 |
| Charlotte  |          715 |
| Phoenix    |          711 |
| Las Vegas  |          706 |
| Phoenix    |          700 |
+------------+--------------+
(Output limit exceeded, 25 of 10000 total rows shown)

	
6. Find the distribution of star ratings to the business in the following cities:

i. Avon

SQL code used to arrive at answer:
```
select stars, review_count
from business
where city = 'Avon'
group by stars
order by stars desc;
```
Copy and Paste the Resulting Table Below (2 columns 鈥  star rating and count):

+-------+--------------+
| stars | review_count |
+-------+--------------+
|   5.0 |            3 |
|   4.5 |           31 |
|   4.0 |           17 |
|   3.5 |           50 |
|   2.5 |            3 |
|   1.5 |           10 |
+-------+--------------+

ii. Beachwood

SQL code used to arrive at answer:
```
select stars, review_count
from business
where city = 'Beachwood'
group by stars
order by stars desc;
```
Copy and Paste the Resulting Table Below (2 columns 鈥  star rating and count):
+-------+--------------+
| stars | review_count |
+-------+--------------+
|   5.0 |            4 |
|   4.5 |            3 |
|   4.0 |           69 |
|   3.5 |            3 |
|   3.0 |            3 |
|   2.5 |            3 |
|   2.0 |            8 |
+-------+--------------+


7. Find the top 3 users based on their total number of reviews:
		
	SQL code used to arrive at answer:
```	
select id, review_count
from user
order by review_count desc
limit 3;
```		
	Copy and Paste the Result Below:
		
+------------------------+--------------+
| id                     | review_count |
+------------------------+--------------+
| -G7Zkl1wIWBBmD0KRy_sCw |         2000 |
| -3s52C4zL_DHRK0ULG6qtg |         1629 |
| -8lbUNlXVSoXqaRRiHiSNg |         1339 |
+------------------------+--------------+

8. Does posing more reviews correlate with more fans?
No.
	Please explain your findings and interpretation of the results:
Explanation:
With top counts of reviews, they have more of fewer fans, not trend observed.

```
select id, review_count, fans
from user
order by review_count desc, fans desc;
```
Result:
+------------------------+--------------+------+
| id                     | review_count | fans |
+------------------------+--------------+------+
| -G7Zkl1wIWBBmD0KRy_sCw |         2000 |  253 |
| -3s52C4zL_DHRK0ULG6qtg |         1629 |   50 |
| -8lbUNlXVSoXqaRRiHiSNg |         1339 |   76 |
| -K2Tcgh2EKX6e6HqqIrBIQ |         1246 |  101 |
| -FZBTkAZEXoP7CYvRV2ZwQ |         1215 |  126 |
| --2vR0DIsmQ6WfcSzKWigw |         1153 |  311 |
| -gokwePdbXjfS0iF7NsUGA |         1116 |   16 |
| -DFCC64NXgqrxlO8aLU5rg |         1039 |  104 |
| -8EnCioUmDygAbsYZmTeRQ |          968 |  497 |
| -0IiMAZI2SsQ7VmyzJjokQ |          930 |  173 |
| -fUARDNuXAfrOn4WLSZLgA |          904 |   38 |
| -hKniZN2OdshWLHYuj21jQ |          864 |   43 |
| -9da1xk7zgnnfO1uTVYGkA |          862 |  124 |
| -B-QEUESGWHPE_889WJaeg |          861 |  115 |
| -kLVfaJytOJY2-QdQoCcNQ |          842 |   85 |
| -kO6984fXByyZm3_6z2JYg |          836 |   37 |
| -lh59ko3dxChBSZ9U7LfUw |          834 |  120 |
| -g3XIcCb2b-BD0QBCcq2Sw |          813 |  159 |
| -l9giG8TSDBG1jnUBUXp5w |          775 |   61 |
| -dw8f7FLaUmWR7bfJ_Yf0w |          754 |   78 |
| -AaBjWJYiQxXkCMDlXfPGw |          702 |   35 |
| -jt1ACMiZljnBFvS6RRvnA |          696 |   10 |
| -IgKkE8JvYNWeGu8ze4P8Q |          694 |  101 |
| -hxUwfo3cMnLTv-CAaP69A |          676 |   25 |
| -H6cTbVxeIRYR-atxdielQ |          675 |   45 |
+------------------------+--------------+------+
(Output limit exceeded, 25 of 10000 total rows shown)
	
9. Are there more reviews with the word "love" or with the word "hate" in them?

	Answer: Yes

	
	SQL code used to arrive at answer:
```
select
count (*) AS Hate
from review
where text like '%hate%';

select
count (*) AS Love
from review
where text like '%love%';
```	
	
10. Find the top 10 users with the most fans:

	SQL code used to arrive at answer:
	
select id, fans
from user
order by fans desc
limit 10;
	
	Copy and Paste the Result Below:
+------------------------+------+
| id                     | fans |
+------------------------+------+
| -9I98YbNQnLdAmcYfb324Q |  503 |
| -8EnCioUmDygAbsYZmTeRQ |  497 |
| --2vR0DIsmQ6WfcSzKWigw |  311 |
| -G7Zkl1wIWBBmD0KRy_sCw |  253 |
| -0IiMAZI2SsQ7VmyzJjokQ |  173 |
| -g3XIcCb2b-BD0QBCcq2Sw |  159 |
| -9bbDysuiWeo2VShFJJtcw |  133 |
| -FZBTkAZEXoP7CYvRV2ZwQ |  126 |
| -9da1xk7zgnnfO1uTVYGkA |  124 |
| -lh59ko3dxChBSZ9U7LfUw |  120 |
+------------------------+------+

		

Part 2: Inferences and Analysis

1. Pick one city and category of your choice and group the businesses in that city or category by their overall star rating. Compare the businesses with 2-3 stars to the businesses with 4-5 stars and answer the following questions. Include your code.
	
i. Do the two groups you chose to analyze have a different distribution of hours?
No

ii. Do the two groups you chose to analyze have a different number of reviews?
Yes       
         
iii. Are you able to infer anything from the location data provided between these two groups? Explain.
No because Eastside has both 4-5 star business and 2-3 star ones.

SQL code used for analysis:

+-------------------+-------+---------------+--------------+--------------+
| hours             | stars | category      | review_count | neighborhood |
+-------------------+-------+---------------+--------------+--------------+
| Monday|9:00-17:30 |   5.0 | Doctors       |            5 | Anthem       |
| Monday|9:00-17:30 |   4.5 | Japanese      |            3 | Eastside     |
| Monday|9:00-17:30 |   4.0 | Gluten-Free   |          168 | Summerlin    |
| Monday|9:00-17:30 |   3.5 | Bars          |          105 | Southwest    |
| Monday|9:00-17:30 |   3.0 | Restaurants   |          123 |              |
| Monday|9:00-17:30 |   2.5 | Beauty & Spas |            6 | Eastside     |
+-------------------+-------+---------------+--------------+--------------+
	
		
2. Group business based on the ones that are open and the ones that are closed. What differences can you find between the ones that are still open and the ones that are closed? List at least two differences and the SQL code you used to arrive at your answer.
		
i. Difference 1:
Those still open have longer hours      
         
ii. Difference 2:
Those still open have more reviews
         
         
SQL code used for analysis:
```
select business.name
, business.is_open
, category.category
, business.stars
, hours.hours
, business.review_count
, business.postal_code
from (business inner join category on business.id = category.business_id) inner join hours on hours.business_id = category.business_id
where business.city = 'Las Vegas' 
 group by business.is_open;
 ```
	
3. For this last part of your analysis, you are going to choose the type of analysis you want to conduct on the Yelp dataset and are going to prepare the data for analysis.

Ideas for analysis include: Parsing out keywords and business attributes for sentiment analysis, clustering businesses to find commonalities or anomalies between them, predicting the overall star rating for a business, predicting the number of fans a user will have, and so on. These are just a few examples to get you started, so feel free to be creative and come up with your own problem you want to solve. Provide answers, in-line, to all of the following:
	
i. Indicate the type of analysis you chose to do:
Wheter business in certain cities have more funny reviews  
         
ii. Write 1-2 brief paragraphs on the type of data you will need for your analysis and why you chose that data:
I will need 2 tables: review & business. From review, I would get data about funny reviews and from business the cities of business                        
                  
iii. Output of your finished dataset:
+-------+------------------+
| funny | city             |
+-------+------------------+
|     7 | Woodmere Village |
|     5 | Strongsville     |
|     4 | North Las Vegas  |
|     2 | Boulder City     |
|     1 | Chandler         |
|     1 | Mississauga      |
|     1 | Parma            |
|     1 | Richmond Hill    |
|     1 | Stow             |
|     1 | Twinsburg        |
|     0 | Ahwatukee        |
|     0 | Ajax             |
|     0 | Allison Park     |
|     0 | Aurora           |
|     0 | Avondale         |
|     0 | Beachwood        |
|     0 | Berea            |
|     0 | Brampton         |
|     0 | Burton           |
|     0 | Cave Creek       |
|     0 | Champaign        |
|     0 | Charlotte        |
|     0 | Cleveland        |
|     0 | Concord          |
|     0 | Cornelius        |
+-------+------------------+
(Output limit exceeded, 25 of 67 total rows shown)         
         
iv. Provide the SQL code you used to create your final dataset:
```
select review.funny, business.city
from review inner join business on business.id = review.business_id
group by business.city
order by funny desc;
```
