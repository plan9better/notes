```bash
# redirect stderr to stdout, >& passes output to a file descriptor
./program 2>&1 ( | grep test)

# see redirected / piped stdout (duplicate output)
```