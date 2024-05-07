## Reflected 
Using the same concept as HTML Injection, it is also possible to inject javascript code into the server to execute code on the server. Reflected XSS is because the attacker creates a malicious URL and needs to send it to a victim, no write is made to the page's database

## Stored 
When XSS is stored somewhere, for example feedback comments, it is possible to steal other users' cookies by sending them to the server itself

### XSStrike
O XSStrike é uma ferramenta para automatizar os testes de XSS em um host
Para utilizar ele basta utilizar o comando `python3 xsstrike.py -u "host?parameter="` ou `python3 xsstrike.py -u "host" --params` para XSS Refletido e o comando `python3 xsstrike.py -u "host/" --path` para Self XSS

Link para o download da ferramenta: https://github.com/s0md3v/XSStrike

XSStrike is a tool for automating XSS testing on a host To use it just use the command `python3 xsstrike.py -u "host?parameter="` or `python3 xsstrike.py -u "host" --params` for Reflected XSS and the command `python3 xsstrike.py -u "host/" --path` for Self XSS 

Link to download the tool: https://github.com/s0md3v/XSStrike