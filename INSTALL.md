# 安装指南

## 从 GitHub Releases 下载

访问 [Releases 页面](https://github.com/lihongjie0209/excel-cli/releases) 下载适合你系统的预编译二进制文件。

### Linux (x86_64)

```bash
# 下载
wget https://github.com/lihongjie0209/excel-cli/releases/latest/download/excel-cli-linux-x86_64.tar.gz

# 解压
tar xzf excel-cli-linux-x86_64.tar.gz

# 移动到系统路径
sudo mv excel-cli /usr/local/bin/

# 验证安装
excel-cli --version
```

### Linux (ARM64)

```bash
# 下载
wget https://github.com/lihongjie0209/excel-cli/releases/latest/download/excel-cli-linux-aarch64.tar.gz

# 解压
tar xzf excel-cli-linux-aarch64.tar.gz

# 移动到系统路径
sudo mv excel-cli /usr/local/bin/

# 验证安装
excel-cli --version
```

### macOS (Intel)

```bash
# 下载
curl -LO https://github.com/lihongjie0209/excel-cli/releases/latest/download/excel-cli-macos-x86_64.tar.gz

# 解压
tar xzf excel-cli-macos-x86_64.tar.gz

# 移动到系统路径
sudo mv excel-cli /usr/local/bin/

# 验证安装
excel-cli --version
```

### macOS (Apple Silicon)

```bash
# 下载
curl -LO https://github.com/lihongjie0209/excel-cli/releases/latest/download/excel-cli-macos-aarch64.tar.gz

# 解压
tar xzf excel-cli-macos-aarch64.tar.gz

# 移动到系统路径
sudo mv excel-cli /usr/local/bin/

# 验证安装
excel-cli --version
```

### Windows (x86_64)

1. 访问 [Releases 页面](https://github.com/lihongjie0209/excel-cli/releases)
2. 下载 `excel-cli-windows-x86_64.exe.zip`
3. 解压到任意目录
4. 将解压目录添加到系统 PATH 环境变量
5. 在命令提示符或 PowerShell 中运行 `excel-cli --version` 验证

或使用 PowerShell：

```powershell
# 下载
Invoke-WebRequest -Uri "https://github.com/lihongjie0209/excel-cli/releases/latest/download/excel-cli-windows-x86_64.exe.zip" -OutFile "excel-cli.zip"

# 解压
Expand-Archive -Path excel-cli.zip -DestinationPath .

# 验证
.\excel-cli.exe --version
```

## 从源码构建

### 前置要求

- Rust 1.70 或更高版本
- Cargo（Rust 包管理器）

### 安装 Rust

如果还没有安装 Rust，请访问 [rustup.rs](https://rustup.rs/) 并按照说明操作。

Linux 和 macOS:
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

Windows: 下载并运行 [rustup-init.exe](https://rustup.rs/)

### 构建步骤

```bash
# 克隆仓库
git clone https://github.com/lihongjie0209/excel-cli.git
cd excel-cli

# 构建 release 版本
cargo build --release

# 二进制文件位于 target/release/excel-cli (或 Windows 上的 excel-cli.exe)

# 可选：安装到系统
cargo install --path .
```

### 开发构建

```bash
# 克隆仓库
git clone https://github.com/lihongjie0209/excel-cli.git
cd excel-cli

# 运行测试
cargo test

# 运行开发版本
cargo run -- convert -i data.xlsx -o output.json -f json
```

## 使用 Cargo 安装

一旦发布到 crates.io，你可以直接安装：

```bash
cargo install excel-cli
```

## Docker（未来支持）

```bash
# 拉取镜像
docker pull ghcr.io/lihongjie0209/excel-cli:latest

# 运行
docker run --rm -v $(pwd):/data ghcr.io/lihongjie0209/excel-cli:latest \
  convert -i /data/input.xlsx -o /data/output.json -f json
```

## 验证安装

运行以下命令验证安装：

```bash
# 查看版本
excel-cli --version

# 查看帮助
excel-cli --help

# 查看支持的格式
excel-cli formats
```

## 更新

### 从 Releases 更新

重复下载和安装步骤，使用最新版本替换旧版本。

### 从源码更新

```bash
cd excel-cli
git pull origin master
cargo build --release
```

### 使用 Cargo 更新

```bash
cargo install excel-cli --force
```

## 卸载

### 删除二进制文件

```bash
# Linux/macOS
sudo rm /usr/local/bin/excel-cli

# Windows
# 手动删除可执行文件并从 PATH 中移除目录
```

### 使用 Cargo 卸载

```bash
cargo uninstall excel-cli
```

## 故障排除

### Linux: "Permission denied"

```bash
chmod +x excel-cli
```

### macOS: "Cannot be opened because the developer cannot be verified"

```bash
xattr -d com.apple.quarantine excel-cli
```

### Windows: "Windows protected your PC"

点击 "More info" 然后 "Run anyway"

### 找不到命令

确保二进制文件所在目录已添加到 PATH 环境变量。

## 支持的平台

| 平台 | 架构 | 支持状态 |
|------|------|---------|
| Linux | x86_64 | ✅ 完全支持 |
| Linux | x86_64 (musl) | ✅ 完全支持 |
| Linux | ARM64 | ✅ 完全支持 |
| macOS | x86_64 (Intel) | ✅ 完全支持 |
| macOS | ARM64 (Apple Silicon) | ✅ 完全支持 |
| Windows | x86_64 | ✅ 完全支持 |
| Windows | ARM64 | ✅ 完全支持 |

## 需要帮助？

- 📖 查看 [README](README.md) 了解使用方法
- 🐛 [报告问题](https://github.com/lihongjie0209/excel-cli/issues)
- 💬 [提问和讨论](https://github.com/lihongjie0209/excel-cli/discussions)
