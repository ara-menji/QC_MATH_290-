The very first thing I did was read the questions.
## Question 1
I read the IMDB documentation to find the appropriate data set that contains the information that I need. 

**title.basics** this dataset has the runtime minutes for every movie
**name.basics** contains the name of the actors

originally, I was planning to join the title basics and name basics tables, however,  I got NULL

I figured out that the reason I got NULL is because the primary keys for each tables do not match.

To fix that, I decided to join the two tables with title principles because it has nconst and tconst

**title.principals** contains the principle cast/crew for titles

I noticed the runtime has a strong datatype, so I casted it to int and then took the sum
After I ran my code, I got an error that read: 

    ERROR: invalid input syntax for type integer: "N"
 I didn't understand what the error meant, so I just removed the sum and the cast functions and just ran the code itself. I expected to see multiple rows and numbers, however, the very first row had an "N". 


I modified my code by excluding the N

I reran my code, it executed  successfully.

The total runtime of all movies in the IMDB database where Nicolas Cage appeared as an actor is 4828 minutes
## Question 2
For this question, I had figure out which dataset contains the appropriate information that I need.
The dataset needs to contain

 -  Titles: ID
 - Names of the actors
 - Years

The tables that contain this information are
**title.principals**: to connect the title.basics and name.basics
**name.basics**: primaryName
**title.basics**: startYear

the question asks for the 'most number of titles' this implies that i need to find the **max** number of titles the actors has been in.

after doing some research, I learned that the easiest way to find find the max is just to order the movie titles from highest to lowest, therefore I used the `desc` command. 

here is my though process: 
- i'm going to count all the names and make a new column called movies. 
- i'm going join this table with the name basics table to access the nconst key. 
- next, i joined the title basics table with title principles to access the startYear column
- I'm searched for actor and startYear 
- lastly, I grouped by actor and the year to find the highest to lowest number of movies the actors have

Andi Arsyil Rahman had the most number of titles in 2012
## Question 3
this question asks specifically for nicholas cage, so I know I will be using a `where` command somewhere. 

then the question asks for "highest average rating", so I will need to use the `desc` command. 

Now I need to figure out what table has the information that I need. 

**name.basics**: This table has the primaryName column 

**title.ratings**: This table has averageRating column

**title.principals**: This table will act as a connection to nb and tr

## Question 4
This question asks for short movie, and average rating in 2009
the tables i'll be using to find this information are 

**title.ratings**: this table has the *averageRating* column

**title.basics**: this table has the *startYear* and *titleType* column

all the tables has the *tconst* pk, so there is no need to "build a bridge" like how we did in previous questions with nconst and tconst

Since the question asks for short movie, I'm going to order by average rating to go from highest to lowest
