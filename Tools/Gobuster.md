## Installation
`sudo apt-get install gobuster`

## Cheat Sheet

| **Parameter** | **Usage**                 | **Exemple**                                        |
| ------------- | ------------------------- | -------------------------------------------------- |
| -w            | Set a wordlist            | gobuster dir -u https://example.com -w rockyou.txt |
| -x            | Set the formats           | gobuster dir -u https://example.com -x .php,.sh    |
| -t            | Set the number of threads | gobuster dir -u https://example.com -t 50          |
| -c            | Set a cookie              | gobuster dir -u https://example.com -c 8a3c5n      |

