C++ standard library multithreading.
```cpp
#include <thread>

void hello(){
    std::cout << "Hello, world!" << std::endl;
}

int main(){
    std::thread my_t(hello);
    my_t.join()
    return 0;
}
```
This program creates a new thread called *my_t* which immediately starts the *hello* function and then waits for the function to finish executing, without the `my_t.join()` the main function could finish execution and return to *libc* where it was started from without waiting for the *hello* function to finish executing. 

`std::thread`'s constructor parameter takes any callable, including [Function call overloaded objects](Operator%20overloading(CPP)).

When 
