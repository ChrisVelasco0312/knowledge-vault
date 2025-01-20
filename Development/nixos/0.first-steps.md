
## First steps

After install and edit `/etc/nixos/configuration.nix`
Add the core packages to start to edit and navigate the system from the terminal
For me:
```
- ranger or lf
- neovim
- tmux
```

Save and go back to the terminal, execute this command:

`sudo nixos-rebuild switch`

# Flakes

### Basic flakes config and workflow

In the `configuration.nix` file:

`nix.settings.experimental-features = [ "nix-command" "flakes" ]`

Now we have access to flake commands

- Create a `.dotfiles` directory in `$HOME`
- `cp /etc/nixos/configuration.nix .`
- `cp /etc/nixos/hardware-configuration.nix .`

#### Create a flake

```nix
{
  description = "My first flake!";
  
  # some git repos
  inputs = {
   nixpkgs.url = "github:NixOS/nixpkgs/nixos-23.05";
  };
  
  # your built and working system config
  outputs = { self, nixpkgs, ... }:
  	let
	  lib = nixpkgs.lib;
	in {
	  nixosConfigurations = {
		  nixos = lib.nixosSystem {
		     system = "x84_64-linux";
		     modules = [ ./configuration.nix ];
		  };
	  };
	};
}
```


- List the config generations `nix profile history --profile /nix/var/nix/profiles/system`