Represents an optional value.

Either 
- `Some` (contains value)
- `None` (does not)
you can pattern match it like:
```rust
let someval: Option<T> = whatever.method();
match someval{
    Some(x) => println!("{x}");
    None => println!("Nothing");
}
```

`.expect()` also works here the same as in [Result](Result)
```rust
let someval: T  = whatever.method().expect("Return value or panic");
```