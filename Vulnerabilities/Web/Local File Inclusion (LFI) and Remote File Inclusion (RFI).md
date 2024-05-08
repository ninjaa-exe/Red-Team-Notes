# Full Path Disclosure | Path Traversal | Directory Traversal
Path Traversal or Directory Traversal is a vulnerability that occurs when it is possible to navigate between directories through a GET parameter through the URL using the ".. /" to list all previous directories. Through this vulnerability, it is possible to find sensitive files that, if placed in the URL, can see their contents and find confidential information
## Local File Inclusion (LFI)
Local File Inclusion occurs when the user is able to include and execute local files on the server, manipulating the parameters of the request to include malicious files in the application code. In code that adds a file extension to the end of the request, it is possible to circumvent it by adding a nullbyte (%00) to the end of the request.

### Remote Code Execution através de LFI
Remote code injection through the server logs file is possible if the server interprets the code passed to the log. In the following example, the code calls the system function and through the GET parameter, executes the parameter-passed code remotely on the server.

PHP Code Example: `<?php system($_GET['parameter']); ?>`

## Remote File Inclusion (RFI)
Remote File Inclusion occurs when the server executes code remotely from another server, so it is possible to upload a server and send malicious code to the server, to execute code remotely through a parameter, just like in RCE through LFI