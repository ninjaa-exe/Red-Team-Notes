Esta vulnerabilidade ocorre quando é possível injetar comandos do sistema operacional que não deveriam ser possíveis por meio de algum campo

Exemplo de código vulnerável: whois url  | grep "nserver" 

Exemplo de injeção de comando: whois ; id;# | grep "nserver"