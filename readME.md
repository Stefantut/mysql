# MySQL Commands

**_ SQL will read everything until gets to ';', no matter on how many lines the command is. _**

### Create a database:

`CREATE DATABASE database_name;`

### Remove database:

`DROP DATABASE database_name; - deletes everything`

### Select a database to use it:

`USE database_name;`

### Create a table inside database:

**_ Tables have columns inside of them that represent the different properties of the object. _**
**_ To create a table we need to tell it what columns to create with. Inside of the () we will put the different columns that we want for our table. _**
**_ For each column you need to specify the type of it (string, integer, date, floating point number)_**

`CREATE TABLE table_name ( test_column INT );`

### To change the properties of the table after was created: ex- add another column with type: string

`ALTER TABLE table_name ADD another_column VARCHAR(255)`
**_ This will create a string column with max of 255 characters named another_column. _**

### Remove Table:

`DROP TABLE table_name;`
