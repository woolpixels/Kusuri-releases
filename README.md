# Kusuri · 薬

管理 Kindle，不必再和文件较劲。

Mac 与越狱 Kindle 连接同一 Wi-Fi，即可无线上传、整理、预览和删除 Kindle 里的图书与文件。文件只在 Mac 与 Kindle 之间直接传输，不经过云端服务器。

[![最新版本](https://img.shields.io/github/v/release/woolpixels/Kusuri-releases?label=release)](https://github.com/woolpixels/Kusuri-releases/releases/latest)
![平台](https://img.shields.io/badge/platform-macOS%20(Apple%20Silicon)-lightgrey)

## 下载

前往 [Releases](https://github.com/woolpixels/Kusuri-releases/releases/latest) 下载最新的 `.dmg` 安装包。

| 平台 | 状态 |
| --- | --- |
| macOS（Apple Silicon） | 可用，已通过 Apple 开发者签名与公证 |
| Windows | 暂无 |

## 系统要求

- Apple Silicon Mac（macOS）
- 已越狱并开启 SSH 服务的 Kindle
- Mac 与 Kindle 连接至同一 Wi-Fi
- Mac 上有 SSH 私钥，对应公钥已添加到 Kindle

## 快速开始

1. 下载 `.dmg`，双击打开，将 **Kusuri** 拖入「应用程序」。
2. 首次打开时，如 macOS 询问是否打开从互联网下载的应用，选择「打开」；如询问本地网络访问，选择「允许」，否则无法发现 Kindle。
3. 填写连接信息后点击「连接 Kindle」：

   | 项目 | 默认值 | 说明 |
   | --- | --- | --- |
   | Kindle IP | 无 | Kindle 在 Wi-Fi 中的地址（必填） |
   | SSH 端口 | `2222` | 与 Kindle 上的设置一致 |
   | 用户名 | `root` | 一般无需修改 |
   | 访问范围 | `/mnt/us/documents` | 改为 `/mnt/us` 可管理整个用户存储 |
   | SSH 私钥 | `~/.ssh/id_ed25519` | 选择不带 `.pub` 的私钥文件 |

连接成功后，下次打开 Kusuri 会自动尝试重新连接。详细步骤见 [使用说明](docs/使用说明.md)。

## 功能

### 整理：分类、显示与排序

Kindle 里不只有书，还有字体、词典、图片，以及系统自动生成的阅读记录。Kusuri 帮你把它们分清楚，只看想看的。

- **自动分类**：图书、字体、词典、图片、其他、系统。文件夹先按名称判断用途，不明确时只读检查其中的文件，空文件夹归为「其他」。
- **按需显示**：「更多 → 文件显示」可多选要显示的类别，每项写明对应格式。默认只显示「图书」和「其他」，字体、词典、图片、系统文件默认收起，书架保持清爽。
- **系统文件保护**：阅读位置、批注等自动生成的文件单独识别、默认隐藏；直接操作时弹窗加重提示，减少误删进度和批注的风险。分错类时可右键手动标为系统文件，随时恢复自动识别，设置只保存在本机。
- **多维排序**：按名称、分类、进度、大小、修改时间、添加时间排序，再点一次反向；没有进度的书始终排在最后。
- **顶部概览**：显示访问范围内的图书总数和 Kindle 容量，路径旁显示当前文件夹各类文件的数量。

### 找书与回顾

- **最近加入**：最近 7 天加入 Kindle 的图书，注明所在文件夹和加入时间。
- **久未阅读**：超过 90 天没翻开的图书（仅限能确认最后阅读时间的内容），方便清理。
- **阅读进度**：读取 Kindle 或 KOReader 的进度并显示在书架，两边都有记录时优先 KOReader；只读取，不修改。

### 传输与安全删除

- **无线管理**：上传、下载、预览、重命名、导出、新建文件夹；支持拖入单个文件或整个文件夹，目录层级原样保留。
- **传输进度**：上传、删除时显示进度、速度与预计剩余时间，上传可随时取消。
- **关联文件处理**：重命名、删除图书时，识别同名的阅读进度和批注文件，可选择一并处理，避免进度丢失。
- **最近删除**：删除前先在 Mac 上本地备份，保留 30 天，可恢复到原位置或永久删除；原位置已有同名文件时不会覆盖。

## 校验安装包

每个 Release 的资产页会显示安装包的 SHA-256。也可在终端中自行计算并对照：

```bash
shasum -a 256 ~/Downloads/Kusuri-1.3.0-arm64.dmg
```

## 常见问题

**连不上 Kindle？** 依次检查：

1. Kindle 是否保持唤醒（休眠后 Wi-Fi 会断开）。
2. Mac 与 Kindle 是否在同一 Wi-Fi。
3. Kindle IP 是否变化。
4. SSH 服务是否开启，端口是否一致。
5. 「系统设置 → 隐私与安全性 → 本地网络」中是否允许 Kusuri。

**提示 SSH 认证失败？** 检查用户名，以及所选私钥是否与 Kindle 上配置的公钥配对。

**上传或删除很慢？** 速度取决于 Wi-Fi。传输大文件时请保持 Kindle 唤醒、网络稳定。

**刚上传的书没有出现在书库？** Kindle 需要一点时间整理新文件，稍等片刻；仍未出现可重启 Kindle。

更多问题见 [使用说明](docs/使用说明.md#常见问题)。

## 安全与隐私

- 无需注册账号，不经过云端服务器，不上传图书内容。
- 文件仅在 Mac 与 Kindle 之间直接传输。
- 连接信息只保存在本机；SSH 私钥仅用于连接 Kindle。
- Kusuri 只能访问你设置的访问范围，无法触及 Kindle 用户存储之外的系统区域。

## 更新记录

见 [CHANGELOG.md](CHANGELOG.md)。

## 联系

有问题或建议，可通过应用「关于」页面中的小红书、GitHub 或邮箱联系：`odyssey.moment@outlook.com`

---

Kusuri · 薬 — Made by [Woolpixels](https://woolpixels.cc/) · 官网：<https://woolpixels.cc/>

Copyright © 2026 Woolpixels
