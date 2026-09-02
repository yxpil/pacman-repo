# pacman 仓库（BIT）

Arch / Manjaro / CachyOS 等可添加本源安装 BIT（由官方 deb 包转换，无需 makepkg）。

```bash
# 添加仓库（自动按架构选择：x86_64 / aarch64 / riscv64 / loongarch64）
echo "
[bit]
Server = https://yxpil.github.io/pacman-repo/\$arch
SigLevel = Never" | sudo tee /etc/pacman.d/bit.conf
sudo sed -i 's/^\[core\]/[bit]\nInclude = \/etc\/pacman.d\/bit.conf\n\n[core]/' /etc/pacman.conf
sudo pacman -Sy
sudo pacman -S bit
```

> 说明：`SigLevel = Never` 跳过签名校验（本源未签名）；包内容与 GitHub Release 产物一致，HTTPS 传输保证完整性。

| 仓库目录 | 芯片 |
|---|---|
| x86_64 | Intel / AMD / 兆芯 / 海光 |
| aarch64 | 飞腾 / 鲲鹏 / 麒麟 / 树莓派等 |
| riscv64 | VisionFive 2 等 RISC-V 设备 |
| loongarch64 | 龙芯 3A5000 / 3A6000 |

升级：`sudo pacman -Syu`

卸载：`sudo pacman -R bit`

习惯用 makepkg 的用户可直接使用主仓库的 [packaging/arch/PKGBUILD](https://github.com/yxpil/bit/blob/main/packaging/arch/PKGBUILD)：`makepkg -si`。
