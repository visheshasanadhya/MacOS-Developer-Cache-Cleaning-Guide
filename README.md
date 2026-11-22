<div align="center">

# 🧹 macOS Developer Cache Cleaning Guide

**Emergency & maintenance terminal cheat sheet to rescue disk space and fix build errors.**

[![macOS](https://img.shields.io/badge/macOS-000000?style=for-the-badge&logo=apple&logoColor=white)](#)
[![Flutter](https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white)](#)
[![Android](https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white)](#)
[![Xcode](https://img.shields.io/badge/Xcode-007ACC?style=for-the-badge&logo=Xcode&logoColor=white)](#)
[![VS Code](https://img.shields.io/badge/VS_Code-0078D4?style=for-the-badge&logo=visual%20studio%20code&logoColor=white)](#)

</div>

---

> [!TIP]
> ### ⚡ 10-Second Emergency Cleanup
> Instantly reclaims **15–25 GB** when your build fails due to *"No space left on device"*:
> ```bash
> pkill -f '.*GradleDaemon.*'
> rm -rf ~/.gradle/caches/* ~/.gradle/daemon/* ~/Library/Developer/Xcode/DerivedData/* ~/Library/Caches/Google/Chrome/*
> ```

---

<div align="center">

### 🧭 Quick Navigation

[🤖 Gradle](#gradle) &nbsp;|&nbsp;
[📲 Emulator](#emulator) &nbsp;|&nbsp;
[🎯 Flutter](#flutter) &nbsp;|&nbsp;
[🔧 Xcode](#xcode) &nbsp;|&nbsp;
[📱 Simulator](#simulator) &nbsp;|&nbsp;
[🍫 CocoaPods](#cocoapods)

[🌐 Chrome](#chrome) &nbsp;|&nbsp;
[💬 WhatsApp](#whatsapp) &nbsp;|&nbsp;
[🔩 Android SDK](#android-sdk) &nbsp;|&nbsp;
[💻 VS Code](#vscode) &nbsp;|&nbsp;
[🤖 AI Tools](#ai-tools)

[💾 macOS System](#system-cache) &nbsp;|&nbsp;
[🌐 DNS](#dns) &nbsp;|&nbsp;
[🍺 Homebrew](#homebrew) &nbsp;|&nbsp;
[🗑️ Trash](#trash)

</div>

---

## 📚 Commands by Category

<a id="gradle"></a>
### 🤖 Android Studio & Gradle
*Fixes build failures, daemon locks, and old Gradle wrapper downloads. Reclaims: **5–20 GB**.*

```bash
pkill -f '.*GradleDaemon.*'
rm -rf ~/.gradle/caches/*
rm -rf ~/.gradle/daemon/*
rm -rf ~/.gradle/wrapper/dists/*
```

---

<a id="emulator"></a>
### 📲 Android Emulator
*Fixes emulator crashes, snapshot corruption, and bloated storage. Reclaims: **5–12 GB**.*

```bash
adb kill-server
adb start-server
rm -rf ~/.android/avd/*.avd/cache
rm -rf ~/.android/avd/*.avd/snapshots
rm -rf ~/.android/cache/*
```

**Reset Emulator User Data** *(Reclaims 5–10+ GB without deleting the device)*
```bash
rm -rf ~/.android/avd/*.avd/userdata-qemu.img.qcow2
```

---

<a id="flutter"></a>
### 🎯 Flutter & Dart
*Fixes pub package corruption and stale build output bloat. Reclaims: **5–15 GB**.*

```bash
flutter pub cache clean -f
rm -rf ~/.pub-cache
```

**Repair Global Package Cache**
```bash
flutter pub cache repair
```

**Bulk Clean All Flutter Projects** *(Run inside your projects directory, e.g. `~/StudioProjects`)*
```bash
find . -maxdepth 3 -type d -name "build" -exec rm -rf {} +
find . -maxdepth 3 -type d -name ".dart_tool" -exec rm -rf {} +
```

---

<a id="xcode"></a>
### 🔧 Xcode Cache
*Fixes Xcode build failures, indexing loops, and compilation errors. Reclaims: **5–20 GB**.*

```bash
rm -rf ~/Library/Developer/Xcode/DerivedData/*
rm -rf ~/Library/Developer/Xcode/Archives/*
rm -rf ~/Library/Developer/Xcode/iOS\ DeviceSupport/*
rm -rf ~/Library/Developer/Xcode/ModuleCache.noindex/*
rm -rf ~/Library/Caches/com.apple.dt.Xcode
```

---

<a id="simulator"></a>
### 📱 iOS Simulator
*Fixes simulator boot failures, runtime errors, and crash log buildup. Reclaims: **2–10 GB**.*

```bash
xcrun simctl shutdown all
xcrun simctl erase all
xcrun simctl delete unavailable
rm -rf ~/Library/Developer/CoreSimulator/Caches/*
rm -rf ~/Library/Logs/CoreSimulator/*
```

---

<a id="cocoapods"></a>
### 🍫 CocoaPods
*Fixes iOS pod dependency management, broken specs, and stale downloads. Reclaims: **1–3 GB**.*

```bash
pod cache clean --all
rm -rf ~/Library/Caches/CocoaPods
rm -rf ~/.cocoapods/cache
```

---

<a id="chrome"></a>
### 🌐 Google Chrome Cache
*Fixes browser slowness, DevTools lag, and gigabytes of cached media. Reclaims: **2–6 GB**.*

```bash
rm -rf ~/Library/Caches/Google/Chrome
rm -rf ~/Library/Application\ Support/Google/Chrome/Default/Cache
rm -rf ~/Library/Application\ Support/Google/Chrome/Default/Code\ Cache
```

---

<a id="whatsapp"></a>
### 💬 WhatsApp Cache & Shared Files
*Clears WhatsApp auto-update installer bloat and temporary caches. Reclaims: **1–5 GB**.*

```bash
rm -rf ~/Library/Caches/net.whatsapp.WhatsApp/*
```

> [!NOTE]
> **How to delete shared APK & AAB files in WhatsApp:**  
> WhatsApp stores sent/received APKs/AABs in its internal database. To clear them:  
> Open WhatsApp → **Settings (`Cmd + ,`) → Storage and Data → Manage Storage** → Select **"Larger than 5 MB"** → Select All and Delete.

---

<a id="android-sdk"></a>
### 🔩 Android SDK Temp
*Clears Android SDK temporary packages and installation residue.*

```bash
rm -rf ~/Library/Android/sdk/.temp/*
rm -rf ~/Library/Android/sdk/.knownPackages
```

---

<a id="vscode"></a>
### 💻 VS Code Cache
*Fixes VS Code extension corruption and performance lag.*

```bash
rm -rf ~/Library/Application\ Support/Code/Cache
rm -rf ~/Library/Application\ Support/Code/CachedData
rm -rf ~/Library/Application\ Support/Code/User/workspaceStorage
rm -rf ~/Library/Logs/Code
```

**Reset Corrupted Extensions** *(Optional)*
```bash
rm -rf ~/.vscode/extensions
```

---

<a id="ai-tools"></a>
### 🤖 AI Developer Tools Cache
*Clears temporary model cache, assistant logs, and background updater files.*

```bash
rm -rf ~/Library/Caches/com.openai.codex/*
rm -rf ~/Library/Caches/com.google.antigravity-ide.ShipIt/*
```

---

<a id="system-cache"></a>
### 💾 macOS System Cache & QuickLook
*Fixes slow system performance, diagnostic lag, and corrupt preview thumbnails.*

```bash
rm -rf ~/Library/Caches/*
rm -rf ~/Library/Logs/*
qlmanage -r cache
qlmanage -r
```

---

<a id="dns"></a>
### 🌐 DNS & Network Cache
*Fixes localhost connection glitches, API endpoint routing errors, and stale DNS.*

```bash
sudo dscacheutil -flushcache; sudo killall -HUP mDNSResponder
```

---

<a id="homebrew"></a>
### 🍺 Homebrew Cache
*Clears Homebrew bottle downloads and frees package cache space.*

```bash
brew cleanup -s
rm -rf ~/Library/Caches/Homebrew
```

---

<a id="trash"></a>
### 🗑️ Trash
*Empties trash to free disk space immediately.*

```bash
rm -rf ~/.Trash/*
```

---

<div align="center">

**Made with ❤️ for macOS Developers**

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)

⭐ **Star this repository if it helped you free up disk space!**

</div>
