Brute force é o método utilizado para tentar descobrir a senha de algum usuário ou serviço através da tentativa e erro, para isso são utilizar ferramentas juntamente com wordlists
## Mutação em Wordlists
O próprio John the Ripper faz mutação em wordlists através do comando `john --wordlist=wordlist --rules --stdout > mutacao`. No arquivo /etc/john/john.conf é também possível adicionar novas regras de mutações na wordlist

## Wordlists personalizadas
O crunch é uma ferramenta capaz de criar wordlists de forma personalizada com base em parâmetros, exemplo: `crunch 10 10 -t senha^%% -o wordlist`
### Parâmetros
- % = Dígitos
- ^ = Caracteres Especiais
- @ = Caracteres Minúsculos
- , = Caracteres Maiúsculos
## Key Space Brute Force
O Key Space Brute Force é uma técnica que busca esgotar todas as possibilidades de senhas até encontrar a senha, ela é muito utilizada para PINs de 4 digitos, ou senhas de somente 6 digitos númericos, para criar uma lista para esse tipo de caso, pode se utilizar o crunch da seguinte maneira `crunch 4 4 0123456789 -o pin`

## Reverse Brute Force
A único diferença do Reverse Brute Force é que ao invés de realizar o ataque de força bruta na senha, se faz no campo de login, visto que nem sempre há uma proteção de brute force no campo de login, mas apenas no campo de senha

## Low Hanging Fruit
A técnica de Low Hanging Fruit se dá por buscar os pontos mais fracos e fáceis dos hosts, utilizando por exemplo credenciais padrões, uma forma de fazer isso é utilizando o hydra da seguinte maneira: `hydra -v -l root -p root -M hosts ssh`

## Hydra
O hydra é uma ferramenta capaz de carregar uma lista de usuário e uma lista de senhas para fazer bruteforce em serviços específicos. Por exemplo `hydra -v -L userlist.txt -P passwordlist.txt 172.16.1.4 smb`