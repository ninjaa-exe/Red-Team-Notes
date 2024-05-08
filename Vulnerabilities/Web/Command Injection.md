This vulnerability occurs when it is possible to inject commands from the operating system that should not be possible through some field. 

Vulnerable code example: whois url  | grep "nserver" 

Example of command injection: whois ; id;# | grep "nserver"