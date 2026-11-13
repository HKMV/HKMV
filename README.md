# Serenity · 慕书

<img src="https://avatars.githubusercontent.com/u/26456469?v=4" width="96" align="right" />

<p align="center">
  <samp>
    <a href="https://hkmv.github.io">博客</a> ·
    <a href="https://github.com/HKMV?tab=repositories">项目</a> ·
    <a href="https://github.com/HKMV/mesh-networking-notes">组网笔记</a> ·
    <a href="https://github.com/HKMV/devroute/releases/latest">Releases</a>
  </samp>
</p>

> 写工具的人：把反复出现的麻烦事，做成一个双击就能用的程序。

主要用 **Rust** 写跨平台桌面工具与网络转发软件 —— 原生 GUI、不套 WebView、单文件即拷即用。同时做内网运维与自动化（MES / 订单自动化平台）。网络这块偏底层：写过本地转发与 SOCKS5/HTTP 代理，也长期折腾私有组网（Mesh VPN）的选型与落地。

- **在做**：[devroute](https://github.com/HKMV/devroute)（本地开发转发）、[tun2proxy-gui](https://github.com/HKMV/tun2proxy-gui)（tun2proxy 桌面前端）
- **在学**：系统层网络（TUN / 分流规则）、GPU 渲染的原生 UI
- **环境**：Windows（PowerShell + C#）、Arch Linux、macOS —— 三个平台日常都用，所以工具一律按跨平台写

## 代表项目

### [devroute](https://github.com/HKMV/devroute) — 本地开发调试用的转发工具

Rust + FLTK 纯原生 GUI，**3MB** 单文件、GUI 空闲 **3.4MB**、`--headless` **2.5MB**；本地镜像与 SOCKS5/HTTP 代理两种模式各自独立启停，用法与已知边界见 [项目 README](https://github.com/HKMV/devroute)。

### [tun2proxy-gui](https://github.com/HKMV/tun2proxy-gui) — tun2proxy 的跨平台桌面图形前端

Rust + GPUI（Zed 的 GPU 渲染 UI 框架），不依赖 WebView；v0.6.1 四个平台产物 Windows **3.55 MB** / macOS **3.11–3.44 MB** / Linux **7.27 MB**，附 SHA-256 校验。用法与已知边界见 [项目 README](https://github.com/HKMV/tun2proxy-gui)。

**也在维护的**：

- [**api-request-analyzer-browser-plugin**](https://github.com/HKMV/api-request-analyzer-browser-plugin) — Svelte + `chrome.debugger`，把每个请求拆成 **DNS / TCP / TLS / 发送 / 等待 / 下载** 6 个阶段做可视化，支持通配符与正则域名规则、CSV / Excel 导出
- [**anywhere-ocr**](https://github.com/HKMV/anywhere-ocr) — AutoHotkey 实现，任意界面框选即识别，不打断当前操作
- [**nal**](https://github.com/HKMV/nal) — 网络自动登录：检测到断联自动重登。最初 Go，后以 Rust + Tokio 重写
- [**atop-analyze**](https://github.com/HKMV/atop-analyze) — Go CLI，解析 Linux `atop` rawlog（2.10），终端出 Top N 并导出带趋势图的 Excel

## 技术栈与数据

| 用途 | 用到的东西 |
|---|---|
| 系统 | Arch Linux、macOS、Windows |
| 语言 | Rust、Go、C#、TypeScript、Java、AutoHotkey |
| 桌面端 | 原生渲染：GPUI、FLTK、iced、egui；WebView 套壳：Tauri、Wails；Java 侧另评估过 JxBrowser；另有 WPF、Svelte |
| 嵌入式 | ESP32 系（ESP32-S3）、Rust no_std（embassy / espflash / embedded-graphics）、LVGL |
| 服务与运维 | Docker Compose、Caddy、内网穿透与反向代理 |
| 私有组网 | EasyTier（主用）、NetBird（备用），研究过 Tailscale / ZeroTier / vnt |

<details>
<summary>star 分布（3,787 个）—— 数据比自我介绍更诚实</summary>

| 语言 | 数量 | 语言 | 数量 |
|---|---|---|---|
| Rust | 625 | Python | 458 |
| TypeScript | 434 | Java | 360 |
| Go | 349 | JavaScript | 289 |
| C++ | 192 | C | 187 |
| C# | 184 | Shell | 97 |

四个观察：

- **Rust 排第一，且比第二名高 37%** —— 对我是日常主力，不是贴在简历上的标签。
- **Windows 171 / Linux 160 / macOS 150 三个 topic 几乎并列**，另有 57 个项目同时打了这三平台 —— 跨平台在我这里是前提条件，不是加分项。
- **AI / LLM 相关 435 个**，其中 MCP（100）、agent（92）、claude-code（97）占大头 —— AI 编码工具链是重度使用，不是浅尝。
- **嵌入式 29 个，其中 9 个是 Rust** —— 从 ESP32 系往里走，正好接上 no_std 那条线（`embassy` / `espflash` / `embedded-graphics`）。

</details>

## 关注的方向

- **Rust 跨平台桌面与系统层工具**：四种范式都动过手 —— 立即模式（egui）、声明式（iced）、原生绑定（FLTK / GPUI）、WebView 套壳（Tauri / Wails）；套壳这条另有 Java 侧的一档，在 Java 项目里评估过 JxBrowser（TeamDev 的商业 Chromium 组件，Swing / JavaFX / SWT 用）。落到自己项目上选原生渲染，因为**体积与内存占用是硬指标，不是加分项**：一个 3MB、空闲 3.4MB 的转发工具，才有资格让人随手双击起来
- **AI 编码代理与技能生态**：Claude Code / Codex / MCP / agent skills 的日常重度使用
- **Windows 与 macOS 提效小工具**：窗口管理、OCR、剪贴板、输入法这一类每天要点几百次的东西
- **Linux 内核与发行版定制**：日常跑 Arch，也跟内核分支与驱动层的改动（star 里集中在 kernel / tkg / zen 这一类）
- **嵌入式与 ESP32**：从 ESP32 系入手，主要看 ESP32-S3 + Rust 这条线 —— `espflash` 烧写、`embassy` 异步、`embedded-graphics` 画图，不碰标准库也能把东西跑起来；顺带看 LVGL / TinyGo 这类小屏图形与固件方案，以及「小智」那种端云一体的语音助手怎么做
- **私有组网与 Mesh VPN**：Tailscale、ZeroTier、NetBird、EasyTier、vnt 都实际部署过，现在**主用 EasyTier、NetBird 留作备用通道**。选型看的是 NAT 穿透成功率、中继是否自己可控、以及多平台（Windows / Arch / macOS / 路由器）部署成本 —— 实践笔记整理在 [mesh-networking-notes](https://github.com/HKMV/mesh-networking-notes)
- **自建服务与内网基础设施**：能自己搭就不依赖第三方

<details>
<summary>常看常参考 —— 各自解决了我反复遇到的问题</summary>

- [**caddy**](https://github.com/caddyserver/caddy) — 自动 HTTPS 的配置模型，反向代理的默认选择
- [**frp**](https://github.com/fatedier/frp) — 内网穿透里实现读起来最省力的一个，协议设计值得抄
- [**tauri**](https://github.com/tauri-apps/tauri) — 套壳方案里最克制的一档，用它的边界在哪很清楚
- [**rustdesk**](https://github.com/rustdesk/rustdesk) — Rust 写跨平台桌面 + 自建中继的完整样本
- [**yazi**](https://github.com/sxyazi/yazi) — 终端界面的异步与渲染组织方式
- [**sniffnet**](https://github.com/GyulyVGC/sniffnet) — 流量可视化的渲染思路，跟 GPUI 那套可以对照看
- [**alacritty**](https://github.com/alacritty/alacritty) — GPU 渲染终端的性能下限
- [**immich**](https://github.com/immich-app/immich) — 自建服务的完备度参照：备份、迁移、升级路径是否写清楚

</details>

<details>
<summary>早年与零散项目</summary>

- [Aria2-CSharp](https://github.com/HKMV/Aria2-CSharp) — C# 多线程下载工具（基于 Aria2）
- [Edge.ahk](https://github.com/HKMV/Edge.ahk) — AutoHotkey 驱动 Chrome 的脚本库
- [User32WindowSendMessage](https://github.com/HKMV/User32WindowSendMessage) — Win32 API 跨进程窗口传值
- [TreeViewDemo](https://github.com/HKMV/TreeViewDemo) — WPF 带复选框的父子级联 TreeView（含简化版 RelayCommand）
- [compose-configs](https://github.com/HKMV/compose-configs) — 常用服务的 docker-compose 配置合集

</details>

---

## English

Developer working mostly in **Rust**: native cross-platform desktop tools and network-forwarding utilities — real native GUI, no WebView, single small binary. Has worked across the whole Rust GUI spectrum (immediate mode `egui`, declarative `iced`, native bindings FLTK / GPUI, and WebView shells Tauri / Wails — plus JxBrowser evaluated on the Java side), and picks native rendering because binary size and idle memory are hard requirements, not nice-to-haves. Ships for Windows, macOS and Linux (Arch included), and also runs internal infrastructure (Docker + Caddy) and industrial automation platforms.

Highlights: [**devroute**](https://github.com/HKMV/devroute) — a ~3MB dev-time forwarder with an independent "local mirror site" mode and a SOCKS5/HTTP proxy mode; [**tun2proxy-gui**](https://github.com/HKMV/tun2proxy-gui) — a GPUI-based desktop front-end for tun2proxy; [**api-request-analyzer-browser-plugin**](https://github.com/HKMV/api-request-analyzer-browser-plugin) — a Chrome extension that breaks every request into DNS / TCP / TLS / send / wait / download phases.

Interests: Rust desktop & systems tooling, AI coding agents and skills, small Windows/macOS productivity tools, self-hosted services, private mesh networking — Tailscale / ZeroTier / NetBird / EasyTier / vnt deployed and compared, currently running EasyTier as the primary mesh with NetBird as a backup path — and embedded work on ESP32, mostly the Rust `no_std` stack (`embassy` / `espflash` / `embedded-graphics`).

Star profile (~3.8k): Rust first (625), then Python / TypeScript / Java / Go — 435 repos in AI/LLM with a heavy MCP + agent share, and 57 projects tagged Windows, Linux and macOS at once. What I star is what I actually run.

Blog: https://hkmv.github.io
