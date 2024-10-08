> now archived, superseded by [`comfybyte/patchy`](https://github.com/comfybyte/patchy).

# nyanvim
my [Neovim](https://neovim.io/) configuration, built with [Nixvim](https://github.com/nix-community/nixvim).

## usage
add this repository as an input to your flake:
```nix
{
    inputs.nyanvim.url = "github:comfybyte/nyanvim";
}
```

and then grab a derivation by calling `withConfig` with a set of options normally passed to `programs.nixvim`,
so for [Home Manager](https://github.com/nix-community/home-manager) you can do:
```nix
{ inputs, system, ... }: {
    home.packages = 
    let
        nyanvim = inputs.nyanvim.legacyPackages.{system};
    in
    [
        (nyanvim.withConfig {
            opts.nu = true;
            globals.mapLeader = " ";
            # ...and other `programs.nixvim` options. does override and may be an empty set.
         })
    ];
}
```

et voilá.
