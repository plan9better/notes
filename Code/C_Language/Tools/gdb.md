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
```

## look at variables

```
info locals (function_name)
print foo (sizeof(foo))
explore foo
```

