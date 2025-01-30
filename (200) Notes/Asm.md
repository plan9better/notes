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

# Writing code

## Sections

| Section Name | Description                                                                     | Info                                                                 | Notes                                                       |
| ------------ | ------------------------------------------------------------------------------- | -------------------------------------------------------------------- | ----------------------------------------------------------- |
| .text        | Contains the code of the program                                                | Executable by the CPU                                                | Read-only to prevent modification                           |
| .data        | Houses the static data of the program that will be modified by during execution | Usually stores globals and initialized data                          | Most likely will be read-write                              |
| .bss         | Stores uninitialized data                                                       | Variables sizes in the section are known but values are 0 at runtime | Saves memory because you don't need to initialize variables |
| .rdata       | Stores read-only data                                                           | Data is not modified during execution                                | Primary purpose is to hold constant data                    |
## Hello world

```nasm

; declare the entrypoint of the program itself
global _start
;
; the keyword global makes the label (in this case _start) accessible from outside the current program.
; This keyword tells the linker where the program starts
;

; initialized data section (readable and writeable data)
section .data
    ; align the data in a 2-byte boundary - allows better memory access 
	align 2
	
	; define a string followed by a newline character
	hello: db 'Hello world!', 0xa
	
	; calculate the length of the string by subtracing from the current address
	helloLen: equ $-hello 
;
; this section stores the data that will be used through the program. The align mnemonic ensures that the 
; string 'Hello, World!' is aligned on a 2-byte boundary for easier memory access. It also houses the length
; of the string.
;

; store uninitialized data
section .bss 
; 
; since there is no data that "may" be used, this section is empty
; 

; store the actual code of the program
section .text
	
	; define the entrypoint where the program starts execution
	_start:
	  
	  ; syscall for sys_write
  	  mov eax, 0x4 
  	  
  	  ; file descriptor for stdout
	  mov ebx, 0x1  
	  
	  ; address of the initialized string
	  mov ecx, hello  
	  
	  ; length of the intialized string
	  mov edx, helloLen
	  
	  ; interrupt to make linux syscall  
	  int 0x80  
	  
	  ; syscall for sys_exit
	  mov eax, 0x1  
	  
	  ; exit status 0
	  xor ebx, ebx
	  
	  ; interrupt to make syscall  
	  int 0x80
	  ;
	  ; this intruction is used to trigger and interrupt and allows you to invoke a system call from 
	  ; user space to kernel space. Basically we are requesting the OS for services.
	  ; This stops the processing and switches into kernel mode (ring0).
	  ;
;
; this section contains the actual program code. It starts with the _start label as the entrypoint
; and makes multiple sys_calls. It then exits the program with an interrupt.
;

```
### 1. `hello:`

This defines a **label** named `hello`. In assembly, labels are used to mark memory locations. The label `hello` refers to the address where the string `'Hello world!'` is stored.

### 2. `db`

- **`db`** stands for "Define Byte."
- It is used to define a series of bytes that will be stored in memory.
- In this case, the bytes represent the ASCII values of the characters in the string `'Hello world!'`, followed by `0xa` (which is a newline character in hexadecimal).
### 3. `0xa`

- This is a **hexadecimal** representation of the number `10` (decimal), which corresponds to the ASCII newline character (`'\n'`).
- In this context, it is used to signify the end of the string with a newline.
### 4. `equ`

- **`equ`** stands for "equate."
- It is a directive used to assign a value to a label or symbol at **assembly time**.
- Unlike variables, which store values in memory, symbols defined with `equ` are constant and evaluated by the assembler during compilation.

### 5. `$`

- **`$`** represents the **current address** or **current location counter**. It points to the memory address the assembler is currently processing.
- In this case, `$` is used to get the memory address right after the string `"Hello world!\n"` has been defined.
### 6. `helloLen: equ $-hello`

This line calculates the length of the string stored in the label `hello`:

- **`$`** gives the memory address right after the string (the end of the string).
- **`hello`** is the address where the string starts.
- The expression `$ - hello` calculates the number of bytes between the current address (after the string) and the starting address of the string.

This difference gives the **length of the string**, which is stored in `helloLen`. Since the string is `12` characters long (`"Hello world!"`) plus a newline character (`0xA`), the total length would be 13 bytes.

# compiling and running

```bash
nasm -f elf32 -o filename.o filename.asm
ld -m elf_i386 -o filename filename.o
./filename
```

# functions
make a function anythwere in the file by adding a label: `hello: ` and some instructions under it. finish it with `ret`. ret is automatically pushed onto the stack, remember when popping of the stack with [bp + offset] 
```asm
section .text

writeHello:
	mov eax, 0x4
	mov ebx, 0x1
	mov ecx, hello
	mov edx, helloLen
	int 0x80
	ret

writeBye:
	mov eax, 0x4
	mov ebx, 0x1
	mov ecx, goodbye
	mov edx, byeLen
	int 0x80
	ret

_start:
	mov eax, 0x4
	mov ebx, 0x4
	cmp eax, ebx
	je equal
	jne notEqual

equal:
	call writeHello
	jmp endProgram

notEqual:
	call writeBye

endProgram:
	; return 0
	mov eax, 0x1
	xor ebx, ebx
	int 0x80
```
