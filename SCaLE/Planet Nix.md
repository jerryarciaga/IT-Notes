# Intro to Nix
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
