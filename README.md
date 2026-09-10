<div align="center">

# 🌐 Chrome 离线镜像

**Google Chrome 全平台离线安装包 —— 每 6 小时自动跟随官方，直发 GitHub Release**

[![Stable](https://img.shields.io/github/v/release/LOVECHEN/chrome-release?label=Stable&color=34a853&logo=googlechrome&logoColor=white)](https://github.com/LOVECHEN/chrome-release/releases/latest)
[![最近更新](https://img.shields.io/github/release-date/LOVECHEN/chrome-release?label=最近更新&color=4285f4)](https://github.com/LOVECHEN/chrome-release/releases)
[![自动同步](https://github.com/LOVECHEN/chrome-release/actions/workflows/daily-download.yml/badge.svg)](https://github.com/LOVECHEN/chrome-release/actions/workflows/daily-download.yml)

[**⬇️ 下载最新正式版**](#download) · [📦 全部版本](https://github.com/LOVECHEN/chrome-release/releases) · [🤔 版本号为何和别处不同](#why)

</div>

---

<a id="download"></a>

## ⬇️ 最新下载

点击即下 **Stable 正式版**最新全量版 —— 永久直链，每次更新自动指向最新：

| 平台 | 架构 / 格式 | 下载 |
|------|------------|------|
| 🪟 **Windows** | 64-bit · `.msi` | [**⬇️ 下载**](https://github.com/LOVECHEN/chrome-release/releases/latest/download/chrome-stable-win64.msi) |
| 🍎 **macOS** | Universal · `.dmg` | [**⬇️ 下载**](https://github.com/LOVECHEN/chrome-release/releases/latest/download/chrome-stable-mac.dmg) |
| 🐧 **Linux** | Debian / Ubuntu · `.deb` | [**⬇️ 下载**](https://github.com/LOVECHEN/chrome-release/releases/latest/download/chrome-stable-linux-deb.deb) |
| 🐧 Linux | Fedora / RHEL · `.rpm` | [⬇️ 下载](https://github.com/LOVECHEN/chrome-release/releases/latest/download/chrome-stable-linux-rpm.rpm) |
| 🪟 Windows | 32-bit · `.msi` | [⬇️ 下载](https://github.com/LOVECHEN/chrome-release/releases/latest/download/chrome-stable-win32.msi) |

> 每个 Release 都附 `checksums.sha256`，下载后可校验完整性。

### 想要抢先版？

Beta / Dev / Canary 的版本号实时如下，点 badge 进对应下载：

[![Beta](https://img.shields.io/github/v/release/LOVECHEN/chrome-release?filter=beta-*&label=Beta%20测试版&color=fbbc04&logo=googlechrome&logoColor=white)](https://github.com/LOVECHEN/chrome-release/releases?q=beta)
[![Dev](https://img.shields.io/github/v/release/LOVECHEN/chrome-release?filter=dev-*&label=Dev%20开发版&color=4285f4&logo=googlechrome&logoColor=white)](https://github.com/LOVECHEN/chrome-release/releases?q=dev)
[![Canary](https://img.shields.io/github/v/release/LOVECHEN/chrome-release?filter=canary-*&label=Canary%20金丝雀&color=ea4335&logo=googlechrome&logoColor=white)](https://github.com/LOVECHEN/chrome-release/releases?q=canary)

---

<a id="why"></a>

## 🤔 为什么这里的版本号可能比别处低？

**这不是落后，而是只收「全量推送版」。**

Chrome 每个大版本都是**灰度发布**的：新版本（比如 154）刚出时，Google 只推给全网约 **0.5%** 的用户试水，几天到几周后才逐步铺到 100%。本镜像只收 **`fraction = 1`（已全量）** 的版本 —— 也就是官方 CDN 真正会发给所有人的那一版。

真实例子（2026-09-10 实测）：

| 版本 | 官方灰度比例 | 本镜像 | 你从 google.com 直链下到的 |
|------|:---:|:---:|:---:|
| `154.0.8037.17` | **0.5%**（试水中） | ⏳ 暂不收 | ❌ 下不到 |
| `153.0.8010.37` | **100%**（全量） | ✅ 就是它 | ✅ 正是这一版 |

> 换句话说：你从官方 `googlechrome.dmg` 直链下到的，和本镜像的 Stable **是同一个文件**（实测字节数完全一致）。别处显示的更高版本号，是「已在灰度、还没轮到大多数人」的预告版。等它全量，本镜像下次自动同步（最多 6 小时内）就会跟上。

<details>
<summary>那我就是想要灰度中的最新版 / 或版本钉死永不更新？</summary>

<br>用 **Chrome for Testing**（见下方数据源）。它按里程碑发布、版本号钉死、天生不会自动更新，适合做固定版本的便携实例。

</details>

---

## 📦 渠道与平台

| 渠道 | 说明 | 平台覆盖 |
|------|------|---------|
| 🟢 **Stable** | 正式版，日常使用首选 | Windows 64/32 · macOS · Linux deb/rpm |
| 🟡 **Beta** | 测试版，提前几周体验新功能 | Windows 64/32 · macOS · Linux deb/rpm |
| 🔵 **Dev** | 开发版，更激进 | Windows 64/32 · macOS · Linux deb/rpm |
| 🔴 **Canary** | 金丝雀，每日构建、最前沿 | 仅 macOS（官方离线包限制）＋ CfT mac-arm64 |

> **Canary 说明**：官方只给 macOS 提供 Canary 离线 DMG（Windows 是在线 stub，Linux 无此渠道）。需要其它平台的最前沿版，请用 Chrome for Testing。

### 两个数据源

| 数据源 | 触发 | 格式 | 自动更新 |
|--------|------|------|----------|
| **官方消费版**（默认） | — | DMG / MSI / DEB / RPM | 是（需自行屏蔽） |
| **Chrome for Testing** | 本地 CLI 加 `-cft` | ZIP（按架构拆分） | **否，版本钉死** |

Chrome for Testing 是 Google 官方专为自动化测试发布的渠道，产物为「Google Chrome for Testing.app」，与正式版并存、版本钉死，数据来自 [CfT JSON API](https://googlechromelabs.github.io/chrome-for-testing/)。

---

## 🔄 自动化

GitHub Actions **每 6 小时**（UTC `0/6/12/18` = 北京 `8/14/20/2` 点）自动执行：

1. 查 [Google VersionHistory API](https://versionhistory.googleapis.com) 取各渠道**已全量**（`fraction ≥ 1`）的最新版本号
2. 与已有 Release 比对，版本没变就跳过（秒退，零成本）
3. 下载官方离线安装包 → 生成 SHA256 → 创建 GitHub Release

> - **Stable 固定为仓库 Latest**，所以上方「最新下载」直链永久有效、不会被 Canary/Dev 抢占。
> - **keepalive 兜底**：仓库即便长期无新版，也不会因 GitHub「60 天不活跃」被停用定时任务。

Release 命名 `{channel}-{version}`，例：`stable-153.0.8010.37` · `beta-154.0.8037.0` · `dev-155.0.8040.2` · `canary-155.0.8048.0`。

<details>
<summary>📅 Canary 的 Release 里为什么有两个文件？</summary>

<br>Canary 的 Release 同时含官方 `chrome-canary-mac.dmg`（mac universal）与 Chrome for Testing 的 `chrome-canary-cft-mac-arm64.zip`（mac Apple Silicon，版本钉死）。tag 版本号以官方 mac Canary 为准。

</details>

---

## 🧰 本地 CLI（可选）

本仓库同时是一个 Go 下载器，可在本地手动拉包：

<details>
<summary>展开用法</summary>

```bash
go build -o chrome-downloader .

./chrome-downloader -info                    # 查看各渠道版本
./chrome-downloader -channel stable mac      # 下 macOS stable
./chrome-downloader -channel canary mac      # 官方 Canary（仅 mac dmg）
./chrome-downloader all                      # 全平台全渠道（官方源）

# —— Chrome for Testing 源（-cft，选项须放在位置参数之前）——
./chrome-downloader -cft -info               # CfT 各渠道版本
./chrome-downloader -cft -channel canary     # CfT Canary（主机架构 mac zip）
./chrome-downloader -cft -channel all all    # CfT 全渠道全平台
```

</details>

---

## 🛡️ 屏蔽自动更新（macOS）

官方消费版装后自带 GoogleUpdater 会后台自动升级。想要版本钉死：删除 App 内 `Frameworks/.../GoogleUpdater.app` 并对 App 重签，或直接改用 Chrome for Testing（天生不更新）。

## 📡 数据源

- 版本信息：[Google VersionHistory API](https://versionhistory.googleapis.com)
- 官方安装包：[dl.google.com](https://dl.google.com) 官方 CDN
- Chrome for Testing：[CfT JSON API](https://googlechromelabs.github.io/chrome-for-testing/) ＋ `storage.googleapis.com` 官方存储桶

## 📄 License

MIT
