# registers
```asm
ip    ; instruction pointer, points to the next instruction for the cpu to execute

# instructions
```asm
mov (register), (value)    ; set register to value
add (register), (value or register)   ; the result is stored in the register
jmp (address e.g. 0x10)    ; jump to an instruction at address, ip = 0x10
int 0x2    ; check the IVT/IDT and do the [[software_interrupt]] found at 0x2
iret    ; return the IP to the place it was before the interrupt
```
