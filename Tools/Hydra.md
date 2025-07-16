## Installation
`sudo apt-get install hydra`

## How to use
`hydra <parameters> <service> 172.16.1.60 smb`

## Cheat Sheet

| **Parameter**   | **Usage**                                       |
| --------------- | ----------------------------------------------- |
| -v              | Verbose Mode                                    |
| -l user         | Set a user                                      |
| -L userlist     | Set a user list                                 |
| -p password     | Set a password                                  |
| -P passwordlist | Set a password list                             |
| -M hostslist    | Set a host list                                 |
| -s port         | Set a port                                      |
| -t number       | Set a number of tasks in parallel               |
| -W number       | Set a time between each connection (needs -t 1) |
