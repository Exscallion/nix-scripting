# Absolute basics of NixOS and the Nix scripting language.

This tutorial assumes you have installed NixOS and can run nix:
```
$ nix --version
nix (Nix) 2.31.2 
```

## Using nix-shell

With nix-shell you can create a temporary shell environment with extra packages that are not installed system wide.
Nix manages these packages per shell, even can setup an auto clean in the configuration.
To spin up a shell with an extra package, you can run the following:

```
$ nix-shell -p cowsay
```

Upon running the command, you will notice Nix downloading the cowsay dependency.
Cowsay should be available in the nix-shell, and if you exit the nix-shell (by writing `exit` or using CTRL + D), you cannot run cowsay (unless you had it installed previously).
 
This is part of the Nix package manager and not neccessarily to do with NixOS.
Nix can be used on any Linux distro and is not limited to NixOS.

##

