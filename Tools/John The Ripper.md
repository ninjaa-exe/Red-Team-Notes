## Installation
`sudo apt-get install john`

## How to use
`john <parameters> <file>`

## Cheat Sheet
| **Parameter**       | **Usage**            |
| ------------------- | -------------------- |
| --format=hashtype   | Set the hash type    |
| --wordlist=wordlist | Set the wordlist     |
| --stdout > new file | Output to a new file |

## Unshadow
The unshadow tool in John the Ripper is used to merge the /etc/passwd and /etc/shadow files on Unix-like operating systems, such as Linux. These files contain user account information and hashed passwords, respectively. By merging these files, unshadow creates a single file that combines the username, password hash, and other relevant information in a format that John the Ripper can process more efficiently for password cracking purposes. This streamlined data structure helps John the Ripper to perform faster and more effective password cracking attempts.

## How to use
`unshadow passwd shadow > unshadow`

## How to discover the hash type
`hashid file`
`hashcat file`
`hash-identifier`

