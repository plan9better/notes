Nix is a package manager as well as a functional declarative language for reproducible and [[declarative]] environments. It is also the base of [[NixOS]].
In the Nix language you use [[Nixpkgs]] [[Nixpgs modules|modules]], to orgnize the code into modules.

The nix language has a function *import* which has a special attribute that when it's called on a directory instead of a file, it executes the *default.nix* of that directory. Which is similiar to the [Nixpkgs modules](Nixpkgs%20modules.md)' *imports* parameter.