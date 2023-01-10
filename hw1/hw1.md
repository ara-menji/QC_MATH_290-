Aracely Menjivar 
HW 4

## Question 1
- I wasn't able to reduce the number of select statement. However, I employed the union command to create the table with the column_name	distinct_records side by side. 

- The total distinct rows from the above results is approximately **23587846**.

## Question 2
- I built a sub-query that will gave me the distinct record count across all 17 columns
-   I don't think any of the columns could serve as a Primary Key.
    
-   Most of the results were in thousands, but the combination of "Vendorid" and "mta_tax" was 35 and "Vendorid" and "ratecodeid" was only 15.
## Question 3
-   How many rows have a "passenger_count" equal to 5.

    select count (passenger_count) as Total_Passenger
    from yellow_taxi
    where passenger_count= 5;

	![image](https://user-images.githubusercontent.com/53866673/205166457-8b312941-b4b0-4215-acda-a3b81927d8ff.png)

-   How many distinct trips have a "passenger_count" greater than 3?

    SELECT COUNT(DISTINCT passenger_count)
    FROM yellow_taxi
    where passenger_count > 3 ;
	![image](https://user-images.githubusercontent.com/53866673/205166749-08495517-12de-48b0-af68-19e45df5ea32.png)


-   How many rows have a tpep_pickup_datetime between '2018-04-01 00:00:00' and '2018-05-01 00:00:00'?

    select count (tpep_pickup_datetime) as Total_Pickuptimes
    from yellow_taxi
    where tpep_pickup_datetime between '2020-04-01 00:00:00' and '2020-05-01 00:00:00';

	![image](https://user-images.githubusercontent.com/53866673/205166964-70423121-9260-42b9-8a30-393a933807a0.png)

-   How many distinct trips occurred in June where the tip_amount was greater than equal to $5.00?

     select count (tpep_pickup_datetime) as Total_Pickuptimes
     from yellow_taxi 
     where tpep_pickup_datetime >= '2020-04-01 00:00:00' and tpep_pickup_datetime <= '2020-05-01 00:00:00';

	![image](https://user-images.githubusercontent.com/53866673/205167073-06f1494a-f43a-424d-a850-1a3c4f3b07e1.png)

-   How many distinct trips occurred in May where the passenger_count was greater than three and tip_amount was between $2.00 and $5.00?

    SELECT COUNT(DISTINCT tpep_pickup_datetime) 
    FROM yellow_taxi
    where tpep_pickup_datetime >= '2020-06-01 00:00:00' and tpep_pickup_datetime <= '2020-06-30 23:59:00' and
    tip_amount >= 5;
	![image](https://user-images.githubusercontent.com/53866673/205167688-c3460feb-6921-4e77-aace-d1f31f5052af.png)


-   What is the sum of tip_amount in the  `2018_Yellow_Taxi_Trip_Data`  dataset? (Hint: use the SUM() function to find the answer)

    SELECT SUM(tip_amount) as Total_Tip
     FROM yellow_taxi; 
	![image](https://user-images.githubusercontent.com/53866673/205167506-4769c881-45c5-408f-94e5-37b1a6765251.png)
## Question 4
- The size of the base folder is 4.4 GB 4,343,696,175 bytes 
- After the deletion, the base folder decreased to 4.04 GB 4,343,696,175 bytes

## Question 5
- The vacuum helps physically remove the deleted tuples from the Database. After deleting itself, the tuples are not physically removed from their table; they remain present until a VACUUM is done.
