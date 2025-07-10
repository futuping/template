# 🌍 跨平台构建系统

## 概述

本项目支持**全平台构建**，可以为 7 大类平台生成优化的二进制文件和库文件。我们的 CI/CD 系统能够自动为所有支持的平台进行构建、测试和发布。

## 🎯 支持的平台

### 🖥️ 桌面平台
| 平台 | 架构 | 目标三元组 | 状态 |
|------|------|------------|------|
| **Linux** | x86_64 | `x86_64-unknown-linux-gnu` | ✅ 完全支持 |
| **Linux** | ARM64 | `aarch64-unknown-linux-gnu` | ✅ 交叉编译 |
| **Linux** | x86_64 (musl) | `x86_64-unknown-linux-musl` | ✅ 静态链接 |
| **Linux** | i686 | `i686-unknown-linux-gnu` | ✅ 交叉编译 |
| **Windows** | x86_64 (MSVC) | `x86_64-pc-windows-msvc` | ✅ 原生构建 |
| **Windows** | i686 (MSVC) | `i686-pc-windows-msvc` | ✅ 原生构建 |
| **Windows** | x86_64 (GNU) | `x86_64-pc-windows-gnu` | ✅ 交叉编译 |
| **macOS** | Intel | `x86_64-apple-darwin` | ✅ 原生构建 |
| **macOS** | Apple Silicon | `aarch64-apple-darwin` | ✅ 原生构建 |

### 📱 移动平台
| 平台 | 架构 | 目标三元组 | 产物类型 | 状态 |
|------|------|------------|----------|------|
| **iOS** | ARM64 (设备) | `aarch64-apple-ios` | 静态库 (.a) | ✅ Xcode 集成 |
| **iOS** | x86_64 (模拟器) | `x86_64-apple-ios` | 静态库 (.a) | ✅ 模拟器支持 |
| **iOS** | ARM64 (模拟器) | `aarch64-apple-ios-sim` | 静态库 (.a) | ✅ M1 Mac 模拟器 |
| **Android** | ARM64 | `aarch64-linux-android` | 共享库 (.so) | ✅ NDK 21+ |
| **Android** | ARMv7 | `armv7-linux-androideabi` | 共享库 (.so) | ✅ 32位设备 |
| **Android** | x86_64 | `x86_64-linux-android` | 共享库 (.so) | ✅ 模拟器 |
| **Android** | x86 | `i686-linux-android` | 共享库 (.so) | ✅ 模拟器 |

### 🌐 Web 平台
| 平台 | 目标三元组 | 产物类型 | 用途 | 状态 |
|------|------------|----------|------|------|
| **WebAssembly** | `wasm32-unknown-unknown` | .wasm + .js | 浏览器、Node.js | ✅ wasm-pack |
| **WASI** | `wasm32-wasi` | .wasm | 服务器端 WASM | ✅ wasmtime |

### 🔮 实验性平台
| 平台 | 架构 | 目标三元组 | 状态 |
|------|------|------------|------|
| **HarmonyOS** | ARM64 | `aarch64-unknown-linux-ohos` | 🧪 实验性 |
| **HarmonyOS** | x86_64 | `x86_64-unknown-linux-ohos` | 🧪 实验性 |

## 🚀 构建流程

### 自动化构建
构建系统分为 4 个并行的作业：

1. **🖥️ desktop-build**: 桌面平台构建
2. **📱 mobile-build**: 移动平台构建  
3. **🌐 web-build**: Web 平台构建
4. **🔮 special-build**: 特殊平台构建

### 触发条件
- **推送到 main**: 触发所有平台构建
- **Pull Request**: 触发所有平台构建
- **发布标签**: 创建完整的发布包

## 🛠️ 开发环境设置

### 基础要求
```bash
# 安装 Rust
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

# 安装交叉编译工具
cargo install cross
```

### 桌面平台开发
```bash
# 添加目标平台
rustup target add x86_64-unknown-linux-musl
rustup target add aarch64-unknown-linux-gnu
rustup target add x86_64-pc-windows-gnu
```

### 移动平台开发

#### iOS 开发 (仅 macOS)
```bash
# 添加 iOS 目标
rustup target add aarch64-apple-ios
rustup target add x86_64-apple-ios
rustup target add aarch64-apple-ios-sim

# 需要 Xcode 和 iOS SDK
sudo xcode-select --install
```

#### Android 开发
```bash
# 安装 Android NDK
# 通过 Android Studio 或直接下载

# 添加 Android 目标
rustup target add aarch64-linux-android
rustup target add armv7-linux-androideabi
rustup target add x86_64-linux-android
rustup target add i686-linux-android

# 设置环境变量
export ANDROID_HOME=/path/to/android-sdk
export ANDROID_NDK_HOME=/path/to/ndk
```

### Web 平台开发
```bash
# 安装 WebAssembly 工具
rustup target add wasm32-unknown-unknown
rustup target add wasm32-wasi

# 安装 wasm-pack
cargo install wasm-pack

# 安装 wasmtime (用于 WASI)
curl https://wasmtime.dev/install.sh -sSf | bash
```

## 📦 本地构建

### 构建所有桌面平台
```bash
# Linux
cargo build --release --target x86_64-unknown-linux-gnu
cross build --release --target aarch64-unknown-linux-gnu
cross build --release --target x86_64-unknown-linux-musl

# Windows (在 Linux/macOS 上)
cross build --release --target x86_64-pc-windows-msvc

# macOS
cargo build --release --target x86_64-apple-darwin
cargo build --release --target aarch64-apple-darwin
```

### 构建移动平台
```bash
# iOS (仅在 macOS 上)
cargo build --release --target aarch64-apple-ios
cargo build --release --target x86_64-apple-ios

# Android
cargo build --release --target aarch64-linux-android
cargo build --release --target armv7-linux-androideabi
```

### 构建 Web 平台
```bash
# WebAssembly
wasm-pack build --target web --out-dir pkg-web
wasm-pack build --target nodejs --out-dir pkg-node

# WASI
cargo build --release --target wasm32-wasi
```

## 📋 配置文件

### Cargo.toml 配置示例
```toml
[lib]
name = "your_project"
crate-type = ["cdylib", "staticlib", "rlib"]

# 移动平台特定配置
[target.'cfg(target_os = "ios")']
# iOS 特定依赖

[target.'cfg(target_os = "android")']
# Android 特定依赖
```

### .cargo/config.toml 示例
```toml
# Android 链接器配置
[target.aarch64-linux-android]
linker = "aarch64-linux-android21-clang"

[target.armv7-linux-androideabi]
linker = "armv7a-linux-androideabi21-clang"

# iOS 链接器配置
[target.aarch64-apple-ios]
linker = "clang"

[target.x86_64-apple-ios]
linker = "clang"
```

## 🔧 故障排除

### 常见问题

#### 1. Android NDK 链接错误
```bash
# 确保 NDK 路径正确
echo $ANDROID_NDK_HOME
ls $ANDROID_NDK_HOME/toolchains/llvm/prebuilt/

# 重新配置链接器
cat ~/.cargo/config.toml
```

#### 2. iOS 构建失败
```bash
# 确保 Xcode 工具链
xcode-select --print-path
xcrun --sdk iphoneos --show-sdk-path

# 检查目标是否安装
rustup target list --installed | grep ios
```

#### 3. WASM 优化问题
```bash
# 安装优化工具
cargo install wasm-opt

# 手动优化
wasm-opt -Oz input.wasm -o output.wasm
```

### 性能优化

#### 发布构建优化
```toml
[profile.release]
opt-level = 3
lto = true
codegen-units = 1
panic = 'abort'

# WASM 特定优化
[profile.release.package."*"]
opt-level = 3
```

## 📊 CI/CD 集成

### GitHub Actions 功能
- ✅ **并行构建**: 4 个平台同时构建
- ✅ **缓存优化**: 智能缓存策略
- ✅ **产物管理**: 自动打包和上传
- ✅ **发布自动化**: 标签推送自动发布
- ✅ **错误容忍**: 实验性平台不影响主流程

### 本地测试
```bash
# 模拟 CI 环境
act -j desktop-build
act -j mobile-build
act -j web-build
```

## 🚀 发布管理

### 自动发布
推送标签即可触发完整的多平台发布：
```bash
git tag v1.0.0
git push origin v1.0.0
```

### 发布产物结构
```
release/
├── desktop-all-platforms.tar.gz     # 所有桌面平台
├── mobile-all-platforms.tar.gz      # 所有移动平台  
├── web-all-platforms.tar.gz         # Web 平台
├── special-platforms.tar.gz         # 实验性平台
└── individual files...               # 单独的平台文件
```

## 📈 后续计划

### 即将支持的平台
- **FreeBSD**: `x86_64-unknown-freebsd`
- **RISC-V**: `riscv64gc-unknown-linux-gnu`
- **更多嵌入式平台**: ARM Cortex-M 系列

### 优化计划
- 🔄 增量构建优化
- 📊 构建时间监控
- 🔍 更细粒度的测试覆盖
- 📱 移动平台集成测试

---

> 💡 **提示**: 这个跨平台构建系统为你的 Rust 项目提供了业界最全面的平台支持。如有特殊需求，请参考各平台的官方文档进行定制化配置。 