Flakes are [Nix](Nix.md)'s version of `package.json`, they generate `flake.lock` similiar to `package-lock.json` which locks package versions, Helping produce reproducible environments. To enable flakes put
```nix
nix.settings.experimental-features = ["nix-command" "flakes"]
```
into your [configuration.nix](configuration.nix).  After enabling this, the go-to configuration file changes from `/etc/nixos/configuration.nix` to `/etc/nixos/flake.nix`, and nix will only look at the former when it can't find the flake.

To create a flake from a template, check out the available templates with `nix flake show templates`.  And create one with `nix flake init -t templates#full`.

*Example of a simple configuration flake.nix extending configuration.nix file*
```nix
{
  description = "plan9better but nixos is fine";

  inputs = {
    # NixOS official package source, using the nixos-24.11 branch here
    nixpkgs.url = "github:NixOS/nixpkgs/nixos-24.11";
  };

  outputs = { self, nixpkgs, ... }@inputs: {
    nixosConfigurations.bebop = nixpkgs.lib.nixosSystem {
      system = "x86_64-linux";
      modules = [
        ./configuration.nix
      ];
    };
  };
}
```

In this example the configuration's name is *bebop*, [NixOS](NixOS.md) by default will look for an attribute in the return value of the outputs function named the same as the system hostname (by default "nixos"). So change the hostName in [configuration.nix](configuration.nix) and for the first time run `sudo nixos-rebuild switch --flake /etc/nixos#bebop`. With bebop substituted for yout configs name. If you changed the hostname in [configuration.nix](configuration.nix) then after reboot hostname will change and the part *after* "switch" is not necessary anymore. (You can also directly reference a github repo as flake source instead of a file path `sudo nixos-rebuild switch --flake github:plan9better/nixos#bebop`)

### Flake structure
- Inputs Specifies dependencies of the flake. This attribute set will be passed to the outputs function after they are fetched. Those dependencies can be:
    1. Git repository (as in example)
    2. Local path
    3. Another flake
    Here we only define a dependency named nixpkgs, which is the most common way to reference in a flake, i.e., github:owner/name/reference. The reference here can be a branch name, commit-id, or tag. After declaring this attribute we can use it as an argument passed into the outputs function which is exactly what out example does.
    - Outputs is a function that takes an attribute set from inputs and returns an attribute set which represents the build results of the flake.
        - The *self* parameter of the outputs function, refers to this functions output / return value as well as the source tree of the flake.
    - By default flakes search for a *flake.nix* file in the root directory of each of it's dependencies (i.e each item in inputs) and lazily evaluates their outputs function, and then passes that functions return value to it's own outputs function. You can look at a flake (e.g. the [nixos-24.11](https://github.com/NixOS/nixpkgs/blob/nixos-24.11/flake.nix) flake) to see what you can expect its output function to return. In the flake mentioned before you see that it has a *lib* attribute, which in turn has a *nixosSystem* attribute, so we can use them in out flake.
        1. `system`: This is straightforward, it's the system architecture parameter.
        2. `modules`: This is a list of [[Nix modules|modules]], where the actual NixOS system configuration is defined. The `/etc/nixos/configuration.nix` configuration file itself is a Nixpkgs Module, so it can be directly added to the `modules` list for use.