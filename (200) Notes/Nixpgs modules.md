Module for organizing code in the [Nix](Nix.md) language.

Basic structure: 
```nix
{lib, config, options, pkgs, ...}:
{
  # Importing other Modules
  imports = [
    # ...
    ./xxx.nix
  ];
  foo.bar.enable = true;
  # Other option declarations
  # ...
}
```

This is a [Nix](Nix.md) function definition. And it takes 4 arguments:
- *lib* is a collection of useful functions, included with [Nixpkgs](Nixpkgs.md).
- *config* is a set of all options' valus in the current environment
- *options* is a set of all options' in all modules in the environment
- *pkgs* is a collection containing all packages in [Nixpkgs](Nixpkgs.md) + a few utility functions.