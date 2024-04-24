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
<img src="https://i.imgur.com/FSaTcfB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p align="initial">
<br />
  <br />
  * Next i assigned constraints as seen in the images below: 
 <br />
  <br />
<p align="center">
  - for the order_details table: order_details_id is the primary key while order_id and pizza_id are the foreign key of the table as seen in the diagram below
   <br />
<img src="https://i.imgur.com/Zr41iD4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
- for the orders table: order_id is the primary key and i also sorted out the datatype for date and time as seen in the diagram below. There is no foreign key in this table
   <br />
<img src="https://i.imgur.com/7StAHq8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
- for the pizza_types table: pizza_type_id is the primary key as seen below. There is no foreign key for this table
   <br />
  <br />
<img src="https://i.imgur.com/BMOr9wd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
- for the pizzas table: pizza_id is the primary key and pizza_type_id is the foreign key as seen in the diagram below
     <br />
  <br />
<img src="https://i.imgur.com/MpqsqVv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
  <br />
  <p align="initial">
* Now diving into the most important part of this project. I am going to use codes to help extract informations that the company needs and also solve problems.
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
    I am going to solve all these problems using codes in SQL
<br />
    <br />
1) The company wants to know the costumers best choice. what category of pizza is most ordered?
<br />
<br />
* To solve this problem we need both the quantity and the category column
<br />
 Hence, i am going to join the order_details table and the pizza_type table 
<br />
    <p align="center">
- To join both table we need to first join the pizzas table to the pizza_type table because there is no column directly connecting both table
  <br />
<img src="https://i.imgur.com/Ssq4H95.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <br />
  <p align="initial">
  * After joining the table and getting the column needed to solve the problem i assigned a CTE to the query
 <br />
* Then sumed the quantity, grouped by the category to get the total quantity ordered for each category
<br />
* Then i ordered it from the highest total quantity to get the most ordered category
<br />
  <p align="center">
    <img src="https://i.imgur.com/Y4Iv0lb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
        <br />
    <p align="initial">
      Therefore the most ordered category of pizza is the "classic"
         <br />
          <br />
    2) There is a recession happening in the country which started April. The company want to know the total sales made from all the sizes of pizza since the recession started to know what size of pizza are customers purchasing the most since the recession
      <br />
      <br />
      *
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
