Simplified [Nixpkgs](Nixpkgs.md) module:
```nix
{lib, config, options, pkgs, ...}:
{
  # Importing other Modules
  imports = [
    # ...
    ./xxx.nix
  ];
  for.bar.enable = true;
  # Other option declarations
  # ...
}
```
### Inputs
- *lib*: std library
- *config* set of all options' values in the current environment
- *options* all options of all modules in the current environment
- *pkgs* collection of all nixpkgs packages.

If you need to pass non-default arguments use *specialArgs*:
```nix
{
  inputs = {
    nixpkgs.url = "github:NixOS/nixpkgs/nixos-24.11";
    another-input.url = "github:username/repo-name/branch-name";
  };

  outputs = inputs@{ self, nixpkgs, another-input, ... }: {
    nixosConfigurations.my-nixos = nixpkgs.lib.nixosSystem {
      system = "x86_64-linux";

      # Set all inputs parameters as special arguments for all submodules,
      # so you can directly use all dependencies in inputs in submodules
      specialArgs = { inherit inputs; };
      modules = [
        ./configuration.nix
      ];
    };
  };
}
```

or the same way with *_module.args* 
and then receive those values in the module:
```nix
# Nix will match by name and automatically inject the inputs
# from specialArgs/_module.args into the third parameter of this function
{ config, pkgs, inputs, ... }:
{
  # ...
}
```
