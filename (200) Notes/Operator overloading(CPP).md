In [CPP](CPP.md) you can overload operators such as the function call operator `()` by defining an `operator X` function where `X` is the operator. 

e.g. function call operator:
```cpp
class background_task {
public: 
    void operator()() const {
        do_something();
        do_something_else();
    }
};
// in main
background_task f;
std::thread my_thread(f);
```

This creates a callable instance of the class *background_task* which means it can then be passed to [[std thread]]'s constructor.

You can do this with any of the default opearators `(+, -, *, ...)`.
[More examples](https://en.cppreference.com/w/cpp/language/operators).