# 🛡️ CleanMac Engine

> **English:** A native, lightweight macOS cleanup tool built with SwiftUI & Shell. Features multi-depth recursive tree exploration, atmospheric progress UI, duplicate file detection, and high-safety granular deletion.
>
> **中文：** 一款原生、轻量级的 macOS 清理与大文件分析工具（基于 SwiftUI + Shell）。支持无限多层级递归展开树状视图、科技感进度面板、重复文件识别以及高安全的粒度删除。

---

## 📖 Table of Contents / 目录
- [✨ Key Features / 核心特性](#-key-features--核心特性)
- [🚀 Quick Start / 快速开始](#-quick-start--快速开始)
- [🖥️ Terminal & Shell Manual / 终端 Shell 独立使用指南](#️-terminal--shell-manual--终端-shell-独立使用指南)
- [⚠️ Limitations of `du` Search / 基于 du 搜索大文件的局限性](#️-limitations-of-du-search--基于-du-搜索大文件的局限性)
- [📄 License / 开源协议](#-license--开源协议)

---

## ✨ Key Features / 核心特性

- **English:**
  - **Multi-Depth Recursive Tree View:** Drill down into subdirectories endlessly to analyze disk usage granularly.
  - **Atmospheric Progress Panel:** Live progress bar (0–100%), elapsed timing counter, and real-time scanning path streams.
  - **High-Safety Granular Deletion:** Deletes only specific leaf files (`isDirectory == false`). Folder roots are never forcibly wiped.
  - **Duplicate Detection & Audit Panel:** Automatically identifies duplicate files and calculates potential freed space in real time.
  - **7 Preset Smart Steps:** One-click sequential execution for system logs, caches, Xcode DerivedData, package manager caches (npm/CocoaPods/pip), trash, and APFS snapshots.

- **中文：**
  - **无限层级递归树形视图：** 支持深度穿透下钻，逐级展开分析子目录占用情况。
  - **科技感进度面板：** 实时 0–100% 进度计算、耗时统计与流式扫描路径展示。
  - **高安全粒度删除：** 物理删除仅对选中的**具体叶子文件**执行 `rm -f`，绝不直接清理文件夹根目录。
  - **重复文件识别与审计面板：** 智能识别重复文件副本，实时计算预计释放容量。
  - **预设 7 大智能步骤：** 顺序清理系统日志、缓存、Xcode 编译文件、包管理器缓存、垃圾桶与 APFS 快照。

---

## 🚀 Quick Start / 快速开始

### System Requirements / 系统要求
- macOS 13.0+ (Ventura / Sonoma / Sequoia)
- Xcode 14.0+


构建步骤

Clone 仓库到本地：

git clone https://github.com/sdyubo/CleanMac-Engine.git


使用 Xcode 打开项目：

cd CleanMac-Engine
open CleanMac.xcodeproj


选择 Target: CleanMac 并直接运行 (⌘ + R)。

🤝 贡献与反馈

欢迎提交 Issue 或 Pull Request！如果你有更高效的算法（例如基于 Swift / C 的多线程文件树扫描方案），非常欢迎参与开源共建。


### Grant Full Disk Access (FDA) / 授权“完全磁盘访问权限”

> **English:**
> macOS Full Disk Access (FDA) is strictly required to scan system paths such as `~/Library/` or protected user containers.
> 1. Open **System Settings** -> **Privacy & Security** -> **Full Disk Access**.
> 2. Enable your compiled **CleanMac Engine** app.
>
> **中文：**
> macOS TCC 权限机制会拦截对 `~/Library/` 及受保护系统目录的访问。
> 1. 打开 **系统设置** -> **隐私与安全性** -> **完全磁盘访问权限**。
> 2. 将编译生成的 **CleanMac Engine** 添加并开启权限。

---

## 🖥️ Terminal & Shell Manual / 终端 Shell 独立使用指南

If you prefer operating directly in the Terminal without running the UI, you can use these native Shell commands:

如果你习惯直接在终端控制台中敲命令清理，可使用以下核心脚本：

### 1. Smart Cleanup Commands / 常用一键清理指令

```bash
# 1. Clear system & user logs / 清理系统与用户日志
rm -rf ~/Library/Logs/* /var/log/* 2>/dev/null

# 2. Clear user caches / 清理应用缓存
rm -rf ~/Library/Caches/* 2>/dev/null

# 3. Clear Xcode DerivedData & Simulator Caches / 清理 Xcode 编译缓存与模拟器数据
rm -rf ~/Library/Developer/Xcode/DerivedData/* ~/Library/Developer/CoreSimulator/Caches/* 2>/dev/null

# 4. Clear Developer Package Caches / 清理 CocoaPods, npm, pip 依赖包缓存
rm -rf ~/.npm/_cacache ~/.cocoapods/repos-mtime ~/Library/Caches/pip 2>/dev/null

# 5. Clear Trash / 清空废纸篓
rm -rf ~/.Trash/* 2>/dev/null

# 6. Thin APFS Local Time Machine Snapshots / 薄化本地 APFS 快照
sudo tmutil thinlocalpurgestorage / 9999999999 2>/dev/null




📄 开源许可证

本项目基于 MIT License 开源，允许免费商用与二次开发。
