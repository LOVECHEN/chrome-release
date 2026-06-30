# Chrome Offline Mirror

自动镜像 Chrome 全平台离线安装包到 GitHub Release，每日更新。

[![Daily Chrome Download](https://github.com/LOVECHEN/chrome-release/actions/workflows/daily-download.yml/badge.svg)](https://github.com/LOVECHEN/chrome-release/actions/workflows/daily-download.yml)

## 下载

前往 [Releases](https://github.com/LOVECHEN/chrome-release/releases) 页面下载对应平台的安装包。

### 支持平台

| 平台 | 文件格式 |
|------|---------|
| Windows 64-bit | `.msi` |
| Windows 32-bit | `.msi` |
| macOS (Universal) | `.dmg` |
| Linux (Debian/Ubuntu) | `.deb` |
| Linux (Fedora/RHEL) | `.rpm` |

### 支持渠道

| 渠道 | 说明 |
|------|------|
| Stable | 正式版，推荐日常使用 |
| Beta | 测试版，提前体验新功能 |
| Dev | 开发版，最新但可能不稳定 |
| Canary | 金丝雀版，每日构建，最前沿 |

> **Canary 说明**：官方源的 Canary 仅 macOS 提供离线 DMG；Windows 只有在线 stub 安装器（无 standalone enterprise MSI），Linux 不存在 Canary 渠道。需要 Windows/Linux 的 Canary 请用下方 Chrome for Testing 源。

### 两个数据源

| 数据源 | 触发 | 格式 | 平台粒度 | 渠道 | 自动更新 |
|--------|------|------|----------|------|----------|
| 官方消费版（默认）| — | DMG / MSI / DEB / RPM | mac 为 universal | stable / beta / dev / canary | 是（需另行屏蔽）|
| Chrome for Testing | `-cft` | ZIP | 按架构拆分（mac-arm64 / mac-x64 / linux64 / win32 / win64）| stable / beta / dev / canary | **否，版本钉死，天生不更新** |

Chrome for Testing 是 Google 官方专为自动化/测试发布的分发渠道，产物为「Google Chrome for Testing.app」，与正式版 / Canary 并存、版本钉死、不会自动更新，适合做版本固定的便携实例。版本与下载地址直接来自 [CfT JSON API](https://googlechromelabs.github.io/chrome-for-testing/)。

## Release 命名规则

```
{channel}-{version}
```

示例：
- `stable-146.0.7680.76` — Stable 正式版
- `beta-147.0.7727.3` — Beta 测试版
- `dev-148.0.7730.2` — Dev 开发版

## 自动化

GitHub Actions 每日 UTC 06:00（北京时间 14:00）自动执行：

1. 查询 [Google VersionHistory API](https://versionhistory.googleapis.com/v1/chrome/platforms/win64/channels/stable/versions/all/releases) 获取最新版本号
2. 对比已有 Release，版本未变则跳过
3. 下载全平台离线安装包
4. 生成 SHA256 校验文件
5. 创建 GitHub Release 并上传

## 本地使用

本项目还包含一个 Go CLI 工具，可在本地手动下载：

```bash
# 编译
go build -o chrome-downloader .

# 查看版本信息
./chrome-downloader -info

# 下载 macOS stable
./chrome-downloader -channel stable mac

# 下载官方 Canary（仅 mac dmg）
./chrome-downloader -channel canary mac

# 下载全平台全渠道（官方源；canary 仅 mac 会落地，其它平台自动跳过）
./chrome-downloader all

# —— Chrome for Testing 源（-cft）——
# 注意：Go flag 要求选项放在位置参数之前

# 查看 CfT 各渠道版本
./chrome-downloader -cft -info

# CfT Canary（默认主机架构的 mac zip）
./chrome-downloader -cft -channel canary

# CfT 全渠道全平台
./chrome-downloader -cft -channel all all
```

## 数据源

- 官方版本信息：[Google VersionHistory API](https://versionhistory.googleapis.com)
- 官方安装包：[dl.google.com](https://dl.google.com) 官方 CDN
- Chrome for Testing：[CfT JSON API](https://googlechromelabs.github.io/chrome-for-testing/) + `storage.googleapis.com` 官方存储桶

## License

MIT
