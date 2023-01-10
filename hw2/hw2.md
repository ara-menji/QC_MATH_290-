Aracely
HW5

## Question 2

 - The answer is shown in the screenshot below
 ![image](https://user-images.githubusercontent.com/53866673/205170087-4e2a6dd3-616c-4e1a-a63b-a6666f01ced6.png)

## Question 3
![image](https://user-images.githubusercontent.com/53866673/205170247-c12544a7-f0a1-4b78-a604-703a430c7e13.png)

## Question 4

     select distinct (*)
     from (
     	select avg
     	(tip_amount/total_amount) as Average_Tip
     	from yellow_taxi
     	where extract (hour from tpep_dropoff_datetime) as drop_hour
     	group by drop_hour
     	order drop_hour by desc
     	)as h ;

## Question 5

    create view daily_tip_percentage_by_distance as
    SELECT tpep_pickup_datetime, trip_mileage 
    	CASE WHEN trip_mileage >= 0 and trip_mileage < 1 then '0-1 mile'
                WHEN trip_mileage >= 0 and trip_mileage < 1 then '0-1 mile'
                WHEN trip_mileage >= 1 and trip_mileage < 2 then '1-2 mile'
                WHEN trip_mileage >= 2 and trip_mileage < 3 then '2-3 mile'
                WHEN trip_mileage >= 3 and trip_mileage < 4 then '3-4 mile'
                WHEN trip_mileage >= 4 and trip_mileage < 5 then '4-5 mile'
                WHEN trip_mileage >= 5 then '5+ mile'
                END as trip_mileage_band
                order by tpep_pickup_datetime, trip_mileage;
