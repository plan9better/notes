Along with [[hardware_interrupt]] are the 2 types interrupts

Asking the kernel to stop whatever it's doing and do what i want it to.
IVT (interrupt vector table) in [[x86]] and IDT (interrupt descriptor table) in [[x64]]  

![[IVT.png]]

e.g. in [[asm]]:
```asm
int 0x2
```
will check the table and switch to kernel mode to jump the [[asm|IP (instruciton pointer)]] to the place which stores  ==Timer 1== block of code and then 
```asm
iret
```
to switch back to [[security_rings|user mode]] and return to the place it was before the interrupt was triggered