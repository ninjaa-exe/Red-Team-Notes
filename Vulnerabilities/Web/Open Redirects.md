Em alguns casos onde o redirecionamento é feito pelo parâmetro GET, o atacante pode mudar o link para um site malicioso ou o que ele quiser. Algumas vezes, o redirecionamento é feito em base64, MD5 ou alguma outra codificação, mas isso também pode ser burlado encontrando a forma de codificação e colocando o link codificado no parâmetro

Exemplo: http://172.16.1.10/turismo/redir.php?url=malicious_site.com
Exemplo: http://172.16.1.10/turismo/redir.php?url=http://172.16.1.5/virus.exe