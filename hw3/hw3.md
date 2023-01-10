## Steps:

1.  #### Extracted the files using 7-zip
    
2.  #### Write the script for each tables (creating a schema)
    
3.  #### Run one table at a time
    
4.  #### Refresh the db
    
5.  #### Run the copy command for the table
    
6.  #### Export the data
    

  

# Process

1.  When I made the script for public titles,I forgot to put the double quotations around the variable names and ran it without error. How was I able to run it without error?
    

-   Remember to wrap your variables with double quotes
    
-   if u have more than one variables put a comma between them
    

When I ran the copy command for the titles.aka file, I first got an error about ungranted permission to the file. The error read

SQL Error [42501]: ERROR: could not open file "C:\Users\arapr\Downloads\title.akas.tsv.gz" for reading: Permission denied

Hint: COPY FROM instructs the PostgreSQL server process to read a file. You may want a client-side facility such as psql's \copy.

  

I researched the error on stackover flow ([https://stackoverflow.com/questions/54031813/i-am-trying-to-copy-a-file-but-getting-error-message](https://stackoverflow.com/questions/54031813/i-am-trying-to-copy-a-file-but-getting-error-message) ) I followed the steps necessary to grant the imbd files permission to everyone and now the error was resolved

  

I reran the copy command and then I was hit with another error

  

SQL Error [22021]: ERROR: invalid byte sequence for encoding "UTF8": 0x8b

  

I wasnt (still isnt) sure how to fix this error but I just imported the data through the GUI

  

When I imported the data, I made sure to change the extension from csv to tsv

  

I was then hit with another error

![](https://lh5.googleusercontent.com/pdLj8y5BG5VPKAGjjHq4t83pqt06YhOBBW20VpJCL2A1Ty9R-RWPo_rc-L1Qkd-Vgmf8eH_NZv3MtaRQR1wqjJj86wgySUG6wGf08mVEKjNw5J2OajznzEM6rE1C2PwAK2OPSL2nGJMsCktN1Q-Q9jBGQXrZL0Z_Tr0gvBvgRd9jrGq9niGHi4xtECh6pg)

  

I’m not sure how to fix it, or if it even got fix, but I chose to skip.

After I selected to skip, I realized that the size of the titles_akas increased from 8k to 24K which indicates that the data was imported.

  

To confirm, however, I should implement select statements.

  

The data unfortunately didn’t import. I used the select statement

  

select "titleId" from "IMDB".public.title_akas

  

But got 0

  

I have to figure out to fix that error… tomorrow

  

I'm stuck on step 4

  

Use the COPY FROM command to import title.akas.tsv into the title_akas table in the imdb database

  

Because I get an error

  

To get around this error, I just imported the data using the GUI

-   I selected the data
    
-   Changed the extension of the file to .tsv
    
-   Changed the column delimiter to \t
    

![](https://lh4.googleusercontent.com/lX8ahlKE7fu20dg7Y76nyx_AKsQwU84-vfgvyevumfBb6sCd2v-qN33Xw8QcSlzJhDFV5iQV0gLkfTX-8tIUTwseNo-GS5_-YhWPorm6uQjIHzIuUUiRQ3Qq71fbTUhLbrF_uJf7QVthm4Bih8CKiWjMR2suBazzhpAvyvFuBfar29MvVCMqeTrSPbENMg)

  

This took a while to load the data

  

The next step I took was to export the data to csv, which I was able to do successfully,

  

The next step is to find the cardinality of each column in each table

I did this using the UNION command. However, the flaw I see with doing this is that I’m not able to distinguish what columns belong to what table because union just merges everything to one table.

  

Question

When I look at each table to determine a candidate for a primary key, I noticed that some tables that don’t denote what row is a “unique identifier” or “uniquely identifies”

For example: this is the title_crew table which clearly states that the “tconst (string) - alphanumeric unique identifier of the title”

![](https://lh3.googleusercontent.com/LaLztMz6gZrl7POJWIbXavSDHbcJv0XSg7fHCETExJIZNEXJgZuevsiIMUBuimTwTWYJKuDaxy9uclnhvI2DMjKhjyyPCylKlSzH6HOzlTgrwzGoAfR96Gkp-sZBfweisRQJfoS-Kz8ZLeXrFoPL0EhDWKCBZCeS5C89-Bv2uLH4QRrFcU_evDY3OS-sag)

  

However,

The title_episode doesn’t indicate which row is a “unique identifier” or “uniquely identifies”, but when I load the tables it creates a “parent Tconst” as shown below,

This leads me to believe that Tconst should be the primary key for the table

![](https://lh4.googleusercontent.com/qF8HHi7mJ-BPZy9qzprdc0O7amyK1fUIuyl0P8seCYQVy5vjIWgmp6SCZKGIF19v3As0HNOtRmvLGd5hRrWiN1Md5V2G3NiVtUB1RwnniJKow-qhFNjI_ENPyomKLFGhhhdBkGMz9KBhOok6TcbS2NagHF__CKMalGs54KGtPlE5Ipm3vfkJhmCQ0oA15Q)

  

When i load up the title_principals data i get this. Which im confused as to why they made ordering a PK if it has only 10 distinct records but tconst and ncost have the most out of all which i understand why it would be a pk

![](https://lh3.googleusercontent.com/1YZcH_VYR88ONYa6SokYMj5DFgeFUK7Sqcd-lYhRq_HGDWpLhUz470VVrWE_T9FPyR0JQfk7jTuQs3h2jHqbxROr9Hg5juxesjfCd9aAhhPAa9Kp5a5lsFvl7T5fmNGGo0K0ahzVNNqJR2JA32i1PdB0eXIYNjTYV9JjKZRcMiZeUuww7PTzG9huNf2odg)

  

When I try to make "titleId", "ordering" PK, I get an error

  

SQL Error [42P16]: ERROR: multiple primary keys for table "title_akas" are not allowed

Error position:
