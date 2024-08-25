# O que são Hashes?
Hashes são uma forma de guardar as senhas no banco de dados de forma mais segura, o conceito consiste em aplicar um algoritmo hash na senha registrada pelo usuário, e dessa forma guardar no banco de dados. Outro exemple de uso dos hashes são para a integridade de arquivos, para isso, é aplicado um algoritmo hash em um arquivo e disponibilizado publicamente este hash, caso alguém queira utilizar o programa e verificar se houve alguma alteração nesse programa, basta verificar se o hash é compatível com o seu.
# Hashes no Windows
## Exemplo de Hashes no Windows
Na imagem é possível observar exemples de como os hashes são armazenas em sistemas Windows. O Usuário representa o nome da conta, seu ID, sendo 500 sempre para o administrador, o hash LM (Lan Manager), utilizado para sistemas antigos, sendo considerado inseguro e não utilizado na maioria dos casos, e por fim o hash NTLM (NT Lan Manager) que é utilizado para armazenar a senha do usuário.


![Exemplo de Hashes no Windows](HashesWindowsExample.png)
*Créditos a Desec Security* 
## Arquivos
As senhas dos usuários no Windows são armazenas em 3 principais arquivos, sendo eles:

SAM - Security Account Manager (Windows)
- Armazena as contas de usuários
- %SystemRoot%/system32/config/sam

NTDS.DIT (Windows Server/Active Directory)
- Armazena dados do AD incluindo as contas de usuários
- %SystemRoot%/ntds/ntds.dit

System
- Arquivo do sistema necessário para decriptar o SAM/NTDS.DIT
- %SystemRoot%/system32/config/system

### Problemas
Um grande problema com os arquivos é que todos eles são bloqueados em execução, portanto é impossível acessar ou copiar eles, porém, existem algumas soluções para isso.

### Soluções
- No diretório C:/Windows/repair em sistemas antigos existe um backup do arquivo SAM e do arquivo System, porém nem sempre esse arquivo é atualizado (apenas sistemas antigos como XP/2003)
- Salvar direto do registro do Windows através do comando reg save hklm/sam (funciona para todas as versões do Windows)
- Fazer uma cópia sombra do volume com a ferramenta "vssadmin" (apenas para versões mais recentes)

### Ataques
- Pass The Hash, uma técnica para utilizar o hash sem precisar quebrá-lo
- Captura de hashes na rede através da ferramenta "responder"

#### Registro do Windows
Este é o meio mais utilizado de todos para se obter os hashes de usuários, utilizado tanto em sistemas antigos quanto em sistemas modernos. Através do registro do Windows, é possível consultar os arquivos SAM ou NTDS.DIT e o SYSTEM e criar novos arquivos a partir deles, para isso é utilizado os comandos `reg save hklm\sam samNOVO` e `reg save hklm\system systemNOVO`. Depois de criar os novos arquivos, pode-se baixar estes e utilizar a ferramenta "samdump2", para sistemas antigos, com o comando `samdump2 system sam/ntds.dit` para obter os hashes dos usuários. Em sistemas mais modernos, o "impacket-secretsdump" pode ser utilizado para se descobrir os hashes de usuários, basta utilizar o comando `impacket-secretsdump -sam sam -system system` que ele já fornecerá os hashes.
#### Senhas em memória/cache
Para esse tipo de ataque, é necessário baixar os arquivos SAM ou NTDS.DIT e o SYSTEM no diretório C:/Windows/repair, após feito o download desses arquivos, é possível utilizar a ferramenta "samdump2" para obter os hashes de usuários do sistema, o comando ficará o seguinte `samdump2 system sam/ntds.dit`. Um adendo importante em relação a esse ataque é que nem sempre os hashes obtidos estarão atualizados, visto que os arquivos armazenados no diretório são apenas um backup dos verdadeiros.

---
# Hashes no Linux
# Sites para quebrar hashes
[Quebra de diversos hashes](https://hashes.com/en/decrypt/hash)

[Quebra de MD5](https://md5decrypt.net/en/)

