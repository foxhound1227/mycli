# MyCLI Binary Builder

这个项目使用 GitHub Actions 自动编译适用于 CentOS 7 的 MyCLI 二进制文件。

## 构建说明

### 自动构建
每次推送到 `main` 分支时,GitHub Actions 会自动触发构建流程:

1. 使用 `manylinux2014_x86_64` 容器(基于 CentOS 7,兼容 glibc 2.17)
2. 安装 Python 3.9 和依赖包
3. 使用 PyInstaller 打包成单文件二进制
4. 上传构建产物到 GitHub Artifacts

### 下载二进制文件

1. 访问 [Actions 页面](https://github.com/foxhound1227/mycli/actions)
2. 点击最新的 "Build MyCLI Binary" 工作流运行
3. 在 "Artifacts" 部分下载 `mycli_linux_binary`
4. 解压后即可在 CentOS 7 上使用

### 手动触发构建

在 [Actions 页面](https://github.com/foxhound1227/mycli/actions/workflows/build_binary.yml) 点击 "Run workflow" 按钮。

## 使用方法

```bash
# 下载并解压后
chmod +x mycli_linux
./mycli_linux --help

# 连接数据库
./mycli_linux -h localhost -u root -p
```

## 技术栈

- **MyCLI**: MySQL/MariaDB 命令行客户端
- **PyInstaller**: Python 打包工具
- **Manylinux**: 兼容性容器镜像
