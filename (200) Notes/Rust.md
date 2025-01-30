Memory safety baby, strong types baby. Rust's main feature is it's compiler and [[Ownership system (Rust)]].

### Creating a project
- `cargo init` creates a project in current directory (can make a git repo with `--git`)
- `cargo new <projectname>` creates a new directory with the project inside and by default will init a git repo.
Both methods put the source code in `src/main.rs` and create a *cargo.toml* with the following info:

```toml
[package]
name = "folder name"
version = "0.1.0"
edition = "2021"

[dependencies]
```

Run the code with `cargo run`

### Basic syntax
- `let x = 3;` creates a variable x (constant)
- `let mut x = 3` creates a mutable variable x
- `println!("Hi");` writes to stdout
- `use std::io;` imports a library (io in this case)
- `let mut str = String::new()` calls a function *new* associated with the type *String* to create a new mutable variable initialized to an empty string.
### User input
- `io::stdin().read_line(&mut str);` calls the function *read_line* from the return of the function *stdin* (handle to std input) which is part of package *io* returns. If we hadn’t imported the `io` library with `use std::io;` at the beginning of the program, we could still use the function by writing this function call as `std::io::stdin`
- *read_line* returns an instance of **Result** type, this instance can have a value of *Ok* or *Err*. You can call the method *.expect("Shit went south")* which if the value is *Err* will crash the program and print the value passed as an argument.  Otherwise if the value is *Ok* it will return that value. In case of *read_line* number of bytes of user input.
### Using packages
- add the package to `[dependencies]` section of `cargo.toml`:
```toml
[dependencies]
rand = "0.8.5"
```

### Types
- [[Option]]
- Const has to have explicit type assigned on declaration + can't use `mut`
- [[Result]]
- [[Array]]
- [[Tuple]]