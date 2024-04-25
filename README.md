<h1>PIZZA_SALES(SQL)</h1>


<h2>Description</h2>
Using the data file PIZZA+PLACE+SALES from https://www.mavenanalytics.io/data-playground. I imported the csv file into SQL<b>(Note: the csv file is attached to this project)</b> and extracted some important information from the data using codes on SQL
<br />


<h2>Data tools used</h2>

- <b>SQL</b> 

<h2>Project walk-through:</h2>
</b>
 * This database constist of 4 tables: order_details, orders, pizza_types, pizzas. As seen on the left side of the image below
 <br />
  <br />
<p align="center">
<img src="https://i.imgur.com/FSaTcfB.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<p align="initial">
<br />
  * Next i assigned constraints as seen in the images below: 
 <br />
<p align="center">
  - for the order_details table: order_details_id is the primary key while order_id and pizza_id are the foreign key of the table as seen in the diagram below
   <br />
<img src="https://i.imgur.com/Zr41iD4.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<br />
<br />
- for the orders table: order_id is the primary key and i also sorted out the datatype for date and time as seen in the diagram below. There is no foreign key in this table
   <br />
<img src="https://i.imgur.com/7StAHq8.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<br />
<br />
- for the pizza_types table: pizza_type_id is the primary key as seen below. There is no foreign key for this table
   <br />
  <br />
<img src="https://i.imgur.com/BMOr9wd.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<br />
<br />
- for the pizzas table: pizza_id is the primary key and pizza_type_id is the foreign key as seen in the diagram below
     <br />
  <br />
<img src="https://i.imgur.com/MpqsqVv.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<br />
  <br />
  <p align="initial">
Now diving into the most important part of this project. I am going to use codes to help extract informations that the company needs and also solve problems.
    <br />
  <br />
1) The company wants to know the costumers best choice. what category of pizza is most ordered?
<br />
    <br />
2) There is a recession happening in the country which started April. The company want to know the total sales made from all the sizes of pizza since the recession started to know what size of pizza are customers purchasing the most since the recession
<br />
    <br />
3) The company is trying to employ more workers. I was reached out to as the data analyst to check which shift gets the most order so they can know what shift needs more workers. Knowing that Morning shift starts at 9:00 and ends at 17;00, while Evening shift starts at 17:00 and ends at 00:00
<br />
    <br />
4) The company needs to know the type of pizza with the most sales and the ones with the least sales so they can know how to balance production
<br />
<br />
    Now i will solve all these problems using codes in SQL
<br />
    <br />
1) The company wants to know the costumers best choice. what category of pizza is most ordered?
<br />
<br />
To solve this problem we need both the quantity and the category column
<br />
 Hence, i am going to join the order_details table and the pizza_type table 
<br />
    <p align="center">
- To join both table we need to first join the pizzas table to the pizza_type table because there is no column directly connecting both table
  <br />
<img src="https://i.imgur.com/Ssq4H95.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
 <br />
  <p align="initial">
  * After joining the table and getting the column needed to solve the problem i assigned a CTE to the query above
 <br />
* Then sumed the quantity, grouped by the category to get the total quantity ordered for each category
<br />
* Then i ordered it from the highest total quantity to get the most ordered category
<br />
  <p align="center">
    <img src="https://i.imgur.com/Y4Iv0lb.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
        <br />
    <p align="initial">
      Therefore the most ordered category of pizza is the "classic"
         <br />
          <br />
    2) There is a recession happening in the country which started April. The company want to know the total sales made from all the sizes of pizza since the recession started to know what size of pizza are customers purchasing the most since the recession
      <br />
      <br />
      * To solve this problem we need the date, size, quantity, price column
     <br />
     * Hence i joined the order_details, orders, pizzas table and select the date, size, quantity and price column
     <br />
     * And also found the total amount per order by multiplying the price and quantity
     <br />
      <br />
      <img src="https://i.imgur.com/CQ2vxsX.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
      <br />
        <br />
     * I assigned a CTE to the query above
        <br />
     * From the CTE i selected only the month from the date knowing that all order happened in 2015, the size and the total amount column
        <br />
     * Knowing that recession started April, i selected the sales from April using "where" clause
        <br />
        <br />
        <img src="https://i.imgur.com/JCgcXXd.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
      <br />
      <br />
     * I assigned another cte to the whole query again i.e cte2
      <br />
     * From the cte i selected the size and total_amount column
      <br />
     * Because we are looking for total sales for each size since April i sumed up the total amount grouped by size as total_sales_since_April
      <br />
      <br />
        <img src="https://i.imgur.com/7b8f0x9.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
      <br />
     We can see that the large size pizza has the most sales since recession started in April and the XXL has the least sales since recession started
     <br />
     <br />
     3) The company is trying to employ more workers. I was reached out to as the data analyst to check which shift gets the most order so they can know what shift needs more workers. Knowing that Morning shift starts at 9:00 and ends at 17;00, while Evening shift starts at 17:00 and ends at 00:00
<br />
     <br />
     * To solve this problem we need the time and order_id column, which is both in the orders table
      <br />
     * Because i have to find out the amount of order during both shifts. I selected hour(time) as hour and order_id
      <br />
      <br />
      <img src="https://i.imgur.com/pvbOIwX.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
      <br />
       <br />
     * I assigned a CTE to the query above
     <br />
     * From the CTE i selected order_id and made a case statement for morning shift and evening shift
     <br />
     <br />
     <img src="https://i.imgur.com/9MlP9dD.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
      <br />
      <br />
      * I assigned another cte to the whole query again i.e cte2
         <br />
         * Then i count the order_id as total_amount_of _order grouped by the workers_shift to get the total order for both shifts
         <br />
         <br />
      <img src="https://i.imgur.com/8TNoERN.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
      <br />
     We can see that the Morning shift has slightly more orders than the evening shift
      <br />
      <br />
       <h2>Note:</h2>
       * The CRM+SALES+OPPORTUNITY raw data file is uploaded above and the excel file for the Project after filtering, sorting and addition of new column is also uploaded above as Tableau Project Excel </b> 
       <br />
    <h1>Tableau Project File</h1>

 ### [TABLEAU PUBLIC](https://public.tableau.com/views/CRMSALESOPPORTUNITY/Dashboard1?:language=en-GB&:sid=&:display_count=n&:origin=viz_share_link)

</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
