# Serenity · 慕书

<img src="https://avatars.githubusercontent.com/u/26456469?v=4" width="96" align="right" />

> 写工具的人：把反复出现的麻烦事，做成一个双击就能用的程序。

后端出身，现在主要用 **Rust** 写跨平台桌面工具与网络转发类软件 —— 原生 GUI、不套 WebView、单文件即拷即用。同时做内网运维与自动化（MES / 订单自动化平台），以及 AI 编码工具链的日常实践。网络这块偏底层：写过本地转发与 SOCKS5/HTTP 代理，也长期折腾私有组网（Mesh VPN）的选型与落地。

- 在做：[devroute](https://github.com/HKMV/devroute)（本地开发转发）、[tun2proxy-gui](https://github.com/HKMV/tun2proxy-gui)（tun2proxy 桌面前端）
- 在学：系统层网络（TUN / 分流规则）、GPU 渲染的原生 UI
- 环境：Windows（PowerShell + C#）、Arch Linux、macOS —— 三个平台都在日常用，所以工具一律按跨平台写
- 博客：[hkmv.github.io](https://hkmv.github.io)

## 代表项目

### [devroute](https://github.com/HKMV/devroute) — 本地开发调试用的转发工具

Rust + FLTK 纯原生 GUI（非 Tauri / Electron，不内嵌浏览器内核），约 3MB 单文件，GUI 空闲内存 3.4MB、`--headless` 模式 2.5MB。

两种**互相独立、可各自启停**的用法：

- **本地镜像**：本地端口直接提供远端页面，接口转发到本地服务 —— 不依赖系统代理，没有 CORS / Cookie 跨域问题，支持 https 上游与内网自签证书
- **SOCKS5 / HTTP 代理**：同一端口自动识别两种协议，按 `Host + 路径前缀` 匹配转发并重写路径

带深浅色主题、中英文界面、实时日志与统计、崩溃残留的系统代理自清理。提供 Windows / macOS / Linux 预编译产物（Linux 版静态链接，Arch 上解压即用）→ [Releases](https://github.com/HKMV/devroute/releases/latest)

### [tun2proxy-gui](https://github.com/HKMV/tun2proxy-gui) — tun2proxy 的跨平台桌面图形前端

Rust + [GPUI](https://github.com/zed-industries/zed/tree/main/crates/gpui)（Zed 的 GPU 渲染 UI 框架），不依赖 WebView。多套代理配置一键切换、启动前预检上游代理、自动下载并校验 tun2proxy 官方二进制（SHA-256）、实时日志与流量图、分流规则清单单独开关、中英文界面、系统托盘。

### [anywhere-ocr](https://github.com/HKMV/anywhere-ocr) — 随处 OCR

AutoHotkey 实现，任意界面框选即识别，不打断当前操作。

### [nal](https://github.com/HKMV/nal) — 网络自动登录

为解决公司网络偶发断联而生：自动检测网络状态，异常时自动重新登录。最初用 Go 实现，后以 Rust + Tokio 重写。

### [api-request-analyzer-browser-plugin](https://github.com/HKMV/api-request-analyzer-browser-plugin) — 请求耗时分析插件

Svelte + `chrome.debugger`，把每个请求拆成 **DNS / TCP / TLS / 发送 / 等待 / 下载** 6 个阶段做可视化，支持通配符与正则域名规则、CSV / Excel 导出、虚拟滚动。

### [atop-analyze](https://github.com/HKMV/atop-analyze) — atop 日志转报表

Go CLI，解析 Linux `atop` rawlog（针对 atop 2.10），终端输出 CPU / 内存 Top N，并导出含进程明细与 CPU、内存趋势图表的 Excel。

## 技术栈

| 用途 | 用到的东西 |
|---|---|
| 系统 | Arch Linux、macOS、Windows |
| 语言 | Rust、Go、C#、TypeScript、Java、AutoHotkey |
| 桌面端 | GPUI、FLTK、WPF、Svelte |
| 服务与运维 | Docker Compose、Caddy、内网穿透与反向代理 |
| 私有组网 | EasyTier（主用）、NetBird（备用），研究过 Tailscale / ZeroTier / vnt |

## 关注的方向

- **Rust 跨平台桌面与系统层工具**：原生渲染优先于套壳，体积与内存占用优先于功能堆叠
- **AI 编码代理与技能生态**：Claude Code / Codex / MCP / agent skills 的日常重度使用
- **Windows 与 macOS 提效小工具**：窗口管理、OCR、剪贴板、输入法这一类每天要点几百次的东西
- **私有组网与 Mesh VPN**：Tailscale、ZeroTier、NetBird、EasyTier、vnt 都实际部署过，现在**主用 EasyTier、NetBird 留作备用通道**。选型看的是 NAT 穿透成功率、中继是否自己可控、以及多平台（Windows / Arch / macOS / 路由器）部署成本
- **自建服务与内网基础设施**：能自己搭就不依赖第三方

## 其它项目

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

Developer working mostly in **Rust**: native cross-platform desktop tools and network-forwarding utilities — real native GUI, no WebView, single small binary. Ships for Windows, macOS and Linux (Arch included), and also runs internal infrastructure (Docker + Caddy) and industrial automation platforms.

Highlights: [**devroute**](https://github.com/HKMV/devroute) — a ~3MB dev-time forwarder with an independent "local mirror site" mode and a SOCKS5/HTTP proxy mode; [**tun2proxy-gui**](https://github.com/HKMV/tun2proxy-gui) — a GPUI-based desktop front-end for tun2proxy; [**api-request-analyzer-browser-plugin**](https://github.com/HKMV/api-request-analyzer-browser-plugin) — a Chrome extension that breaks every request into DNS / TCP / TLS / send / wait / download phases.

Interests: Rust desktop & systems tooling, AI coding agents and skills, small Windows/macOS productivity tools, self-hosted services, and private mesh networking — Tailscale / ZeroTier / NetBird / EasyTier / vnt deployed and compared, currently running EasyTier as the primary mesh with NetBird as a backup path.

Blog: https://hkmv.github.io
