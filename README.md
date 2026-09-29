# Kusuri · 薬

管理 Kindle，  
不必再和文件较劲。

连接同一 Wi-Fi 后生效。适用于懒得插线、文件堆积、分类随缘，  
以及临时起意整理 Kindle 的 P 人。

> 文件只在 Mac 与 Kindle 之间直接传输，不经过云端服务器。

---

## 下载

前往 [Releases](../../releases/latest) 下载最新版。

### macOS

下载最新的 `.dmg` 安装包。

适用于：

- macOS
- Apple Silicon Mac
- 已越狱并开启 SSH 服务的 Kindle
- Mac 与 Kindle 连接至同一 Wi-Fi

目前暂无 Windows 版本。

---

## 开始之前

Kusuri 通过 SSH / SFTP 无线连接 Kindle。

第一次使用前，需要准备：

1. Kindle 已越狱
2. Kindle 已开启 SSH 服务
3. Mac 与 Kindle 连接至同一 Wi-Fi
4. Mac 上准备好 SSH 私钥
5. 对应公钥已添加到 Kindle

常见 SSH 端口为 `2222`。

连接成功后，之后打开 Kusuri 可以自动尝试重新连接。

---

## 主要功能

### 无线管理 Kindle

不用连接数据线，即可在 Mac 上：

- 上传图书与文件
- 下载到本地
- 预览文件
- 重命名
- 删除
- 新建文件夹
- 整理目录

支持直接拖入单个文件或整个文件夹。

### 文件分类

Kusuri 会把 Kindle 中的内容整理为：

- 图书
- 字体
- 词典
- 图片
- 其他
- 系统

默认只显示「图书」和「其他」，其余类别可以按需开启。

系统文件会单独识别，并在操作时加强提示，减少误删阅读进度、批注等关联文件的风险。

### 最近加入

查看最近 7 天加入 Kindle 的图书。

可以直接：

- 预览
- 进入所在文件夹
- 重命名
- 导出
- 删除

### 久未阅读

查看超过 90 天没有阅读的图书。

仅显示能够确认最后阅读时间的内容。

### 最近删除

删除图书前，Kusuri 会先在 Mac 上进行本地备份。

最近删除的内容保留 30 天，可以：

- 恢复到原来的位置
- 永久删除

如果原位置已经存在同名文件，不会直接覆盖。

### 阅读进度

Kusuri 可以读取 Kindle 或 KOReader 的阅读进度。

如果两边都有记录，会优先显示 KOReader 的进度。

Kusuri 只读取这些数据，不会修改阅读记录。

---

## 安装

1. 下载最新的 `.dmg`
2. 双击打开安装包
3. 将 **Kusuri** 拖入「应用程序」
4. 从「应用程序」中启动 Kusuri

Kusuri 已通过 Apple 开发者签名与 Apple 公证。

第一次打开时，如果 macOS 询问是否允许打开从互联网下载的应用，选择「打开」即可。

如果系统询问是否允许 Kusuri 访问本地网络，请选择「允许」，否则无法发现和连接 Kindle。

---

## 第一次连接

打开 Kusuri 后，需要填写：

- **Kindle IP**  
  Kindle 当前在 Wi-Fi 网络中的地址

- **SSH 端口**  
  默认 `2222`

- **用户名**  
  默认 `root`

- **访问范围**  
  默认 `/mnt/us/documents`

- **SSH 私钥**  
  默认使用 `~/.ssh/id_ed25519`

如果希望管理整个 Kindle 用户存储，可以将访问范围改为：

`/mnt/us`

Kusuri 只能访问你设置的范围，不会访问 Kindle 用户存储之外的系统区域。

---

## 常见问题

### 连不上 Kindle

请依次检查：

1. Kindle 是否保持唤醒
2. Mac 与 Kindle 是否连接到同一 Wi-Fi
3. Kindle IP 是否发生变化
4. SSH 服务是否已经开启
5. SSH 端口是否正确
6. macOS「隐私与安全性 → 本地网络」中是否允许 Kusuri 访问

### 提示 SSH 认证失败

检查：

- 用户名是否正确
- 当前选择的私钥是否对应 Kindle 上配置的公钥

### 上传或删除很慢

速度取决于当前 Wi-Fi 环境。

传输大文件时，请让 Kindle 保持唤醒并维持稳定的 Wi-Fi 连接。

### 刚上传的书没有出现在 Kindle 书库

Kindle 可能需要一点时间整理新文件。

稍等片刻，如果仍未出现，可以尝试重启 Kindle。

---

## 安全与隐私

Kusuri 不需要注册账号。

- 不经过云端服务器
- 不上传图书内容
- 文件仅在 Mac 与 Kindle 之间传输
- 连接信息只保存在当前 Mac
- SSH 私钥仅用于连接 Kindle
- 阅读进度只读取，不修改

---

## 关于

Kusuri · 薬

Made by Woolpixels

有问题或建议，可以通过应用「关于」页面中的小红书、GitHub 或邮箱联系。

Email: `odyssey.moment@outlook.com`

Copyright © 2026 Woolpixels
