In PHP, "wrappers" are mechanisms that allow you to access different types of resources using the same interface. They function as middle layers that encapsulate specific resources, such as files, URLs, dataflows, etc., and provide a consistent way to interact with those resources, regardless of the underlying type.

For example, PHP provides wrappers for accessing local files (e.g., `file://`), remote resources (e.g., `http://` and `ftp://`), as well as other communication protocols. Using these wrappers, you can manipulate local files and remote resources in the same way, using functions such as `file_get_contents()` and `file_put_contents()`, for example.

## Table of Contents

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


More informations: https://www.php.net/manual/en/wrappers.php