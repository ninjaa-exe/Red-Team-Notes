## Installation
`sudo apt-get install nmap`

## How to use
`nmap <parameters> <hosts>`

## Cheat Sheet

| **Parameter**      | **Usage**                            | **Exemple**                       |
| ------------------ | ------------------------------------ | --------------------------------- |
| -v                 | Verbose mode                         | nmap -v 192.168.1.10              |
| -sV                | Shows the version                    | nmap -sV 192.168.1.10             |
| -Pn                | Don't verifies if the hosts is alive | nmap -Pn 192.168.1.10             |
| -sS                | SYN scan                             | nmap -sS 192.168.1.10             |
| -sU                | UDP scan                             | nmap -sU 192.168.1.10             |
| -sF                | FIN scan                             | nmap -sF 192.168.1.10             |
| -sX                | XMAS scan                            | nmap -sX 192.168.1.10             |
| -sN                | NULL scan                            | nmap -sN 192.168.1.10             |
| -p port            | Set ports                            | nmap -p21 192.168.1.10            |
| -sn hosts          | Verifies which hosts are alive       | nmap -sn 192.168.1.0/24           |
| --top-ports=number | Set the number of top ports to scan  | nmap --top-ports=10 192.168.1.10  |
| -A                 |                                      | nmap -A 192.168.1.10              |
| -D                 | Decoy mode                           | nmap -D 192.168.1.11 192.168.1.10 |
| -O                 | Verifies the operating system        | nmap -O 192.168.1.10              |
