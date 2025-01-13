Known for being a successor of B.
### Input / Output
```cpp
fgets(buf, sizeof(buf),  [[Streams|stream]])
```
reads at most sizeof(buf) - 1 bytes or until a newline, leaves room for null terminator
```
testing123(enter)
-> "Testing123\n\0"
```

### String formatting

```cpp
strncpy(src, dest, maxline)
```
Copies src to dest, at most maxline characters.

```cpp
snprintf(result, maxline, "format %s\n", args)
```
copies into result, at most maxline characters that result from the format
