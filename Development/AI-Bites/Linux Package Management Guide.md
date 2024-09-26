## Updating Packages

### Debian-based Systems (Ubuntu, Linux Mint, etc.)
```bash
sudo apt update
sudo apt upgrade
```

### Red Hat-based Systems (Fedora, CentOS, etc.)
For newer versions:
```bash
sudo dnf update
```
For older versions:
```bash
sudo yum update
```

### Arch-based Systems
```bash
sudo pacman -Syu
```

## Cleaning Unused Files and Caches

### Debian-based Systems
```bash
sudo apt autoremove
sudo apt clean
```

### Red Hat-based Systems
```bash
sudo dnf autoremove
sudo dnf clean all
```

### Arch-based Systems
```bash
sudo pacman -Rns $(pacman -Qtdq)
sudo pacman -Sc
```

## Command Explanations

- `update`: Refreshes the package list
- `upgrade`: Installs newer versions of installed packages
- `autoremove`: Removes packages that were automatically installed to satisfy dependencies and are no longer needed
- `clean`: Clears out the local repository of retrieved package files
- `-Syu` (Arch): Syncs repositories, updates packages
- `-Rns` (Arch): Removes a package along with its dependencies and configuration files
- `-Qtdq` (Arch): Lists all packages no longer required as dependencies
- `-Sc` (Arch): Removes all the cached packages that are not currently installed

Remember to run these commands with caution, especially when removing packages or cleaning caches. It's always a good idea to review what will be removed before confirming any action.