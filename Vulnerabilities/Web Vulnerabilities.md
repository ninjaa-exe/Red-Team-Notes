
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

# Vulnerabilidades
## Directory and files Bruteforce
Com o dirbuster é possível encontrar diretórios e arquivos escondidos no host através de bruteforce

## Method Bypass
É possível ver o conteúdo de uma página que é necessário acesso administrativo utilizando outro método para acessar. Exemplo: Fazer uma requisição POST via curl para a página específicada

## Source Code Analysis
É possível encontrar informações confidenciais através do código fonte da página e das suas subpáginas


## Open Redirect
Em casos que o redirecionamento é feito pelo parâmetro GET e seja passível de mudar a URL, o hacker pode alterar o link para um site malicioso ou para o que ele desejar. Algumas vezes, o parâmetro de redirecionamento está codificado em base64, MD5, etc. , mas isso também é possível burlar descobrindo a codificação e colocando no parâmetro o link codificado


## SQL Injection
Para testar se existe um SQL Injection, um método é colocar o contrabarra ou uma aspa simples nos campos de login e senha 
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
### Cross Site Scripting (XSS) - Refletido
Utilizando o mesmo conceito do HTML Injection, é possível também injetar códigos javascript no servidor para executar códigos no servidor. O XSS Refletido se dá por que o atacante cria uma URL maliciosa e precisa enviar para uma vítima, não é feito nenhuma gravação no banco de dados da página

### Stored XSS
Quando o XSS é armazenado em algum lugar, por exemplo os comentários de feedback,  e com isso, é possível roubar os cookies de outros usuários enviando eles para o próprio servidor 

### XSStrike
O XSStrike é uma ferramenta para automatizar os testes de XSS em um host
Para utilizar ele basta utilizar o comando `python3 xxstrike.py -u host?parameter=`
Link para o github da ferramenta: https://github.com/s0md3v/XSStrike