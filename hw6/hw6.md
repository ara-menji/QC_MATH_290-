Aracely Menjivar
HW9

For this homework, we used Tableau to visualize the data.

Since we are using Tableau Public, we unfortunately couldn't connect the Postgres sever to Tableau. 

## Question 1
 -   Visualize the data in a histogram and observe if the ratings adhere to a bell curve (use PowerBI to do this)
			 - I uploaded the title_ratings through a text file to overcome this 		   obstacle. 
			 - I then created a new sheet where I visualized the frequency of average_ratings

![image](https://user-images.githubusercontent.com/53866673/204936601-0ad2d585-779f-43d3-a67b-09b32bfe92a9.png)

-   Look at the descriptive statistics of the data (n, min, max, mean, variance, skewness, kurtosis)
			-	I added average_title_rating to the sheet 
			-	Then I employed each operation to each sheet
			-	I struggled to find the skewness and kurtosis of the data, so I researched how to do it (the code for each calculation is shown below)
			

### The descriptive statistics of Title Ratings
![image](https://user-images.githubusercontent.com/53866673/204946260-5a215943-7759-46d9-8398-fb79bf897ec7.png)

### [The table summary]
![image](https://user-images.githubusercontent.com/53866673/204946586-ff4a7465-3427-47aa-ab57-8abab28c00f8.png)

 -   Calculate the relative frequency distribution of movies ratings
		- The relative frequency is illustrated below as a histogram with average rating as the column and rows as the count of the title ratings as a percentage of the total count 
![image](https://user-images.githubusercontent.com/53866673/204950824-78ce665a-d9b1-4719-808a-9a98b21cd96e.png)

## Question 2:

 -  What are the first and last names of all the actors cast in the movie 'Lord of war'? What roles did they play in that production?
	- First I selected the table I needed 
	- Then I decided to do a full outer join between title_principals and title_basics to create a relation betweeb the two
	- Lastly I used a where clause to search for actors and movies
## Question 3:
 - What are the highest-rated Comedy shorts between 2000 and 2010?
	- Similar to question 2, I selected the primary name column from the  title_basics table and performed a full outer join with title_principals.
	- I created a relation between the two tables' primary key to access title_type, genres and start/end year
	
## Question 4:
  
 - What is the average number of votes for movies rated between 0-1, 1-2, 2-3, 3-4, 4-5?
	- I took the average number of votes
	- Did a full outer join with title principals
	- Created the relation 
	- Employed a where clause to search for movie category
	- Grouped by the average ratings between 0-1, 1-2, 2-3, 3-4, 4-5

