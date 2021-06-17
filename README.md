# OSED-prep
Notes for OSED (EXP-301) course preparation

## x86 ASSEMBLY

Printing "Hello World!".

Code:
```
; hello world asm

global _start

section .text

_start:
        ; print hello world

        mov eax, 0x4 ; syscall for write: ssize_t write(int fd, const void *buf, size_t count);
        mov ebx, 0x1 ; first param: int fd (file descriptor) 0 for stdin, 1 for stdout, 3 for stderror
        mov ecx, message ;second param: const void *buff which is the buffer, in this case, defined in .data section, message.
        mov edx, mlen ; third param: size_t count, which is the lenght of the buffer
        int 0x80 ; syscall

        ; exit the program
        mov eax, 0x1 ; syscall for exit: void _exit(int status);
        mov ebx, 0x5 ; return 5 for exit
        int 0x80 ; syscall

section .data

        message: db "Hello World!"
        mlen    equ $-message
```
Assemble and link:
```
# nasm -f elf32 -o helloworld.o helloworld.asm
# ld -o helloworld helloworld.o
```
