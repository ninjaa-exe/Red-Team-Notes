Em PHP, "wrappers" são mecanismos que permitem acessar diferentes tipos de recursos usando a mesma interface. Eles funcionam como camadas intermediárias que encapsulam recursos específicos, como arquivos, URLs, fluxos de dados, etc., e fornecem uma maneira consistente de interagir com esses recursos, independentemente do tipo subjacente.

Por exemplo, o PHP fornece wrappers para acessar arquivos locais (por exemplo, `file://`), recursos remotos (por exemplo, `http://` e `ftp://`), bem como outros protocolos de comunicação. Usando esses wrappers, você pode manipular arquivos locais e recursos remotos da mesma forma, usando funções como `file_get_contents()` e `file_put_contents()`, por exemplo

Exemplo: http://rh.businesscorp.com.br/index.php?page=data://text/plan;base64,PD9waHAgc3lzdGVtKGlkKTs/Pg== (<?php system(id);?> em base64)
# Tabela de Wrappers

| Wrapper   | Function                        |
| --------- | ------------------------------- |
| file://   | Accessing local filesystem      |
| http://   | Accessing HTTP(s) URLs          |
| ftp://    | Accessing FTP(s) URLs           |
| php://    | Accessing various I/O streams   |
| zlib://   | Compression Streams             |
| data://   | Data (RFC 2397)                 |
| glob://   | Find pathnames matching pattern |
| phar://   | PHP Archive                     |
| ssh2://   | Secure Shell 2                  |
| rar://    | RAR                             |
| ogg://    | Audio streams                   |
| expect:// | Process Interaction Streams     |

Mais informações: https://www.php.net/manual/en/wrappers.php