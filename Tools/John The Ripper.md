## Installation
`sudo apt-get install john`

## Cheat Sheet
| Parameter           | Usage                | Exemple                              |
| ------------------- | -------------------- | ------------------------------------ |
| --format=hashtype   | Choose the hash type | john --format=Raw-MD5 file.txt       |
| --wordlist=wordlist | Choose the wordlist  | john --wordlist=rockyou.txt file.txt |
| --stdout > new file | Output to a new file | john --format=Raw-MD5 file.txt > md5 |

## Unshadow
The unshadow tool in John the Ripper is used to merge the /etc/passwd and /etc/shadow files on Unix-like operating systems, such as Linux. These files contain user account information and hashed passwords, respectively. By merging these files, unshadow creates a single file that combines the username, password hash, and other relevant information in a format that John the Ripper can process more efficiently for password cracking purposes. This streamlined data structure helps John the Ripper to perform faster and more effective password cracking attempts.

## How to use
`unshadow passwd shadow > unshadow`

## How to discover the hash type
`hashid file`
`hashcat file`

