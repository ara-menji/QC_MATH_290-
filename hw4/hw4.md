Aracely
HW7

## Exercise 1

 - I ran the script provided by the professor
 - I created views for every table
 - I created separate files for each
 - I created the physical tables for each data set
 - I changed some of the table's Primary Key and Foreign key relationships from the previous homework.
 - Most of the tables contained the Primary key from the title_aka table. So, I added them as foreign keys in other tables. Some tables do not have Primary Keys as well.

**Question 1** How many movies are in the  `xf_title_basic`  table with runtimes between 42 and 77 minutes?

    SELECT count(*) FROM xf_title_basics
    WHERE runtimeminutes BETWEEN 42 AND 77;

**Question 2** What is the average runtime of movies for adults?

     SELECT AVG(runtimeminutes) as AverageRuntime FROM xf_title_basics WHERE isadult = '1';

**Question 3** Without running the SQL below, what number should it return? In other words, what is the cartesian product of the xf_title_basic table with itself?

 - The query will not run

**Question 4**
 **Round function**  will round the decimal. ROUND(_number_,  _decimals_) or round(30.222,0) rounds the decimal to the nearest 0.

     select round (AVG (runtimeminutes),0) as roundedAVG FROM xf_title_basics WHERE genres [1] = 'Action'
    
**Question 5**  

 - Relative frequency  relationship will show how many times each genre appears in the dataset.
