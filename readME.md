# MySQL Commands

**_ SQL will read everything until gets to ';', no matter on how many lines the command is. _**

### Create a database:

`CREATE DATABASE database_name;`

### Remove database:

`DROP DATABASE database_name; - deletes everything`

### Select a database to use it:

`USE database_name;`

### Create a table inside database:

Tables have columns inside of them that represent the different properties of the object.<br />
To create a table we need to tell it what columns to create with. Inside of the () we will put the different columns that we want for our table.<br/>
For each column you need to specify the type of it (string, integer, date, floating point number).

`CREATE TABLE table_name ( test_column INT );`

`CREATE TABLE bands ( id INT NOT NULL AUTO_INCREMENT, name VARCHAR(255) NOT NULL, PRIMARY KEY (id))`
The column can no longer have any null values inside of it. The ID will be created automatically.<br />
The ID will be the identifier of the table so needs to be declared as pimary key.

`CREATE TABLE albums ( id INT NOT NULL AUTO_INCREMENT, name VARCHAR(255) NOT NULL, realease_year INT, band_id INT NOT NULL, PRIMARY KEY (id), FOREIGN KEY (band_id) REFERENCES bands(id))`

The albums table will contain the different albums for our different bands inside of our database.<br />
To connect an album to a band, we need to reference the band table from inside of album table.<br />
First we need to save the id from bands table inside of albums, then we can reference it.<br />
Using Foreign key property we can define the relationship between the band id and band table.<br />

### To change the properties of the table after was created: ex- add another column with type: string

`ALTER TABLE table_name ADD another_column VARCHAR(255)`
This will create a string column with max of 255 characters named another_column.

### Remove Table:

`DROP TABLE table_name;`

### Insert data in table

`INSERT INTO bands (name) VALUES ('stefan');`

To add more than 1 entry: <br />
`INSERT INTO bands (name) VALUES ('stefan1'), ('stefan 2'), ('stefan 3');`

### Query data from table

`SELECT * FROM bands;`

### Query just the fisrt 2 bands

`SELECT * FROM bands LIMIT 2;`

### Query just certain columns

`SELECT name FROM bands`

### Rename the columns

`SELECT id AS 'ID', name AS 'Band Name' from bands;`

### Order the way elements inside SELECT are rendered

`SELECT * FROM bands ORDER BY name;`

### Descening Order the way elements inside SELECT are rendered

`SELECT * FROM bands ORDER BY name DESC;`

### Example of adding more albums

`INSERT INTO albums (name, release_year, band_id) VALUES('album 1', 2000, 1), VALUES('album 2', 2001, 1), VALUES('album 3', 2002, 1), VALUES('album 4', 2003, 2), VALUES('album 5', NULL, 3), `

### Query just the unique rows from table - add DISTINCT

`SELECT DISTINCT name FROM albums;`

### Change a value

`UPDATE albums SET release_year = 1983 WHERE id = 1;`

### Filter what you are selecting from database

`SELECT * FROM albums WHERE release_year <br 2000;`

### Another way to filter - any amount of chars before and after 'er'

`SELECT * FROM albums WHERE name LIKE '%er%'`

### Combine inside of a single query

`SELECT * FROM albums WHERE name LIKE '%er%' OR band_id = 2;`
`SELECT * FROM albums WHERE release_year = 1984 AND band_id = 1;`

### Filter between 2 different values

`SELECT * FROM albums WHERE release_year BETWEEN 2000 and 2018`

### Filter for things that are null

`SELECT * FROM albums WHERE realease_year IS NULL;`

### Delete just one row

`DELETE FROM albums WHRE id = 5;`

### Joint Statement - allows us to join 2 different tables toghether on different properties

`SELECT * FROM bands INNER JOIN albums ON bands.id = albums.band_id;`
Inner join (join) combines data where there is a value on both sides and only return values that will match. <br />

`SELECT * FROM bands LEFT JOIN albums ON bands.id = albums.band_id;`
Left Join will return everything from the left side no matter what. (left side = bands, right side = albums)

`SELECT * FROM bands RIGHT JOIN albums ON bands.id = albums.band_id;`
RIGHT Join will return everything from the right side no matter what.
