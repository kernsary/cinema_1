# SQL Homework

The Springfield Cinema is having a Marvel Movie Marathon! They have asked you to help maintain their database of movies with times and attendees.

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

Use the supplied data as the source of data to answer the questions. Copy the SQL command you have used to get the answer, and paste it below the question, along with the result they gave.

## Questions

1.  Return ALL the data in the 'movies' table.

marvel=# SELECT * FROM movies
id |                title                | year | show_time
----+-------------------------------------+------+-----------
  1 | Iron Man                            | 2008 | 17:00
  2 | The Incredible Hulk                 | 2008 | 23:55
  3 | Iron Man 2                          | 2010 | 18:45
  4 | Thor                                | 2011 | 15:45
  5 | Captain America: The First Avenger  | 2011 | 14:15
  6 | Avengers Assemble                   | 2012 | 14:45
  7 | Iron Man 3                          | 2013 | 21:55
  8 | Thor: The Dark World                | 2013 | 22:55
  9 | Batman Begins                       | 2005 | 13:40
 10 | Captain America: The Winter Soldier | 2014 | 18:25
 11 | Guardians of the Galaxy             | 2014 | 13:10
 12 | Avengers: Age of Ultron             | 2015 | 20:20
 13 | Ant-Man                             | 2015 | 13:00
 14 | Captain America: Civil War          | 2016 | 12:35
 15 | Doctor Strange                      | 2016 | 22:00
 16 | Guardians of the Galaxy 2           | 2017 | 14:05
 17 | Spider-Man: Homecoming              | 2017 | 23:00
 18 | Thor: Ragnarok                      | 2017 | 22:10
 19 | Black Panther                       | 2018 | 21:00
(19 rows)

2.  Return ONLY the name column from the 'people' table

marvel=# SELECT name FROM people;
         name         
----------------------
 Homer Simpson
 Marge Simpson
 Lisa Simpson
 Maggie Simpson
 Patty Bouvier
 Selma Bouvier
 Kent Brockman
 Ned Flanders
 Barney Gumble
 Itchy
 Eric Cartman
 Scratchy
 Crusty the Clown
 Montgomery Burns
 Mayor Joe Quimby
 Groundskeeper Willie
(16 rows)

3.  Oops! Someone spelled Krusty The Klown's name wrong! Change it to reflect the proper spelling (Crusty should be Krusty).

marvel=# UPDATE people SET name = 'Krusty the Clown' WHERE name = 'Crusty the Clown';
UPDATE 1
marvel=# SELECT name FROM people;
         name         
----------------------
 Homer Simpson
 Marge Simpson
 Lisa Simpson
 Maggie Simpson
 Patty Bouvier
 Selma Bouvier
 Kent Brockman
 Ned Flanders
 Barney Gumble
 Itchy
 Eric Cartman
 Scratchy
 Montgomery Burns
 Mayor Joe Quimby
 Groundskeeper Willie
 Krusty the Clown
(16 rows)

4.  Return ONLY Homer Simpson's name from the 'people' table.

marvel=# SELECT * FROM people
marvel-# ;
 id |         name         
----+----------------------
  1 | Homer Simpson
  2 | Marge Simpson
  3 | Lisa Simpson
  4 | Maggie Simpson
  5 | Patty Bouvier
  6 | Selma Bouvier
  7 | Kent Brockman
  8 | Ned Flanders
  9 | Barney Gumble
 10 | Itchy
 11 | Eric Cartman
 12 | Scratchy
 14 | Montgomery Burns
 15 | Mayor Joe Quimby
 16 | Groundskeeper Willie
 13 | Krusty the Clown
(16 rows)

marvel=# SELECT name FROM people WHERE id = 1;
     name      
---------------
 Homer Simpson
(1 row)

5.  The cinema is showing 'Batman Begins', but Batman is DC, not Marvel! Delete the entry from the 'movies' table.

marvel=# DELETE FROM movies WHERE id = 9;
DELETE 1
marvel=# SELECT * FROM movies
marvel-# ;
 id |                title                | year | show_time
----+-------------------------------------+------+-----------
  1 | Iron Man                            | 2008 | 17:00
  2 | The Incredible Hulk                 | 2008 | 23:55
  3 | Iron Man 2                          | 2010 | 18:45
  4 | Thor                                | 2011 | 15:45
  5 | Captain America: The First Avenger  | 2011 | 14:15
  6 | Avengers Assemble                   | 2012 | 14:45
  7 | Iron Man 3                          | 2013 | 21:55
  8 | Thor: The Dark World                | 2013 | 22:55
 10 | Captain America: The Winter Soldier | 2014 | 18:25
 11 | Guardians of the Galaxy             | 2014 | 13:10
 12 | Avengers: Age of Ultron             | 2015 | 20:20
 13 | Ant-Man                             | 2015 | 13:00
 14 | Captain America: Civil War          | 2016 | 12:35
 15 | Doctor Strange                      | 2016 | 22:00
 16 | Guardians of the Galaxy 2           | 2017 | 14:05
 17 | Spider-Man: Homecoming              | 2017 | 23:00
 18 | Thor: Ragnarok                      | 2017 | 22:10
 19 | Black Panther                       | 2018 | 21:00
(18 rows)

6.  We forgot one of the main characters! Add Bart Simpson to the 'people' table

marvel=# INSERT INTO people (name) VALUES ('Bart Simpson');
INSERT 0 1
marvel=# SELECT * FROM people;
id |         name         
----+----------------------
 1 | Homer Simpson
 2 | Marge Simpson
 3 | Lisa Simpson
 4 | Maggie Simpson
 5 | Patty Bouvier
 6 | Selma Bouvier
 7 | Kent Brockman
 8 | Ned Flanders
 9 | Barney Gumble
10 | Itchy
11 | Eric Cartman
12 | Scratchy
14 | Montgomery Burns
15 | Mayor Joe Quimby
16 | Groundskeeper Willie
13 | Krusty the Clown
17 | Bart Simpson
(17 rows)

7.  Eric Cartman has decided to hijack our movie evening, Remove him from the table of people.

marvel=# DELETE FROM people WHERE id = 11;
DELETE 1
marvel=# SELECT * FROM people;
 id |         name         
----+----------------------
  1 | Homer Simpson
  2 | Marge Simpson
  3 | Lisa Simpson
  4 | Maggie Simpson
  5 | Patty Bouvier
  6 | Selma Bouvier
  7 | Kent Brockman
  8 | Ned Flanders
  9 | Barney Gumble
 10 | Itchy
 12 | Scratchy
 14 | Montgomery Burns
 15 | Mayor Joe Quimby
 16 | Groundskeeper Willie
 13 | Krusty the Clown
 17 | Bart Simpson
(16 rows)

8.  The cinema has just heard that they will be holding an exclusive midnight showing of 'Avengers: Infinity War'!! Create a new entry in the 'movies' table to reflect this.

marvel=# INSERT INTO movies (title, year, show_time) VALUES ('Avengers: Infinity War', 2019, '00:00');
INSERT 0 1
marvel=# SELECT * FROM movies;
 id |                title                | year | show_time
----+-------------------------------------+------+-----------
  1 | Iron Man                            | 2008 | 17:00
  2 | The Incredible Hulk                 | 2008 | 23:55
  3 | Iron Man 2                          | 2010 | 18:45
  4 | Thor                                | 2011 | 15:45
  5 | Captain America: The First Avenger  | 2011 | 14:15
  6 | Avengers Assemble                   | 2012 | 14:45
  7 | Iron Man 3                          | 2013 | 21:55
  8 | Thor: The Dark World                | 2013 | 22:55
  9 | Batman Begins                       | 2005 | 13:40
 10 | Captain America: The Winter Soldier | 2014 | 18:25
 11 | Guardians of the Galaxy             | 2014 | 13:10
 12 | Avengers: Age of Ultron             | 2015 | 20:20
 13 | Ant-Man                             | 2015 | 13:00
 14 | Captain America: Civil War          | 2016 | 12:35
 15 | Doctor Strange                      | 2016 | 22:00
 16 | Guardians of the Galaxy 2           | 2017 | 14:05
 17 | Spider-Man: Homecoming              | 2017 | 23:00
 18 | Thor: Ragnarok                      | 2017 | 22:10
 19 | Black Panther                       | 2018 | 21:00
 20 | Avengers: Infinity War              | 2019 | 00:00
(20 rows)

9.  The cinema would like to make the Iron Man movies a triple billing. Find out the show time of "Iron Man 2" and set the show time of "Iron Man 3" to start two hours later.

marvel=# UPDATE movies SET show_time ='20:45' WHERE id = 7;
UPDATE 1
marvel=# SELECT * FROM movies;
 id |                title                | year | show_time
----+-------------------------------------+------+-----------
  1 | Iron Man                            | 2008 | 17:00
  2 | The Incredible Hulk                 | 2008 | 23:55
  3 | Iron Man 2                          | 2010 | 18:45
  4 | Thor                                | 2011 | 15:45
  5 | Captain America: The First Avenger  | 2011 | 14:15
  6 | Avengers Assemble                   | 2012 | 14:45
  8 | Thor: The Dark World                | 2013 | 22:55
  9 | Batman Begins                       | 2005 | 13:40
 10 | Captain America: The Winter Soldier | 2014 | 18:25
 11 | Guardians of the Galaxy             | 2014 | 13:10
 12 | Avengers: Age of Ultron             | 2015 | 20:20
 13 | Ant-Man                             | 2015 | 13:00
 14 | Captain America: Civil War          | 2016 | 12:35
 15 | Doctor Strange                      | 2016 | 22:00
 16 | Guardians of the Galaxy 2           | 2017 | 14:05
 17 | Spider-Man: Homecoming              | 2017 | 23:00
 18 | Thor: Ragnarok                      | 2017 | 22:10
 19 | Black Panther                       | 2018 | 21:00
 20 | Avengers: Infinity War              | 2019 | 00:00
  7 | Iron Man 3                          | 2013 | 20:45
(20 rows)


## Extension

1.  Research how to delete multiple entries from your table in a single command

Use DELETE but after WHERE use multiple ids or another condition eg id >= 80
