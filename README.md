# MacOS-Developer-Cache-Cleaning-Guide

<div align="center">

![macOS](https://img.shields.io/badge/macOS-000000?style=for-the-badge&logo=apple&logoColor=white)
![Xcode](https://img.shields.io/badge/Xcode-007ACC?style=for-the-badge&logo=Xcode&logoColor=white)
![Flutter](https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white)
![Android](https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white)
![VS Code](https://img.shields.io/badge/VS_Code-0078D4?style=for-the-badge&logo=visual%20studio%20code&logoColor=white)

**Complete Terminal Cheat Sheet for Developer Cache Management**

</div>

---

## ⚠️ BEFORE YOU START

> **🚨 CLOSE THESE APPS FIRST:**
> 
> ✅ Xcode  
> ✅ Android Studio  
> ✅ VS Code  
> ✅ Chrome  
> ✅ Simulators/Emulators

---

## 🚀 AUTO CLEAN SCRIPT

### **Step 1: Create the Script**

```bash
nano clean_all.sh
```

### **Step 2: Copy & Paste This Complete Script**

```bash
#!/bin/bash

# 💾 macOS System Cache - Fixes slow system performance and app lag
rm -rf ~/Library/Caches/*
rm -rf ~/Library/Logs/*
sudo rm -rf /Library/Caches/*

# 🔧 Xcode DerivedData - Fixes Xcode build and indexing issues
rm -rf ~/Library/Developer/Xcode/DerivedData/*

# 🔧 Xcode Module Cache - Fixes module compilation errors
rm -rf ~/Library/Developer/Xcode/ModuleCache.noindex/*

# 🔧 Xcode Archives - Removes old app archives
rm -rf ~/Library/Developer/Xcode/Archives/*

# 🔌 Xcode Device Support - Clears old iOS device pairing data
rm -rf ~/Library/Developer/Xcode/iOS\ DeviceSupport/*

# 📱 iOS Simulator Cache - Fixes simulator performance issues
rm -rf ~/Library/Developer/CoreSimulator/Caches/*

# 📱 iOS Simulator Logs - Clears simulator crash logs
rm -rf ~/Library/Logs/CoreSimulator/*

# 🎯 Flutter pub-cache - Fixes Flutter package dependency issues
rm -rf ~/.pub-cache/*

# 🤖 Gradle Cache - Fixes Android build and dependency errors
rm -rf ~/.gradle/caches/*

# 🤖 Android SDK folder - Clears Android emulator and SDK cache
rm -rf ~/.android/*

# 💻 VS Code Cache - Fixes VS Code performance and extension issues
rm -rf ~/Library/Application\ Support/Code/Cache/*
rm -rf ~/Library/Application\ Support/Code/CachedData/*
rm -rf ~/Library/Application\ Support/Code/Service\ Worker/CacheStorage/*

# 🌐 Chrome Cache - Fixes browser slowness and DevTools issues
rm -rf ~/Library/Caches/Google/Chrome/*

# 🍫 CocoaPods Cache - Fixes iOS dependency management issues
rm -rf ~/.cocoapods/*
rm -rf ~/Library/Caches/CocoaPods/*

echo "------------------------------------------------------------"
echo "🎉 All Done! Restart Mac for best performance."
```

### **Step 3: Make Executable & Run**

```bash
chmod +x clean_all.sh
./clean_all.sh
```

---

## 📚 MANUAL COMMANDS BY CATEGORY

### 💾 **macOS System Cache**
Fixes: Slow system performance and app lag

```bash
rm -rf ~/Library/Caches/*
rm -rf ~/Library/Logs/*
```

---

### 🌐 **Google Chrome Cache**
Fixes: Browser slowness and DevTools performance issues

```bash
rm -rf ~/Library/Caches/Google/Chrome
rm -rf ~/Library/Application\ Support/Google/Chrome/Default/Cache
```

---

### 🎯 **Flutter & Dart**
Fixes: Flutter build errors, pub dependencies, and package issues

```bash
flutter clean
flutter pub cache repair
rm -rf .dart_tool build
```

**Hard Reset** (Only for severe dependency issues)

```bash
rm -rf ~/.pub-cache
flutter pub get
```

---

### 🔧 **Xcode Cache**
Fixes: Xcode build failures, indexing problems, and compilation errors

```bash
rm -rf ~/Library/Developer/Xcode/DerivedData/*
rm -rf ~/Library/Developer/Xcode/Archives/*
rm -rf ~/Library/Developer/Xcode/iOS\ DeviceSupport/*
```

**Clear iOS Pairing Data** (Fixes device connection issues)

```bash
rm -rf ~/Library/Developer/Xcode/iOS\ DeviceSupport/*
rm -rf ~/Library/Developer/Xcode/DerivedData/*
```

---

### 📱 **iOS Simulator**
Fixes: Simulator boot failures, runtime errors, and performance issues

```bash
xcrun simctl shutdown all
xcrun simctl erase all
xcrun simctl delete unavailable
```

---

### 🍫 **CocoaPods**
Fixes: iOS dependency management and pod installation issues

```bash
pod cache clean --all
rm -rf ~/Library/Caches/CocoaPods
```

**Project Reset** (Run from project root)

```bash
cd ios
pod deintegrate
rm -rf Pods Podfile.lock
pod install
cd ..
```

---

### 🤖 **Android Studio & Gradle**
Fixes: Gradle build errors and dependency resolution issues

```bash
rm -rf ~/.gradle/caches
rm -rf ~/.gradle/daemon
```

---

### 📲 **Android Emulator**
Fixes: Android emulator boot failures and snapshot corruption

```bash
adb kill-server
adb start-server
rm -rf ~/.android/avd/*.avd/cache
rm -rf ~/.android/avd/*.avd/snapshots
```

---

### 🔩 **Android SDK Temp**
Fixes: Clears Android SDK temporary and cache files

```bash
rm -rf ~/Library/Android/sdk/.temp
rm -rf ~/Library/Android/sdk/.knownPackages
```

---

### 💻 **VS Code Cache**
Fixes: VS Code extension corruption and performance lag

```bash
rm -rf ~/Library/Application\ Support/Code/Cache
rm -rf ~/Library/Application\ Support/Code/CachedData
rm -rf ~/Library/Application\ Support/Code/User/workspaceStorage
rm -rf ~/Library/Logs/Code
```

**Extensions Reset** (Optional, only if corrupted)

```bash
rm -rf ~/.vscode/extensions
```

---

### 🍺 **Homebrew Cache**
Fixes: Clears Homebrew package cache and frees disk space

```bash
brew cleanup -s
rm -rf ~/Library/Caches/Homebrew
```

---

### 👁️ **Watchman**
Fixes: React Native file watching issues

```bash
watchman watch-del-all
```

---

### 🗑️ **Trash**
Fixes: Empties trash to free disk space

```bash
rm -rf ~/.Trash/*
```

---

## 🔄 QUICK USEFUL COMMANDS

```bash
# 🎯 Flutter Commands
flutter clean
flutter pub get

# 📱 iOS Simulator Commands
xcrun simctl shutdown all
xcrun simctl erase all

# 🤖 Android Emulator Commands
adb kill-server
adb start-server
```

---

## 🛠️ SAFE & AGGRESSIVE CLEANING MODES

### **Create the Script**

```bash
nano clean.sh
```

### **Copy & Paste This Script**

```bash
#!/bin/bash
# 🧹 macOS Developer Cleaning Script
# Modes:
# safe       → Recommended, no system risk
# aggressive → Deep clean, requires sudo

MODE=$1

if [[ "$MODE" == "safe" ]]; then
  # 💾 macOS User Cache - Fixes slow system and app lag
  rm -rf ~/Library/Caches/*
  rm -rf ~/Library/Logs/*

  # 🎯 Flutter - Fixes pub, build & dependency errors
  flutter clean
  rm -rf ~/.pub-cache/.lock

  # 🔧 Xcode - Fixes build, indexing, pairing issues
  rm -rf ~/Library/Developer/Xcode/DerivedData/*
  rm -rf ~/Library/Developer/Xcode/ModuleCache.noindex/*
  rm -rf ~/Library/Developer/Xcode/iOS\ DeviceSupport/*

  # 📱 iOS Simulator - Fixes boot & runtime errors
  xcrun simctl shutdown all
  rm -rf ~/Library/Developer/CoreSimulator/Caches/*
  rm -rf ~/Library/Logs/CoreSimulator/*

  # 🤖 Android Studio & Emulator - Fixes Gradle & emulator issues
  rm -rf ~/.gradle/caches/*
  rm -rf ~/.android/avd/*.avd/cache

  # 💻 VS Code - Fixes extension & cache corruption
  rm -rf ~/Library/Application\ Support/Code/Cache/*
  rm -rf ~/Library/Application\ Support/Code/CachedData/*

  # 🌐 Chrome - Fixes browser lag & DevTools issues
  rm -rf ~/Library/Caches/Google/Chrome/*

  echo "✅ Safe mode cleaning completed!"

elif [[ "$MODE" == "aggressive" ]]; then
  # 💾 SYSTEM CACHE - Deep system cleanup
  rm -rf ~/Library/Caches/*
  rm -rf ~/Library/Logs/*
  sudo rm -rf /Library/Caches/*

  # 🔧 Xcode - Deep clean
  rm -rf ~/Library/Developer/Xcode/*
  rm -rf ~/Library/Developer/CoreSimulator/*

  # 🎯 Flutter - Deep reset
  rm -rf ~/.pub-cache
  rm -rf .dart_tool build

  # 🤖 Android - Deep reset
  rm -rf ~/.gradle
  rm -rf ~/.android

  # 💻 VS Code - Deep reset
  rm -rf ~/Library/Application\ Support/Code
  rm -rf ~/.vscode

  # 🌐 Chrome - Full cache reset
  rm -rf ~/Library/Caches/Google/Chrome
  rm -rf ~/Library/Application\ Support/Google/Chrome/Default/Cache

  echo "✅ Aggressive mode cleaning completed!"
  echo "⚠️  Please restart your Mac for best results."

else
  echo "❌ Usage: ./clean.sh safe | aggressive"
  echo ""
  echo "Examples:"
  echo "  ./clean.sh safe        → Safe cleaning (recommended)"
  echo "  sudo ./clean.sh aggressive → Deep cleaning (requires sudo)"
fi
```

### **Make Executable**

```bash
chmod +x clean.sh
```

### **Run SAFE Mode**

```bash
./clean.sh safe
```

### **Run AGGRESSIVE Mode**

```bash
sudo ./clean.sh aggressive
```

---

## ⚙️ TERMINAL TIPS

### **ZSH Configuration**

```bash
# Reload terminal config
source ~/.zshrc

# Edit config file
nano ~/.zshrc
```

### **Nano Editor Shortcuts**

| Shortcut | Action |
|----------|--------|
| `CTRL + O` | 💾 Save file |
| `CTRL + X` | 🚪 Exit nano |
| `CTRL + W` | 🔍 Search in file |

---

## 🚨 SAFETY WARNINGS

### ❌ **NEVER RUN THESE COMMANDS:**

```bash
# ⛔ THESE WILL DESTROY YOUR MAC!
rm -rf /System
rm -rf /Library
rm -rf ~/Documents
rm -rf ~/Desktop
```

> **🔥 DANGER:**  
> - 💀 Will damage macOS beyond repair  
> - 📁 Will delete ALL your files  
> - 🚫 Will make Mac unbootable  
> - ⚠️ Requires complete reinstallation

---

## 📊 DISK SPACE IMPACT

| Category | Impact | Space Saved |
|----------|--------|-------------|
| 💾 macOS System Cache | 🔴 High | 1-5 GB |
| 🔧 Xcode DerivedData | 🔴 High | 5-20 GB |
| 📱 iOS Simulator | 🟡 Medium | 2-10 GB |
| 🎯 Flutter Cache | 🟡 Medium | 500 MB - 2 GB |
| 🤖 Android/Gradle | 🔴 High | 2-15 GB |
| 💻 VS Code Cache | 🟢 Low | 100-500 MB |
| 🌐 Chrome Cache | 🟡 Medium | 500 MB - 2 GB |
| 🍫 CocoaPods | 🟢 Low | 100-500 MB |

---

## 🎯 WHEN TO USE EACH MODE

### **Use SAFE Mode:**
- ✅ Regular maintenance
- ✅ Minor performance issues
- ✅ Build errors after updates
- ✅ First time cleaning

### **Use AGGRESSIVE Mode:**
- ⚠️ Major system slowdown
- ⚠️ Persistent build failures
- ⚠️ Critically low disk space
- ⚠️ Last resort option

---

<div align="center">

**Made with ❤️ for macOS Developers**

![Platform](https://img.shields.io/badge/Platform-macOS-blue?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)
![Maintained](https://img.shields.io/badge/Maintained-Yes-brightgreen?style=flat-square)

**⭐ Star this repo if it helped you!**

</div>