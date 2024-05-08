## Installation
`sudo apt-get install nmap`

## How to use
`nmap <parameters> <hosts>`

## Cheat Sheet

| **Parameter**      | **Usage**                            |
| ------------------ | ------------------------------------ |
| -v                 | Verbose mode                         |
| -sV                | Shows the version                    |
| -Pn                | Don't verifies if the hosts is alive |
| -sS                | SYN scan                             |
| -sU                | UDP scan                             |
| -sF                | FIN scan                             |
| -sX                | XMAS scan                            |
| -sN                | NULL scan                            |
| -p port            | Set ports                            |
| -sn hosts          | Verifies which hosts are alive       |
| --top-ports=number | Set the number of top ports to scan  |
| -A                 |                                      |
| -D                 | Decoy mode                           |
| -O                 | Verifies the operating system        |
