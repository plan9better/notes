```asm
org 100h     ; set offset to 100 to fix some nasm macros


mov AH, 09h
mov DX, label
int 21h      ; print string to stdout

mov AH, 00h
int 21h      ; exit program 

label db "Patryk Wojnarowski$"
```