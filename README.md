# BIT pacman 源（Arch / Manjaro 等）

自托管 pacman 仓库（由 deb 重打包），由 CI 从 [BIT Releases](https://github.com/yxpil/bit/releases) 自动同步。

```ini
[bit]
Server = https://yxpil.github.io/pacman-repo/$arch
SigLevel = Never
```

写入 `/etc/pacman.d/bit.conf` 并在 `/etc/pacman.conf` 中 `Include = /etc/pacman.d/bit.conf`，然后：

```bash
sudo pacman -Sy bit
```

- 架构: x86_64 / aarch64 / riscv64 / loongarch64
