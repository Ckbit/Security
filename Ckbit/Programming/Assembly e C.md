---
folder: "[[Programming]]"
---
Assembly é uma linguagem de programação de baixo nível que está intimamente ligada ao código de máquina específico de uma arquitetura de computador. Cada instrução em assembly geralmente corresponde a uma instrução única em código de máquina, permitindo um controle preciso sobre o hardware. Isso é particularmente útil em situações que exigem otimizações de desempenho crítico ou manipulação direta de componentes de hardware, como em sistemas embarcados, drivers de dispositivos e kernels de sistemas operacionais.



Programar em assembly requer um entendimento profundo da arquitetura do processador, incluindo registradores, modos de endereçamento e instruções específicas. Embora ofereça alto desempenho e controle, a programação em assembly é propensa a erros e menos produtiva devido à sua complexidade e verbosidade em comparação com linguagens de alto nível.



A linguagem C, por outro lado, é considerada uma linguagem de programação de médio nível. Desenvolvida nos anos 1970, C combina características de linguagens de alto e baixo nível. Ela permite manipulação direta de memória através de ponteiros e oferece estruturas de controle de alto nível como loops e condicionais, facilitando o desenvolvimento de software complexo.



C é amplamente utilizada para o desenvolvimento de sistemas operacionais, aplicativos de sistemas e software embarcado devido à sua eficiência e portabilidade. O código escrito em C pode ser compilado para rodar em diversas arquiteturas com poucas modificações, o que não é facilmente alcançável com assembly.



Em resumo, enquanto assembly oferece controle máximo sobre o hardware ao custo de complexidade e portabilidade, C proporciona um equilíbrio entre desempenho e facilidade de uso, tornando-se uma escolha popular para desenvolvimento de software onde eficiência e controle são importantes.







Esse é um exemplo de código assembly para a arquitetura x86 que imprime "Hello, World!" na tela usando o sistema operacional Linux:

```
section .data
msg db 'Hello, World!', 0xA ; Mensagem a ser exibida seguida por uma nova linha
len equ $ - msg ; Comprimento da mensagem

section .text
global _start

_start:
mov eax, 4 ; Chamada do sistema para sys_write
mov ebx, 1 ; File descriptor 1 (saída padrão)
mov ecx, msg ; Endereço da mensagem
mov edx, len ; Comprimento da mensagem
int 0x80 ; Interrupção do sistema

mov eax, 1 ; Chamada do sistema para sys_exit
mov ebx, 0 ; Código de saída 0
int 0x80 ; Interrupção do sistema
```

**Explicação do código:**

- **section .data**: Declara a seção de dados onde armazenamos a mensagem a ser impressa.
- **msg db 'Hello, World!', 0xA**: Define a string "Hello, World!" seguida por um caractere de nova linha (0xA em hexadecimal).
- **len equ $ - msg**: Calcula o comprimento da mensagem.
- **section .text**: Declara a seção de código onde o código executável é colocado.
- **global \_start**: Define o ponto de entrada do programa.

No rótulo **\_start**:

1. **mov eax, 4**: Coloca o número da chamada do sistema sys\_write no registrador eax.
2. **mov ebx, 1**: Define o file descriptor como 1 (saída padrão).
3. **mov ecx, msg**: Passa o endereço da mensagem para o registrador ecx.
4. **mov edx, len**: Passa o comprimento da mensagem para o registrador edx.
5. **int 0x80**: Invoca a interrupção do sistema para executar a chamada sys\_write.
6. **mov eax, 1**: Coloca o número da chamada do sistema sys\_exit no registrador eax.
7. **mov ebx, 0**: Define o código de saída como 0 (sem erros).
8. **int 0x80**: Invoca a interrupção do sistema para terminar o programa.

**Como compilar e executar:**

Salve o código acima em um arquivo chamado hello.asm. Em um ambiente Linux com o assembler NASM instalado, execute os seguintes comandos no terminal:

```bash
nasm -f elf32 hello.asm -o hello.o
ld -m elf_i386 hello.o -o hello
./hello
```

- **nasm -f elf32 hello.asm -o hello.o**: Monta o código assembly em um objeto de 32 bits.
- **ld -m elf\_i386 hello.o -o hello**: Liga o objeto e produz um executável de 32 bits.
- **./hello**: Executa o programa, que deverá imprimir "Hello, World!" na tela.

**Nota:** Este exemplo é para sistemas de 32 bits. Em sistemas de 64 bits, as chamadas de sistema e registradores são diferentes. Certifique-se de ajustar o código ou usar um ambiente compatível.

