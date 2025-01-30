Gnu Debugger.

## compiling C code with debug symbols

```
gcc main.c -ggdb
```

## starting gdb

```
gdb exec main
```

## running program

```
r (run)
```

## breakpoints

```
break foo
break main.c:45
info break      # list bp
del (number)    # remove bp 
```

## look at variables

```
info locals (function_name)
print foo (sizeof(foo))
explore foo
```

## check what functions are available
```
info functions
disassemble (func name or address)
```