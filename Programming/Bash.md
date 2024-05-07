
sempre “.sh” no final

sempre começar o script com “#!/bin/bash” que é o interpretador

sempre usar “chmod +x [script.sh](http://script.sh)” para dar permissão de execução

depois é necessário usar “./” antes do arquivo para executar

o “#” é utilizado para comentários

o “$” é utilizado para variável (exemplo: ip = 192.168.0.1, echo “IP:” $ip)

o “echo” exibe texto na tela

o “read” serve para ler uma variável

### IF 
`echo “Qual a cor do semáforo?”`

`read cor`

`if [ ”$cor” == “verde” ]` (tem que ter os espaços)

`then`

`echo “Siga em frente :)”`

`elif [”$cor” == “amarelo”]`

`then`

`echo “Aguarde”`

`else`

`echo “PARE!”`

`fi`

### Switch Case

`echo “O cliente já autorizou o Pentest?”`

`echo “ 1 - Sim”`

`echo “2 - Não”`

`read resp`

`case $resp in`

`“1”)`

`echo “Pode iniciar”`

`“2”`

`echo “Aguarde a autorização”`

`;;`

`esac`

### ARGS

$0 é o script

$1 para primeiro argumento

$2 para segundo argumento

e assim adiante

### Loops

`echo {1 . . 10}`

Output: 1 2 3 4 5 6 7 8 9 10

Same for `echo {a . . z}`

`seq 1 10`

Output: 1 2 3 4 5 6 7 8

9 10

`for ip in {1 . . 10};`

`do`

`echo 192.168.0.$ip;`

`done`

Output:

192.168.0.1
192.168.0.2
192.168.0.3
192.168.0.4
192.168.0.5
192.168.0.6’
192.168.0.7
192.168.0.8
192.168.0.9
192.168.0.10

`while true;`

`do`

`echo “Hacked”;`

`done`

### Portscan

`hping3 -S -p 80 -c 1 192.168.0.1`

-S = SYN

-p = porta

-c 1 = quantidade de pacotes

### HTML Parsing

wget $host

grep http index.html | cut -d “/” -f 3 | grep “\.” | cut -d ‘”’ -f 1 > list

for url in $(cat list); do host $url | grep “has address”; done