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
Output:

![asm_helloworld_output](https://user-images.githubusercontent.com/66387143/122335922-024aa100-cf0a-11eb-9bf5-cbb360011d0c.png)

## Syscalls

https://chromium.googlesource.com/chromiumos/docs/+/master/constants/syscalls.md

# SHORT JUMP (x86) REFERENCE

FF	-1
FE	-2
FD	-3
FC	-4
FB	-5
FA	-6
F9	-7
F8	-8
F7	-9
F6	-10
F5	-11
F4	-12
F3	-13
F2	-14
F1	-15
F0	-16
EF	-17
EE	-18
ED	-19
EC	-20
EB	-21
EA	-22
E9	-23
E8	-24
E7	-25
E6	-26
E5	-27
E4	-28
E3	-29
E2	-30
E1	-31
E0	-32
DF	-33
DE	-34
DD	-35
DC	-36
DB	-37
DA	-38
D9	-39
D8	-40
D7	-41
D6	-42
D5	-43
D4	-44
D3	-45
D2	-46
D1	-47
D0	-48
CF	-49
CE	-50
CD	-51
CC	-52
CB	-53
CA	-54
C9	-55
C8	-56
C7	-57
C6	-58
C5	-59
C4	-60
C3	-61
C2	-62
C1	-63
C0	-64
BF	-65
BE	-66
BD	-67
BC	-68
BB	-69
BA	-70
B9	-71
B8	-72
B7	-73
B6	-74
B5	-75
B4	-76
B3	-77
B2	-78
B1	-79
B0	-80
AF	-81
AE	-82
AD	-83
AC	-84
AB	-85
AA	-86
A9	-87
A8	-88
A7	-89
A6	-90
A5	-91
A4	-92
A3	-93
A2	-94
A1	-95
A0	-96
9F	-97
9E	-98
9D	-99
9C	-100
9B	-101
9A	-102
8F	-103
8E	-104
8D	-105
8C	-106
8B	-107
8A	-108
99	-109
98	-110
97	-111
96	-112
95	-113
94	-114
93	-115
92	-116
91	-117
90	-118
89	-119
88	-120
87	-121
86	-122
85	-123
84	-124
83	-125
82	-126
81	-127
80	-128

![image](https://user-images.githubusercontent.com/66387143/124022161-6f564000-d9ba-11eb-8915-cd8a5d381af9.png)

