Functional, lazy, statically typed programming language.

### TODO:
- Implement some [Data Structures and/or algorithms](Data%20Structures%20and%20Algorithms.md) in haskell and use them in a [Project](Projects.md), for example by making a [Java](Java.md) library in haskell to use [Red Black Trees](Red%20Black%20Trees.md) to store some data. 
- Finish book "Learn [Physics](Physics) with functional programming".

### Introduction
This note is following the online book "[Learn You a Haskell for Great Good!](https://learnyouahaskell.com/)", and is structured mostly like it (That is, in that order).

### Functions
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
Variables are functions that don't have input arguments, just return a value. Therefore all haskell variables are constant.
```haskell
myvar = 10 + 83
myvar' = "myvar"
```

### Lists
Lists are homogenous (store values of the same type, e.g. "thisstring" is a list of characters)

[[Lists (Haskell)|Details]]

List comprehensions are like [Mathemathical](Math.md) set comprehensions (also similiar to [Python](Python.md). e.g. for a set of first 10 even natural numbers:
Math: $S = \{2 \times x | x \in N, x <= 10\}$
Haskell: `S = [2 * x | x <- [1 .. 10]]
Haskell with additional predicate: `S' = [2 * x | x <- [1 .. 10], x * 2 > 12]

### Types
You can create a type alias with the `type` keyword.
```haskell
type R = Double
```

Or complex data types with the `data` keyword. (Using the above type alias)
```haskell
data Shape = Circle R R R | Square R R R R
```
This declares a type shape which can be a *circle* **or** a *square*.
And also provides constructors for both of those (R R R and R R R R).

[Lambda calculus](https://augustss.blogspot.com/2007/10/simpler-easier-in-recent-paper-simply.html)
```haskell
type Sym = String

data Expr
        = Var Sym
        | App Expr Expr
        | Lam Sym Expr
        deriving (Eq, Read, Show)
```
