## fgets(buf, sizeof(buf),  [[streams|stream]])
reads at most sizeof(buf) - 1 bytes or until a newline, leaves room for null terminator
```
testing123 
-> "Testing123\n\0"
```

