Functional, lazy, statically typed programming language.
## Functions
In Haskell functions play a key role. They work a bit like math functions, a function can only take 1 argument at a time but you can make it seem like it takes more by currying, that is function composition. For example:
```haskell
mysin x y = sin x + y
```
Is a function  that takes a number $x$ and returns a function that takes a number  $y$ and adds it to $\sin{x}$. So really there is no need to think of it like math functions but it is sometimes helpful.

### Infix, prefix and postfix functions.
Functions can also be infix, prefix and postfix. Usually functions are prefix like in example above, but $*$ is a function (specifically a function that multiplies two numbers), and it is infix. You can turn a prefix function into an infix function by surrounding it with backticks, a good example is the div function which does integer division (div 92 10 -> 9) but there may be some confusion as to which number is being devided so for clarity you may write:
```haskell
x = 92 `div` 10
```
Which will evaluate to 9.

### Conditionals
In haskell conditions have to be functions, additionally the `else` part is **necessary**:
```haskell
softmaxpartial x = if x < 0 
            then 0
            else x
```

### Variables
Variables are functions that don't have input arguments, just return a value.
```haskell
myvar = 10 + 83
myvar' = "myvar"
```

### Lists
Lists are homogenous (store values of the same type, e.g. "thisstring" is a list of characters)