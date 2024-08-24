Hashes são uma forma de guardar as senhas no banco de dados de forma mais segura, o conceito consiste em aplicar um algoritmo hash na senha registrada pelo usuário, e dessa forma guardar no banco de dados. Outro exemple de uso dos hashes são para a integridade de arquivos, para isso, é aplicado um algoritmo hash em um arquivo e disponibilizado publicamente este hash, caso alguém queira utilizar o programa e verificar se houve alguma alteração nesse programa, basta verificar se o hash é compatível com o seu.
# Hashes no Windows
## Exemplo de Hashes no Windows
Na imagem é possível observar exemples de como os hashes são armazenas em sistemas Windows. O Usuário representa o nome da conta, seu ID, sendo 500 sempre para o administrador, o hash LM (Lan Manager), utilizado para sistemas antigos, sendo considerado inseguro e não utilizado na maioria dos casos, e por fim o hash NTLM (NT Lan Manager) que é utilizado para armazenar a senha do usuário <br>
![[HashesWindowsExample.png]]
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
- Obter os arquivos e usá-los para obter os hashes, para depois descobrir os hashes obtidos
- Senhas em memória/cache
- Pass The Hash, uma técnica para utilizar o hash sem precisar quebrá-lo
- Captura de hashes na rede através da ferramenta "responder"

---
# Hashes no Linux
# Sites para quebrar hashes
https://hashes.com/en/decrypt/hash
https://md5decrypt.net/en/

