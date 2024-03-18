## Installation
`sudo apt-get install gobuster`

## Cheat Sheet

| **Parameter** | **Usage**                    | **Exemple**                                        |
| ------------- | ---------------------------- | -------------------------------------------------- |
| -w            | Choose a wordlist            | gobuster dir -u https://example.com -w rockyou.txt |
| -x            | Choose the formats           | gobuster dir -u https://example.com -x .php,.sh    |
| -t            | Choose the number of threads | gobuster dir -u https://example.com -t 50          |
