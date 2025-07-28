## Installation
`sudo apt-get install sqlmap

## How to use
`sqlmap -u "<url>"`

--dbms -> database
--dbs -> mostra todas as bases de dados
--forms -> verifica os formulários da página
--current-db -> mostra a base de dados utilizada
--current-user -> mostra o usuário atual
--users -> mostra todos os usuários
--passwords -> mostra as senhas dos usuários
--os-shell -> consegue uma shell
-D <database> --tables -> mostra todas as tabelas da database
-D <database> -T <table> --columns -> mostra as colunas da tabela
-D <database> -T <table> -C 'columns'-> mostra os dados das colunas 
--dump -> faz o dump das informações
