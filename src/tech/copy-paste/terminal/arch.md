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
