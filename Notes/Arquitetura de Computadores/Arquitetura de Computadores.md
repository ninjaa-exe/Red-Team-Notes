## CPU
É responsável por realizar as operações lógicas do computador e todo o processamento, é o cérebro do computador

## Machine Code
É um conjunto de instruções que a CPU processa, essas instruções são representadas em formato hexadecimal

## Assembly
O machine code pode ser traduzido para um código mais legível conhecido como Assembly, cada CPU tem seu próprio conjunto de instruções conhecido como Instruction Set Architecture (ISA)

## Arquiteturas
Cada CPU tem um conjunto de registradores que são pequenos locais para ler e manipular dados de uma forma extremamente rápida

- x86 - Processadores de 32 bits com 4 bytes de largura
- x64 - Processadores de 64 bits (x86_64 / AMD64) com 8 bytes de largura

### Registradores

![Registradores em diferentes arquiteturas](Registradores.png)

## Processo em memória
Quando um processo executa ele é carregado e organizado an memória

![Processo na memória](Processo_memoria.png)

## Assembler
É o programa que traduz a linguagem assembly em código de máquina. Após usar um assembler será gerado um **object file**, que é uma representação binária do programa. Um **linker** vai combinar os arquivos necessários para gerar o executável final.

Exemplo: Um código que utiliza uma função externa da User32.dll após gerar o object file, precisará do linker para que o programa consiga usar as funções em User32.dll, o linker por sua vez vai resultar em um arquivo final executável

Assemblers: NASM e MASM
Linkers: GoLink e Id

### Processo
![Processo do Assembler](Processo_assembler.png)