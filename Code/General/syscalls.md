ask the OS kernel to perfrom some action (read from keyboard, write to screen) through a [[software_interrupt]]


usermode:
    printf("Hello, world!");
syscall:
    please write this string for me

On linux, check the [[software_interrupt]] table and prepare registers as needed.
To syscall exit:
```asm
mov eax, 0x1    ; exit software interrupt code
mov ebx, 0x9    ; argument to pass
int 0x80        ; check the table and do the syscall ??