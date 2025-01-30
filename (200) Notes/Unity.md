Unity can be exported to 1 of 2 runtimes:
- mono (starts a VM and runs with a JIT compiler) (small to medium games)
- il2cpp (translates to cpp and compiles a native binary) (little harder to hack)

# hacking
- ### mono
open dnSpyEx and patch (don't use 64bit for 32 bit games) can also use melonloader to make mods, use UnityExplorer plugin to check out the values.

- ### il2cpp
use melon loader