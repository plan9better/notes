[x86re](https://x86re.com/1.html)
# syntax
regular syntax is:
`INSTRUCTION DESTINATION, SOURCE`
if you see dest and source swapped you might be looking at AT&T syntax which is:
`INSTRUCTION SOURCE, DESTINATION`


# Instructions

```asm
mov (register), (value)    ; set register to value
add (register), (value or register)   ; the result is stored in the register
jmp (address e.g. 0x10)    ; jump to an instruction at address, ip = 0x10
int 0x2    ; check the IVT/IDT and do the [[software_interrupt]] found at 0x2
cmp eax, ebx ; compare 2 registers if they are equal the "zero flag (zf)" will be set to 1 and 0 if they are not
jz 0x53298  ; jump to the selected addres if the "zero flag (zf)" is 0. jzn works the other way, jump if not zero
iret    ; return the IP to the place it was before the interrupt
```

# Registers
## Data Registers
- EAX: Accumulator, often for math and return values .
- EBX: Base, often holds function params and indexed addresses .
- ECX: Count, for loop counts (prograrrmers: this is "i") and function params .
- EDX: Data, general use and function params . Internally labeled boxes are subregisters which can be used.
# Index Registers
- ESI: Source Index, often stores constants or used as a pointer.
- EDI: Destination Index, often a destination for data or used as a pointer. Pointers Points to a memory location, generally expressed in hex. Example: Ox40154b.
- ESP: Stack pointer, stores a pointer to top of stack.
- EBP: Base pointer, stores a pointer to base of current stack frame.
## Flags
Certain instructions change flags, which are represented as simple 1 or 0 on a flag register. For example, if we perform an "add" between two numbers, we may have a few outcomes that we need to be aware of. Let's say we compare two values to see if they are equal with CMP EDX, EAX. The "zero flag" will either be set to 1 if they are equal, or 0 if they are not. An instruction like `JZ Ox40154b` that jumps to memory location Ox40154b if the comparison equaled to zero would check this flag. Think of these as boolean variables.
- ZF, "zero flag," set if result is 0.
- SF, "sign flag," set if a result is negative.
- OF, "overflow flag," set if a result was larger than a register can hold. Let us say AL and DL are set to OxFF. `ADD AL, DL` would return a 9 bit character and therefore overflow the 8 bit register.

# Call stack
last in first out so push the arguments in reverse order then call the function and store the result in register
![[callstack.png]]
Stack frames have 4 different parts:
1. Parameters
2. return addres (wherever the funciton what called from)
3. EBP (Base pointer)
4. Local variables

- EBP points to the base of the stack frame
- ESP points to the top of the stack (increases when values are popped of the stack and decreases when values are added to the stack)

Simple Overview:
1. When a function is called, the current EBP is pushed onto the stack.
2. EBP is then assigned the value of ESP; EBP is now the base pointer to access vars and params.
3. As function runs, ESP will change as needed, EBP remains static.
4. As function terminates, ESP is set to EBP. Stack pointer is now set to top of stack to equal the base pointer. This frees memory allocated on the stack for local vars.
5. EBP is now popped from the stack (remember, first in last out,) and EBP can be used again as base pointer.
6. In simpler terms, stack frames contain the EBP value of the functions caller (step 1.) Now we can use EBP register as this function' s base pointer.