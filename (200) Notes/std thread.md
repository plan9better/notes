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
This program creates a new thread called *my_t* which immediately starts the *hello* function and then waits for the function to finish executing, without the `my_t.join()` the main function could finish execution and return to *libc* where it was started from without waiting for the *hello* function to finish executing and calling `my_t.detach()` would detach it.

*YOU HAVE TO `JOIN` OR `DETACH` THE THREAD BEFORE IT'S DELETED.*

This means that you need to worry about exceptions being thrown.
```cpp
struct func;
void f() {
    int some_local_state=0;
    func my_func(some_local_state);
    std::thread t(my_func);
    try {
        do_something_in_current_thread();
    } catch(...) {
        t.join();
        throw;
    }
    t.join(); }
```

`std::thread`'s constructor parameter takes any callable, including [Function call overloaded objects](Operator%20overloading(CPP)).

When not using *named* variables make sure to avoid accidentaly defining a function instead of getting a value:
```cpp
std::thread my_thread(background_task());
```
declares a `my_thread` function that takes a single parameter of type *pointer-to-a-function-taking-no-parameters-and-returning-a-background_task-object*.
More about [[Passing functions as arguments]].

