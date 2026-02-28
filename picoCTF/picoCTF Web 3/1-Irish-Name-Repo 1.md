##  Irish-Name-Repo 1
## Descripcion
Do you think you can log us in? Try to see if you can login!http://fickle-tempest.picoctf.net:50426.
## Solucion SQL

 Pasamos el cuadro de login, poniendo cualquiera de las siguientes cadenas en el nombre de usuario:

`admin' ; admin' or 1=1;`

picoCTF{s0m3_SQL_85832275}

## Notas

#### SQL Injection

SQL injection is a code injection technique that might destroy your database.

SQL injection is one of the most common web hacking techniques.

SQL injection is the placement of malicious code in SQL statements, via web page input.


#### SQL Injection Based on 1=1 is Always True

Look at the example above again. The original purpose of the code was to create an SQL statement to select a user, with a given user id.

If there is nothing to prevent a user from entering "wrong" input, the user can enter some "smart" input like this:

UserId: 

Then, the SQL statement will look like this:

SELECT * FROM Users WHERE UserId = 105 OR 1=1;
The SQL above is valid and will return ALL rows from the "Users" table, since **OR 1=1** is always TRUE.
#### SQL in Web Pages

SQL injection usually occurs when you ask a user for input, like their username/userid, and instead of a name/id, the user gives you an SQL statement that you will **unknowingly** run on your database.

Look at the following example which creates a `SELECT` statement by adding a variable (txtUserId) to a select string. The variable is fetched from user input (getRequestString):
## Referencias:

- SQL Injection: [https://www.w3schools.com/sql/sql_injection.asp](https://www.w3schools.com/sql/sql_injection.asp "https://www.w3schools.com/sql/sql_injection.asp")

