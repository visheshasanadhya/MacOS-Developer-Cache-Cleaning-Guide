<div align="center">

# 🧹 macOS Developer Cache Cleaning Guide

**Terminal cheat sheet to rescue disk space and fix build errors on macOS.**

[![macOS](https://img.shields.io/badge/macOS-000000?style=for-the-badge&logo=apple&logoColor=white)](#)
[![Flutter](https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white)](#)
[![Android](https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white)](#)
[![Xcode](https://img.shields.io/badge/Xcode-007ACC?style=for-the-badge&logo=Xcode&logoColor=white)](#)
[![VS Code](https://img.shields.io/badge/VS_Code-0078D4?style=for-the-badge&logo=visual%20studio%20code&logoColor=white)](#)
[![WhatsApp](https://img.shields.io/badge/WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white)](#)

</div>

---

### <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/androidstudio/androidstudio-original.svg" width="20" height="20" /> Android Studio & Gradle
*Clears build cache, daemons, and old wrapper zips. Reclaims: **5–20 GB**.*

```bash
pkill -f '.*GradleDaemon.*'
rm -rf ~/.gradle/caches/*
rm -rf ~/.gradle/daemon/*
rm -rf ~/.gradle/wrapper/dists/*
```

---

### <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/android/android-original.svg" width="20" height="20" /> Android Emulator
*Clears cache, snapshots, and bloated phone storage. Reclaims: **5–12 GB**.*

```bash
adb kill-server
adb start-server
rm -rf ~/.android/avd/*.avd/cache
rm -rf ~/.android/avd/*.avd/snapshots
rm -rf ~/.android/cache/*
```

**Reset Emulator User Data** *(Reclaims 5–10+ GB)*
```bash
rm -rf ~/.android/avd/*.avd/userdata-qemu.img.qcow2
```

---

### <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/flutter/flutter-original.svg" width="20" height="20" /> Flutter & Dart
*Clears global pub cache and stale project builds. Reclaims: **5–15 GB**.*

```bash
flutter pub cache clean -f
rm -rf ~/.pub-cache
```

**Repair Global Package Cache**
```bash
flutter pub cache repair
```

**Bulk Clean All Flutter Projects** *(Run in `~/StudioProjects`)*
```bash
find . -maxdepth 3 -type d -name "build" -exec rm -rf {} +
find . -maxdepth 3 -type d -name ".dart_tool" -exec rm -rf {} +
```

---

### <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/xcode/xcode-original.svg" width="20" height="20" /> Xcode Cache
*Clears DerivedData, archives, and build indexes. Reclaims: **5–20 GB**.*

```bash
rm -rf ~/Library/Developer/Xcode/DerivedData/*
rm -rf ~/Library/Developer/Xcode/Archives/*
rm -rf ~/Library/Developer/Xcode/iOS\ DeviceSupport/*
rm -rf ~/Library/Developer/Xcode/ModuleCache.noindex/*
rm -rf ~/Library/Caches/com.apple.dt.Xcode
```

---

### <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/apple/apple-original.svg" width="20" height="20" /> iOS Simulator
*Clears simulator runtimes, caches, and crash logs. Reclaims: **2–10 GB**.*

```bash
xcrun simctl shutdown all
xcrun simctl erase all
xcrun simctl delete unavailable
rm -rf ~/Library/Developer/CoreSimulator/Caches/*
rm -rf ~/Library/Logs/CoreSimulator/*
```

---

### <img src="https://cdn.simpleicons.org/cocoapods/EE3322" width="20" height="20" /> CocoaPods
*Clears pod cache and broken specs. Reclaims: **1–3 GB**.*

```bash
pod cache clean --all
rm -rf ~/Library/Caches/CocoaPods
rm -rf ~/.cocoapods/cache
```

---

### <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/chrome/chrome-original.svg" width="20" height="20" /> Google Chrome Cache
*Clears browser cache and site data. Reclaims: **2–6 GB**.*

```bash
rm -rf ~/Library/Caches/Google/Chrome
rm -rf ~/Library/Application\ Support/Google/Chrome/Default/Cache
rm -rf ~/Library/Application\ Support/Google/Chrome/Default/Code\ Cache
```

---

### <img src="https://cdn.simpleicons.org/whatsapp/25D366" width="20" height="20" /> WhatsApp Cache & Shared Files
*Clears update installer cache and temp files. Reclaims: **1–5 GB**.*

```bash
rm -rf ~/Library/Caches/net.whatsapp.WhatsApp/*
```

> **Tip:** In WhatsApp, go to **Settings (`Cmd + ,`) → Storage and Data → Manage Storage → Larger than 5 MB** to delete shared `.apk`/`.aab` files.

**Delete All Built & Downloaded APKs / AABs** *(Reclaims: **1–5 GB**)*
```bash
find ~/StudioProjects ~/Downloads -type f \( -name "*.apk" -o -name "*.aab" \) -delete
```

---

### <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/android/android-original.svg" width="20" height="20" /> Android SDK Temp
*Clears SDK temporary packages and installer residue.*

```bash
rm -rf ~/Library/Android/sdk/.temp/*
rm -rf ~/Library/Android/sdk/.knownPackages
```

---

### <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vscode/vscode-original.svg" width="20" height="20" /> VS Code Cache
*Clears workspace storage and editor cache.*

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

### <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg" width="20" height="20" /> AI Developer Tools Cache
*Clears AI assistant logs and updater cache.*

```bash
rm -rf ~/Library/Caches/com.openai.codex/*
rm -rf ~/Library/Caches/com.google.antigravity-ide.ShipIt/*
```

---

### <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/apple/apple-original.svg" width="20" height="20" /> macOS System Cache & QuickLook
*Clears user cache, logs, and QuickLook previews.*

```bash
rm -rf ~/Library/Caches/*
rm -rf ~/Library/Logs/*
qlmanage -r cache
qlmanage -r
```

---

### <img src="https://cdn.simpleicons.org/cloudflare/F38020" width="20" height="20" /> DNS & Network Cache
*Flushes DNS resolver and mDNSResponder.*

```bash
sudo dscacheutil -flushcache; sudo killall -HUP mDNSResponder
```

---

### <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/homebrew/homebrew-original.svg" width="20" height="20" /> Homebrew Cache
*Clears Homebrew bottle downloads and cache.*

```bash
brew cleanup -s
rm -rf ~/Library/Caches/Homebrew
```

---

### <img src="https://cdn.jsdelivr.net/npm/@tabler/icons/icons/trash.svg" width="20" height="20" /> Trash
*Empties the macOS Trash.*

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
