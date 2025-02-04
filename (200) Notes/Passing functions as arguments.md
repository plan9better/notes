```cpp
// Function that takes a pointer to a function returning int and taking two ints
int compute(int a, int b, int (*operation)(int, int)) {
    return operation(a, b);
}

int add(int x, int y) { return x + y; }

int main() {
    int result = compute(3, 4, add);  // Pass function pointer
    return 0;
}
```
