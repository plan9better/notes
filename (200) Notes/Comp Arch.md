Course is run on dosbox emulator of ms dos operating system. It runs on a 16 bit intel i4.. architecture. The CPU has 20 pins 4 of which are used for determining the type of operation and the remaining 16 are the 16 bits. Each cell in RAM is 1MB. To debug we will use [[Insight Debugger|Insight Debugger]] and to compile [[nasm]].

## example workflow
- in wsl open nvim in `C:\Users\lain\Desktop\dosbox` + right directory.
- write [[example ASM|asm code]]
- `cd .. & cd dir` (if new file still not present `CTRL + F4` or restart dosbox)
- compile with `nasm -o test.com test.asm` (com for compiled)
- Debug with `insight test.com`