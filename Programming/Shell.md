## Shell Commands

|                                                   |                                                    |                                            |
| ------------------------------------------------- | -------------------------------------------------- | ------------------------------------------ |
| Command                                           | Function                                           | Exemple                                    |
| ls                                                | Show the directories                               | ls /home/guilherme/Downloads               |
| cd                                                | Muda o diretório                                   | cd Documents/                              |
| mkdir                                             | Cria um diretório                                  | mkdir pasta                                |
| rmdir                                             | Remove um diretório                                | ==`rmdir pasta`==                          |
| ==`pwd`==                                         | Diz o pathname                                     | ==`pwd`==                                  |
| ==`man`==                                         | Manual do comando passado por parâmetro            | ==`man ls`==                               |
| ==`history`==                                     | Mostra o histórico de comandos                     | ==`history`==                              |
| ==`mv`==                                          | Move ou renomeia um diretório                      | `==mv pasta Pasta==` ou `==mv pasta ~==`   |
| ==`rm`==                                          | Remove um arquivo                                  | ==`rm linux.txt`==                         |
| ==`touch`==                                       | Cria um arquivo vazio                              | ==`touch linux.txt`==                      |
| ==`cp`==                                          | Cria uma cópia de um arquivo                       | ==`cp linux.txt /home/guilherme`==         |
| ==`cat`==                                         | Exibe o conteúdo de um arquivo                     | ==`cat linux.txt`==                        |
| ==`tac`==                                         | Exibe o conteúdo de um arquivo de forma inversa    | ==`tac linux.txt`==                        |
| ==`head`==                                        | Mostra as 10 primeiras linhas de um arquivo        | ==`head linux.txt`==                       |
| ==`tail`==                                        | Mostra as 10 últimas linhas de um arquivo          | ==`tail linux.txt`==                       |
| ==`file`==                                        | Exibe informações de um arquivo                    | ==`file linux.txt`==                       |
| ==`whatis`==                                      | Explica o que determinado comando faz              | ==`whatis file`==                          |
| ==`find`==                                        | Busca por arquivos em uma hierarquia de diretórios | ==`find ~ -name linux.txt`==               |
| ==`cal`==                                         | Exibe o calendário                                 | ==`cat 2023`==                             |
| ==`date`==                                        | Exibe a data atual                                 | ==`date`==                                 |
| ==`grep`==                                        | Busca palavras em um arquivo de texto              | ==`grep linux linux.txt`==                 |
| ==`more`==                                        | Faz a paginação de um arquivo                      | ==`cat linux.txt \| more`==                |
| ==`arch`==                                        | Exibe a arquitetura do kernel                      | ==`arch`==                                 |
| ==`free`==                                        | Exibe a memória física e a swap                    | ==`free`==                                 |
| ==`reboot`==                                      | Reinicia o sistema                                 | ==`reboot`==                               |
| ==`shutdown`==                                    | Desliga o sistema                                  | ==`shutdown -h now`==                      |
| ==`uname`==                                       | Exibe o nome e arquitetura do Kernel do sistema    | `==uname -r ou uname -m==`                 |
| `==lscpu==`                                       | Exibe informações do processador                   | `==lscpu==`                                |
| `==lspci==`                                       | Exibe as placas PCI conectadas                     | `==lspci==`                                |
| `==lsusb==`                                       | Exibe todos os USB conectados                      | `==lsusb==`                                |
| ==`lshw`==                                        | Exibe informações de hardware                      | ==`lshw`==                                 |
| `==ifconfig==`                                    | Mostra as configurações dos adaptadores de rede    | `==ifconfig==`                             |
| `==route==`                                       | Mostra a tabela de roteamento                      | `==route -n==`                             |
| `==netstat==`                                     | Mostra os serviços de rede                         | `==netstat==`                              |
| `==nano==`                                        | É um editor de texto                               | `==nano calendario==`                      |
| `==leafpad==`                                     | É um editor de texto gráfico                       | `==leafpad calendario==`                   |
| `==apt update -> apt upgrade==`                   | Atualiza todos os pacotes                          | `==apt update -> apt upgrade==`            |
| `==apt remove==`                                  | Remove um programa                                 | `==apt remove xvnc4viewer==`               |
| `==dpkg==`                                        | Lista quais aplicativos tem instalado              | `==dpkg -l==`                              |
| `==locate==`                                      | Localiza onde um arquivo se encontra               | `==locate sshd_config==`                   |
| `==whereis==`                                     | Localiza onde um arquivo se encontra               | `==whereis nmap==`                         |
| `==updatedb==`                                    | Atualiza o banco de dados do locate                | `==updatedb==`                             |
| `==awk==`                                         | Filtra as colunas em arquivos de texto             | `==awk -F : ''{print $1}' calendario==`    |
| ==`netstat`==                                     | Exibe as portas abertas                            | ==`netstat -nlpt`==                        |
| ==`find <dir> -type f -exec grep '<word>' {} +`== | Procura alguma palavra em algum diretório          | ==`find / -type f -exec grep 'KEY' {} +`== |

## Operators

|   |   |
|---|---|
|**==Operador==**|**==Função==**|
|==`>`==|Redireciona a saída de um comando para outro comando ou arquivo|
|==`>>`==|Redireciona a saída e adiciona a mesma para um comando ou arquivo|
|==`<`==|Direciona a entrada de um arquivo para a saída de outro comando|
|==`\|`==|Envia a saída de um comando para entrada de outro|
|==`&`==|Permite executar dois comandos e separar suas saídas no terminal|
|==`&&`==|Usado para que dois comandos só sejam executados se o primeiro for executado com sucesso|


## Shortcuts

|   |   |
|---|---|
|**==Atalho==**|**==Função==**|
|==`Ctrl + Alt + T`==|Abre o terminal|
|`==Ctrl + C==`|Cancela o comando atual|
|`==Ctrl + Z==`|Pausa o comando atual|
|`==Ctrl + D==`|Fecha o terminal|
|`==Ctrl + W==`|Apaga uma palavra na linha|
|`==Ctrl + U==`|Apaga toda a linha|
|`==Ctrl + R==`|Busca um comando recente|
|==`Ctrl + L`==|Limpa o terminal|
|==`!!`==|Repete o último comando|

## Directories

|   |   |
|---|---|
|**==Diretório==**|**==Função==**|
|==`/bin/`==|Executáveis principais dos usuários|
|==`/boot/`==|Arquivos do sistema de boot|
|==`/dev/`==|Arquivos de dispositivos|
|==`/etc/`==|Arquivos de configuração do sistema|
|==`/home/`==|Diretório dos usuários comuns do sistema|
|==`/lib/`==|Bibliotecas essenciais do sistema e os módulos do Kernel|
|==`/media/`==|Diretório de montagem e dispositivos|
|==`/mnt/`==|Mesmo que media|
|==`/opt/`==|Instalação de programas não oficinais da distribuição|
|==`/sbin/`==|Armazena arquivos executáveis que representam comandos administrativos (ex: shutdown)|
|==`/srv/`==|Diretório para dados de serviços fornecidos pelo sistema|
|==`/tmp/`==|Diretório para arquivos temporários|
|==`/usr/`==|Segunda hierarquia do sistema, onde ficam os usuários comuns do sistema e programas|
|==`/var/`==|Diretório com arquivos variáveis gerados pelos programas do sistema|
|==`/root/`==|Diretório do usuário root|
|==`/proc/`==|Diretório virtual controlado pelo Kernel|