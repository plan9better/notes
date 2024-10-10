```asm
org 100h ; set offset to 100 to fix 


mov AH, 09h
mov DX, label
int 21h

mov AH, 00h
int 21h

label db "Patryk Wojnarowski$"
```