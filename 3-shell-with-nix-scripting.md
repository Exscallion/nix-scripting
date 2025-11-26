## Creating a shell with Nix scripting

With Nix we can create a declaration for a shell that is reproducible across systems.
This is meant as a more permanent solution to juggling nix-shell commands.
The declaration of the shell is also written in the Nix language.

Lets take a look at the script:

```nix
let
  nixpkgs = fetchTarball "https://github.com/NixOS/nixpkgs/tarball/nixos-25.05";
  pkgs = import nixpkgs { config = {}; overlays = []; };
in

pkgs.mkShellNoCC {
  packages = with pkgs; [
    cowsay
  ];
}
```


In the let block we define two variables, nixpkgs and pkgs.

nixpkgs is as we know from the previous chapters, it pins the repository to a version.
and pkgs simply imports the packages with with a configuration (config and overlay is the configuration, intentionally left empty).

After the let ... in block, we use the variables to spin up a shell.
This is done via the mkShell function, there are two flavours out there:

`mkShell` A way to construct a shell, including compiler tools to compile C. 
`mkShellNoCC` As you guessed it, same as mkShell without compiler tools, making it more lightweight.

### Executing the nix file.

When your terminal is located at a directory with a shell.nix file, it will be executed when nix-shell is ran.
If you run nix-shell from the directory with shell.nix, you will notice that `cowsay` is available without explicitly specifying it in the -p parameter.

### Shell hooks

You can use `shellHook` to run a command when the nix-shell is invoked.







