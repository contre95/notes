# Arch

I suggest using the [Arch wiki](https://wiki.archlinux.org/) instead if you
don't know what the command is doing.

### Rollback a package to a cached version

```bash
sudo pacman -U /var/cache/pacman/pkg/<package-name>.pkg.tar.zst
# sudo pacman -U /var/cache/pacman/pkg/moc-1:2.5.2-3-x86_64.pkg.tar.zst
```

### Dependency tree viewer

```bash
pactree <package-name>
# pactree mocp
```

### Unused packages

```bash
# List them
pacman -Qtdq
# Remove them
sudo pacman -R $(pacman -Qtdq)
```

### Clear Pacman cache
Cache is usually located under `/var/cache`
```
# pacman's built-in option
sudo pacman -Sc
#To remove all cached versions of uninstalled packages, re-run paccache with u flag
sudo paccache -ruk0
# To keep only one most recent version
sudo paccache -rk 1
```
