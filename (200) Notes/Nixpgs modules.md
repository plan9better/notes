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

This is a [Nix](Nix.md) function definition. And it takes 4 arguments by default (Automatically generated, automatically injected, declaration free):
- *lib* is a collection of useful functions, included with [Nixpkgs](Nixpkgs.md).
- *config* is a set of all options' valus in the current environment
- *options* is a set of all options' in all modules in the environment
- *pkgs* is a collection containing all packages in [Nixpkgs](Nixpkgs.md) + a few utility functions.
- *modulesPath*: A parameter available only in NixOS, which is a path pointing to [nixpkgs/nixos/modules](https://github.com/NixOS/nixpkgs/tree/nixos-24.11/nixos/modules).
    - It is defined in [nixpkgs/nixos/lib/eval-config-minimal.nix#L43](https://github.com/NixOS/nixpkgs/blob/nixos-24.11/nixos/lib/eval-config-minimal.nix#L43).
    - It is typically used to import additional NixOS modules and can be found in most NixOS auto-generated `hardware-configuration.nix` files.
    
    The Nixpkgs module system provides two ways to pass non-default parameters:
1. The `specialArgs` parameter of the `nixpkgs.lib.nixosSystem` function
2. Using the `_module.args` option in any module to pass parameters