# SQL Homework

The Glasgow Film Theatre are having a Marvel Movie Marathon! They have asked you to help maintain their database of movies with times and attendees.

## To access the database:

First, create a database called 'marvel'
```
# terminal
createdb marvel
```

Next, run the provided SQL script to populate your database:
```
# terminal
psql -d marvel -f marvel.sql
```

Use the supplied data as the source of data to answer the questions.  Copy the SQL command you have used to get the answer, and paste it below the question, along with the result they gave.

## Questions

1. Return ALL the data in the 'movies' table.

SELECT * FROM movies;

id |                title                | year | show_time
----+-------------------------------------+------+-----------
 1 | Iron Man                            | 2008 | 18:10
 2 | The Incredible Hulk                 | 2008 | 20:10
 3 | Iron Man 2                          | 2010 | 19:05
 4 | Thor                                | 2011 | 21:45
 5 | Captain America: The First Avenger  | 2011 | 17:50
 6 | Avengers Assemble                   | 2012 | 15:20
 7 | Iron Man 3                          | 2013 | 21:00
 8 | Thor: The Dark World                | 2013 | 19:35
 9 | Batman Begins                       | 2005 | 13:30
10 | Captain America: The Winter Soldier | 2014 | 16:25
11 | Guardians of the Galaxy             | 2014 | 21:20
12 | Avengers: Age of Ultron             | 2015 | 21:00
13 | Ant-Man                             | 2015 | 22:00
14 | Captain America: Civil War          | 2016 | 19:30
15 | Doctor Strange                      | 2016 | 20:30
16 | Guardians of the Galaxy 2           | 2017 | 21:40
17 | Spider-man: Homecoming              | 2017 | 15:10
18 | Thor: Ragnarok                      | 2017 | 14:30
(18 rows)


2. Return ONLY the name column from the 'people' table

SELECT name FROM people;

name         
----------------------
Graeme Brough
Victor Cintron
Eleftheria Koronidi
Edward Ostler
Paul Stewart
Sarah Campbell
Daniel Kelly
Jeff Bridges
Angus Malloch
Steven Ward
Daniel Conner
Jonathan Cruickshank
Emma Roberts
Elanor McCulloch
Chris Murphy
Deborah Gemmell
Gene BaMaung
Jim Bevington
Christine Lester
(19 rows)


3. Oops! Someone at CodeClan HQ spelled Jean's name wrong! Change it to reflect the proper spelling ('Gene BaMaung' should be 'Jean BaMaung').

UPDATE people SET name = 'Jean BaMaung' WHERE name = 'Gene BaMaung';
SELECT name FROM people;

name         
----------------------
Graeme Brough
Victor Cintron
Eleftheria Koronidi
Edward Ostler
Paul Stewart
Sarah Campbell
Daniel Kelly
Jeff Bridges
Angus Malloch
Steven Ward
Daniel Conner
Jonathan Cruickshank
Emma Roberts
Elanor McCulloch
Chris Murphy
Deborah Gemmell
Jim Bevington
Christine Lester
Jean BaMaung
(19 rows)


4. Return ONLY your name from the 'people' table.

Did this a couple of ways, not sure which is more appropriate.

SELECT name FROM people WHERE name = 'Steven Ward';

name     
-------------
Steven Ward
(1 row)


SELECT name FROM people WHERE id = 10;

name     
-------------
Steven Ward
(1 row)


SELECT name FROM people LIMIT 1 OFFSET 9;

name     
-------------
Steven Ward
(1 row)




5. The cinema is showing 'Batman Begins', but Batman is DC, not Marvel! Delete the entry from the 'movies' table.

DELETE FROM movies WHERE title = 'Batman Begins';
SELECT * FROM movies;

id |                title                | year | show_time
----+-------------------------------------+------+-----------
 1 | Iron Man                            | 2008 | 18:10
 2 | The Incredible Hulk                 | 2008 | 20:10
 3 | Iron Man 2                          | 2010 | 19:05
 4 | Thor                                | 2011 | 21:45
 5 | Captain America: The First Avenger  | 2011 | 17:50
 6 | Avengers Assemble                   | 2012 | 15:20
 7 | Iron Man 3                          | 2013 | 21:00
 8 | Thor: The Dark World                | 2013 | 19:35
10 | Captain America: The Winter Soldier | 2014 | 16:25
11 | Guardians of the Galaxy             | 2014 | 21:20
12 | Avengers: Age of Ultron             | 2015 | 21:00
13 | Ant-Man                             | 2015 | 22:00
14 | Captain America: Civil War          | 2016 | 19:30
15 | Doctor Strange                      | 2016 | 20:30
16 | Guardians of the Galaxy 2           | 2017 | 21:40
17 | Spider-man: Homecoming              | 2017 | 15:10
18 | Thor: Ragnarok                      | 2017 | 14:30
(17 rows)

6. Create a new entry in the 'people' table with the name of one of the instructors.

INSERT INTO people (name) values ('Steve Meiklejohn');
SELECT * FROM people;

id |         name         
----+----------------------
 1 | Graeme Brough
 2 | Victor Cintron
 3 | Eleftheria Koronidi
 4 | Edward Ostler
 5 | Paul Stewart
 6 | Sarah Campbell
 7 | Daniel Kelly
 8 | Jeff Bridges
 9 | Angus Malloch
10 | Steven Ward
11 | Daniel Conner
12 | Jonathan Cruickshank
13 | Emma Roberts
14 | Elanor McCulloch
15 | Chris Murphy
16 | Deborah Gemmell
17 | Gene BaMaung
18 | Jim Bevington
19 | Christine Lester
20 | Steve Meiklejohn
(20 rows)

7. Jeff Bridges has decided to hijack our movie evening, Remove him from the table of people.

DELETE FROM people WHERE name = 'Jeff Bridges';
SELECT * FROM people;

id |         name         
----+----------------------
 1 | Graeme Brough
 2 | Victor Cintron
 3 | Eleftheria Koronidi
 4 | Edward Ostler
 5 | Paul Stewart
 6 | Sarah Campbell
 7 | Daniel Kelly
 9 | Angus Malloch
10 | Steven Ward
11 | Daniel Conner
12 | Jonathan Cruickshank
13 | Emma Roberts
14 | Elanor McCulloch
15 | Chris Murphy
16 | Deborah Gemmell
17 | Gene BaMaung
18 | Jim Bevington
19 | Christine Lester
(18 rows)

8. The cinema has just heard that they will be holding an exclusive midnight showing of 'Avengers: Infinity War'!! Create a new entry in the 'movies' table to reflect this. (The year should be 2018)

INSERT INTO movies (title, year, show_time) VALUES ('Avengers: Infinity War', 2018, '00:00');
SELECT * FROM movies;

id |                title                | year | show_time
----+-------------------------------------+------+-----------
 1 | Iron Man                            | 2008 | 18:10
 2 | The Incredible Hulk                 | 2008 | 20:10
 3 | Iron Man 2                          | 2010 | 19:05
 4 | Thor                                | 2011 | 21:45
 5 | Captain America: The First Avenger  | 2011 | 17:50
 6 | Avengers Assemble                   | 2012 | 15:20
 7 | Iron Man 3                          | 2013 | 21:00
 8 | Thor: The Dark World                | 2013 | 19:35
 9 | Batman Begins                       | 2005 | 13:30
10 | Captain America: The Winter Soldier | 2014 | 16:25
11 | Guardians of the Galaxy             | 2014 | 21:20
12 | Avengers: Age of Ultron             | 2015 | 21:00
13 | Ant-Man                             | 2015 | 22:00
14 | Captain America: Civil War          | 2016 | 19:30
15 | Doctor Strange                      | 2016 | 20:30
16 | Guardians of the Galaxy 2           | 2017 | 21:40
17 | Spider-man: Homecoming              | 2017 | 15:10
18 | Thor: Ragnarok                      | 2017 | 14:30
19 | Avengers: Infinity War              | 2018 | 00:00
(19 rows)


9. The cinema would also like to make the Guardian movies a back to back feature. Update the 'Guardians of the Galaxy' show time from 15:30 to 20:00

UPDATE movies SET show_time = '20:00' WHERE title = 'Guardians of the Galaxy';
SELECT * FROM movies;

id |                title                | year | show_time
----+-------------------------------------+------+-----------
 1 | Iron Man                            | 2008 | 18:10
 2 | The Incredible Hulk                 | 2008 | 20:10
 3 | Iron Man 2                          | 2010 | 19:05
 4 | Thor                                | 2011 | 21:45
 5 | Captain America: The First Avenger  | 2011 | 17:50
 6 | Avengers Assemble                   | 2012 | 15:20
 7 | Iron Man 3                          | 2013 | 21:00
 8 | Thor: The Dark World                | 2013 | 19:35
 9 | Batman Begins                       | 2005 | 13:30
10 | Captain America: The Winter Soldier | 2014 | 16:25
12 | Avengers: Age of Ultron             | 2015 | 21:00
13 | Ant-Man                             | 2015 | 22:00
14 | Captain America: Civil War          | 2016 | 19:30
15 | Doctor Strange                      | 2016 | 20:30
16 | Guardians of the Galaxy 2           | 2017 | 21:40
17 | Spider-man: Homecoming              | 2017 | 15:10
18 | Thor: Ragnarok                      | 2017 | 14:30
11 | Guardians of the Galaxy             | 2014 | 20:00
(18 rows)



## Extension

1. Research how to delete multiple entries from your table in a single command.

DELETE FROM movies WHERE title = 'Iron Man' OR title = 'Iron Man 2' OR title = 'Iron Man 3';
SELECT * FROM movies;

id |                title                | year | show_time
----+-------------------------------------+------+-----------
 2 | The Incredible Hulk                 | 2008 | 20:10
 4 | Thor                                | 2011 | 21:45
 5 | Captain America: The First Avenger  | 2011 | 17:50
 6 | Avengers Assemble                   | 2012 | 15:20
 8 | Thor: The Dark World                | 2013 | 19:35
 9 | Batman Begins                       | 2005 | 13:30
10 | Captain America: The Winter Soldier | 2014 | 16:25
11 | Guardians of the Galaxy             | 2014 | 21:20
12 | Avengers: Age of Ultron             | 2015 | 21:00
13 | Ant-Man                             | 2015 | 22:00
14 | Captain America: Civil War          | 2016 | 19:30
15 | Doctor Strange                      | 2016 | 20:30
16 | Guardians of the Galaxy 2           | 2017 | 21:40
17 | Spider-man: Homecoming              | 2017 | 15:10
18 | Thor: Ragnarok                      | 2017 | 14:30
(15 rows)
