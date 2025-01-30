Unix shell programming language.

The `|` pipe operator is used for function composition.
```bash
# redirect stderr to stdout, >& passes output to a file descriptor
./program 2>&1 ( | grep test)

# see redirected / piped stdout (duplicate output)
echo "Hi" | tee file1 (file2 ...)
```