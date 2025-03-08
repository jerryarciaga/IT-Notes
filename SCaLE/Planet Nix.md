# Intro to Nix
#nixos #SCaLE
## Flakes
Flakes are currently an experimental feature

```
# /etc/nix/nix.conf file
...
experimental-features = nix-command flakes
```

### 2 Files: `flake.nix` and `flake.lock`
* `flake.nix`
```
{
    description = "My first flake";
    inputs.nixpkgs.url = "github:NixOS/nixpkgs/nixos-unstable";

    outputs = { self, nixpkgs }: {
        packages.aarch64-darwin.htop = nixpkgs.legacyPackages.aarch64-darwin.htop;
    }
}
```
`$nix build .#htop`

## Nix language
* Attribute sets
* Multiline strings -- two single quotes in the beginning and the end
* List can have different data types inside it
* `let in` -- allows defining variable
### Functions
```
let
  sum = arg1: arg2: arg1 + arg2;
in
  sum 1 2
```
### Note on environment variables
It's possible to use environment variables; however, this may go against reproducibility
## Evaluating nix expressions
* You can evaluate inline: `$ nix eval --expr '1 + 2'`
* Or a file full of nix expressions: `$ nix eval --file example.nix`

## `mkShell` -- Development environment
* This allows you to drop into a dev shell with certain tools installed
```
{
...
  outputs = { self, nixpkgs }:
    let 
      system = "aarch64-linux";
      pkgs = nixpkgs.legacyPackages.${system};
    in {
      devShells.${system} = {
        nodejs = pkgs.mkShell {
          packages = [ pkgs.nodejs ];
        };
        python = pkgs.mkShell {
          packages = [ pkgs.python3 pkgs.poetry ];
        };
      };
    };
...
}
```
* To use it, you can now do:
`$ nix develop .#nodejs` or `$ nix develop .#python`
* NOTE: You can also use `default` as one of the attribute sets of `devShells.${system}` so you only have to invoke `$ nix develop` to drop into that shell.

## Custom Package - `mkDerivation`
* Capture every thing that a package needs and store it into `/nix/store`

# Nix on Python? Yes you can!
## Projects
### Python-nix
* Lightweight wrapper build upon C
* [Python nix](https://github.com/tweag/python-nix)
* Forked by presenter: [Python-Nix (fork)](https://github.com/fusiled/python-nix)
* Seems not maintained anymore
## Examples
### A simple override

# Evaluating nix evaluators
## `benchmarking-nix-eval`
* Nix flake for benchmarking the Nix flake
* Matrix nix packages and configurations through flakes
* Runs `time nix eval` inside the sandbox `n` times

# Configurable Flakes
## Flakes
* Way to distribute Nix artifacts
* Git repo with a `flake.nix` in it
* Exact dependencies are recorded in a lock file
## Goals
* Reproducibility
* Composable
* Extensible
* "Just works"
* Discoverable