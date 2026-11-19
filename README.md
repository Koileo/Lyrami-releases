<h1 align="center">Lyrami</h1>

<p align="center">舞萌 DX 原生玩家工具箱</p>
<p align="center">玩家卡 · 成绩分析 · 数据同步 · 本机快照</p>
<p align="center">Windows · macOS · Linux · Android · iOS</p>

<p align="center">
  <a href="https://github.com/Koileo/Lyrami-releases/releases"><strong>下载应用</strong></a> ·
  <a href="#下载与安装">安装指南</a> ·
  <a href="#常见问题">常见问题</a> ·
  <a href="https://github.com/Koileo/Lyrami-releases/issues">问题反馈</a>
</p>

---

Lyrami 将账号登录、玩家卡展示、成绩分析、数据同步与本机存档管理集中在一个原生应用中，使用 Rust + NSH 构建。**安装后无需 Python、Node.js 或独立后端，也不用先启动开发服务。**

本仓库是 Lyrami 的**公开发行入口**，用于分发安装包、更新元数据和对应版本源码归档，不是日常开发仓库。

> [!WARNING]
> 仅操作本人或明确获授权的账号。成绩上传、解锁、购票、跑图和迁移会真实修改服务器数据，可能不可撤销，并存在封禁、覆盖或异常成绩风险。请先核对预检内容，确认后再提交；结果未知时先回查，不要重复操作。

## 功能概览

- **玩家中心**：玩家卡、Rating、段位／阶级、称号、装扮与旅行伙伴。
- **成绩分析**：B50、历代牌子、完成表、趋势、省界地图与推分推荐。
- **数据同步**：MuNET / AquaDX / Portal 文件导入，以及按新增或提升谱面增量同步。
- **收藏与地图**：歌曲、收藏品、票券、搭档与地图进度管理。
- **快照与导出**：本机历史、JSON 导入／导出、水鱼／落雪导出；未登录时可只读浏览本机快照。

## 下载与安装

1. 打开 **[Releases 下载页](https://github.com/Koileo/Lyrami-releases/releases)**，选择要安装的版本。
2. 阅读该版本的发行说明，核对系统、CPU 架构和签名状态。
3. 展开 **Assets**，按下表选择文件。需要解压的包请保留完整目录，不要只取出可执行文件。

> [!NOTE]
> 标记为 **Pre-release** 的是预发布版本，不等于稳定版。若下载页暂无发行记录，说明尚无公开安装包；若只有预发布版本，可按需试用或等待正式发行。

下表说明各平台的打包格式与运行要求；实际提供的平台、架构和文件，以每次发行的附件为准。

| 平台 | 下载与安装 | 运行要求 |
| --- | --- | --- |
| Windows | 推荐 `Lyrami-setup.exe`；便携使用可解压完整 `Lyrami.zip` 后运行 `Lyrami.exe` | Windows 10 1809+ / Windows 11；网页组件需要 WebView2 |
| macOS | 打开 `Lyrami.dmg`，将 Lyrami 拖入「应用程序」后启动 | macOS 14+；核对 Intel / Apple Silicon 架构，或选择 Universal 包 |
| Linux | 解压完整 `Lyrami.tar.gz`，运行 `Lyrami/Lyrami`；可用附带的 `install.sh` 注册应用菜单 | glibc 2.39+、GTK 4.14+；网页组件需要 WebKitGTK 6.0 |
| Android | 解压 `Lyrami-android-…-distribution.tar.gz`，取出 APK，通过系统安装器安装 | Android 8 / API 26+；AAB 不能直接安装 |
| iOS | 下载 `Lyrami-ios-UNSIGNED.ipa`，自行签名后安装；若提供已签名版本，按其授权渠道安装 | iOS 15+；有效的签名证书、描述文件与设备授权 |

**不要下载错文件：**

- `Lyrami-macos-update.tar.gz` 是 macOS 更新归档，首次安装优先选择 DMG。
- `Lyrami-source.tar.gz` 是该版本的对应源码，不是安装包。
- GitHub 自动附带的 **Source code (zip / tar.gz)** 只是本发行仓库的快照，不是应用源码；需要应用源码时，请选 `Lyrami-source.tar.gz`。
- `SHA256SUMS`、`Lyrami-<平台>-SHA256SUMS` 和 `Lyrami-<平台>-release.json` 用于校验与核对构建信息，不是安装包。

## 首次使用

1. 在「设置」选择省份、城市与店铺，核对并保存获授权的机台配置。
2. 回到「玩家中心」，粘贴机台登录二维码内容，或选择二维码图片识别。
3. 登录后查看玩家卡与快照；涉及服务器写入时，先阅读预检差分，再明确确认。
4. 操作完成后检查结果；同步或结算期间不要退出应用。

MuNET 官方登录需要本人完成验证。桌面端需安装稳定版 Chrome、Edge 或 Chromium，Linux 还需要可交互的图形会话；移动端使用应用内临时 WebView。无需手工复制 Token，也无需安装浏览器驱动。

## 更新与校验

- **手动更新**：从 Releases 选择版本，阅读发行说明，备份重要数据，并在替换前退出旧版应用。
- **应用内更新**：入口为「关于 → 版本与更新」。是否可用取决于所安装构建是否内置可信公钥，以及签名更新源是否已启用；不可用时请手动下载。
- **更新确认**：应用不会自动下载或静默退出；下载与安装分别确认。移动端转到对应发行页面，仍需满足系统签名要求。
- **文件校验**：下载同一次发行的 `SHA256SUMS`，计算安装包的 SHA-256，并与同名条目比较。不一致时不要安装。校验和只能检测文件变化，不能单独证明发布者身份。

## 常见问题

### 系统提示开发者未知、未签名或阻止安装？

预发布包可能使用开发签名：macOS 的 ad hoc 签名不等于 Developer ID 签名或公证，Android 的 debug key 也不等于正式发行密钥。先确认下载来源和该版本的签名说明，再按系统提供的单应用授权流程处理；**不要全局关闭系统安全保护**。

### Android 更新提示签名冲突？

不同开发构建可能使用不同的 debug key，不能保证直接覆盖升级。先备份可导出的重要数据，再决定如何处理；不要为解决安装错误直接卸载而丢失本机数据。

### iOS 的 UNSIGNED.ipa 能直接安装吗？

不能。可将 IPA 交给 AltStore、Sideloadly 等工具，使用自己的 Apple ID 或有效证书签名后安装。证书有效期、设备授权和权限限制仍然适用，部分签名方式需要定期刷新。项目不提供签名证书，也不需要收集你的 Apple ID 密码。

### 为什么打开后要求连接开发服务器？

请确认安装的是 **Lyrami**，而不是 NSH 的 **NshDev** 开发宿主。日常使用应下载本仓库的原生发行包；独立应用不依赖开发服务器。

## 问题反馈

请在 **[Issues](https://github.com/Koileo/Lyrami-releases/issues)** 中反馈，并尽量提供：

- 操作系统版本、设备型号与 CPU 架构；
- 「关于 → 版本与更新」中的版本、build 与修订信息；
- 下载的文件名、复现步骤、预期结果与实际表现；
- 已脱敏的截图或日志，以及是否使用预发布包、是否自行签名。

**不要公开登录二维码、Token、密码、第三方密钥或完整账号存档。** 本机数据的文件权限保护不等于加密；分享快照、日志或备份前请先脱敏。游戏协议的兼容 TLS 不验证服务端证书身份，不能视为可抵御中间人的安全通道。

## 源码、许可与致谢

应用代码沿用 **AGPL-3.0**。每次发行的对应源码见同一 Release 的 **`Lyrami-source.tar.gz`**；许可原文、第三方声明和素材来源见源码及安装包内的 `LICENSE` / `notices/`。

历史界面与行为参考 [Stella-maiweb](https://github.com/Eiyuuzaki/Stella-maiweb)，协议研究参考 [Astral](https://git.fragrance.moe/Txiaochen/Astral)；玩家卡设计保留 **LuoYe_XwX / Cachebot** 署名。NSH 与其他依赖遵循各自许可。

Lyrami 是非官方项目，与游戏开发商、运营方及上游作者无合作或背书关系。游戏名称、图像、字体和数据属于各自权利人，不因代码许可而自动取得再分发授权。
