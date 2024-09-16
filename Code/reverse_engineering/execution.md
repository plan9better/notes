Program executes by loading itself into memory and then instruction by instruction the cpu fetches the [[opcodes|machine code]] of the program from RAM ==(**fetch-execute cycle**)==.
==[[asm|Instruction pointer (ip)]]== points to the place in memory where the next instruction is waiting for the cpu to fetch it.

Example of program execution on linux:
- `./app` calls ==execve("Path to file")== syscall which takes us to the kernel space which loads it and does some setup for it as well as trying to identify the binaries format. If it succeeds it goes to the next step
- Starts a new process