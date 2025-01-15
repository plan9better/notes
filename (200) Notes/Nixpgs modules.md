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

This is a [Nix](Nix.md) function definition.