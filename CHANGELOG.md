# Changelog

All notable changes to this project will be documented in this file.

---
## [0.5.0]($REPO/compare/v0.4.2..v0.5.0) - 2025-07-12

### 🚀 Features

- enhance changelog and CI/CD workflow configuration - ([b1b9070]($REPO/commit/b1b907082047d2304a57dc0908f9f088e28cad3c)) - Maverick Tuping Fu

### ⚙️ Miscellaneous Tasks

- add markdownlint ignore file for CHANGELOG.md - ([29d8ba4]($REPO/commit/29d8ba4772cc70db9da6d228de9de585bfa24eeb)) - Maverick Tuping Fu
- bump version to 0.5.0 and update changelog - ([bd78d02]($REPO/commit/bd78d02e08a5eee0906eb62781a50cdb3034a32a)) - Maverick Tuping Fu

---
## [0.4.2]($REPO/compare/v0.4.1..v0.4.2) - 2025-07-12

### ⚙️ Miscellaneous Tasks

- update changelog and workflows - ([dfc4a2d]($REPO/commit/dfc4a2d93bb6ba5b039155978139c92dbeaebbe7)) - Maverick Tuping Fu

---
## [0.4.1]($REPO/compare/v0.4.0..v0.4.1) - 2025-07-12

### 🐛 Bug Fixes

- 修复 GitHub Release 中 changelog 的 Markdown 格式问题 - ([c322bcf]($REPO/commit/c322bcff91d39efc57fdb3b2a8fe47fd12722e9f)) - Maverick Tuping Fu

### ⚙️ Miscellaneous Tasks

- 更新版本号到 0.4.0 - ([2f13e37]($REPO/commit/2f13e37c4775032803fbbf75ba7108d1d8b5f19e)) - Maverick Tuping Fu
- 更新 Cargo.lock 以匹配版本 0.4.0 - ([ff04e49]($REPO/commit/ff04e49f485bd6fb3fa0e52c125f086423723671)) - Maverick Tuping Fu
- 更新版本号到 0.4.1 - ([3ed36a2]($REPO/commit/3ed36a2162eac72fe882e31239c6682b41c585db)) - Maverick Tuping Fu

---
## [0.4.0]($REPO/compare/v0.3.1..v0.4.0) - 2025-07-11

### 🚀 Features

- 升级到完整的 Rust CI/CD 管道 - ([b26bd1b]($REPO/commit/b26bd1bc4460246c399c8ca350b205ac1c3596a6)) - Maverick Tuping Fu

---
## [0.3.1]($REPO/compare/v0.3.0..v0.3.1) - 2025-07-11

### 🐛 Bug Fixes

- 添加最低支持的 Rust 版本 (MSRV) 配置 - ([f42ccb6]($REPO/commit/f42ccb678fa6893a48d1fe11d2e94f89dc9ed1d7)) - Maverick Tuping Fu

---
## [0.3.0]($REPO/compare/v0.2.1..v0.3.0) - 2025-07-11

### 🚜 Refactor

- 重构 CI/CD 工作流配置 - ([8ea4e93]($REPO/commit/8ea4e93e45d6a714c65b27c5a1c73650cb18a5de)) - Maverick Tuping Fu

---
## [0.2.1]($REPO/compare/v0.2.0..v0.2.1) - 2025-07-11

### 💼 Other

- 工作流名称从 build 改为 ci-cd - ([a1a83b9]($REPO/commit/a1a83b907a1b8b7088b9a2e9c399c31440fd2e88)) - Maverick Tuping Fu

---
## [0.2.0]($REPO/compare/v0.1.4..v0.2.0) - 2025-07-11

### 💼 Other

- 实现 CodeQL 优先的串行发布策略 - ([819dbb8]($REPO/commit/819dbb8ae8edd3801a217ac3fb77a81aa5c2902b)) - Maverick Tuping Fu

---
## [0.1.4]($REPO/compare/v0.1.3..v0.1.4) - 2025-07-11

### 💼 Other

- 解决发布文件路径 404 错误 - ([ed66f00]($REPO/commit/ed66f005f4469ab4d3ae03151cb32cd2bef289b4)) - Maverick Tuping Fu

---
## [0.1.3]($REPO/compare/v0.1.2..v0.1.3) - 2025-07-11

### 💼 Other

- 解决 CodeQL 检查脚本的 undefined 错误 - ([e5cf464]($REPO/commit/e5cf464a1bce56ed09f43bb19f0099dcec80fb57)) - Maverick Tuping Fu

---
## [0.1.2]($REPO/compare/v0.1.1..v0.1.2) - 2025-07-11

### 💼 Other

- 解决发布资产上传 404 错误 - ([8aa1eb9]($REPO/commit/8aa1eb96a7eecb4f43da036fa1c77ba728cb2477)) - Maverick Tuping Fu

---
## [0.1.1]($REPO/compare/v0.1.0..v0.1.1) - 2025-07-11

### 💼 Other

- PR 工作流效率提升 - ([db8c160]($REPO/commit/db8c160e42180b82ca211924797de3f78732e4ed)) - Maverick Tuping Fu
- 解决发布作业 hdiutil 命令找不到的问题 - ([4bc0a43]($REPO/commit/4bc0a433e3873eb6ce454c8fc5c6dbc626ce60f1)) - Maverick Tuping Fu

---
## [0.1.0] - 2025-07-11

### 🚀 Features

- Exclude cliff.toml from cargo-generate templating - ([7df8834]($REPO/commit/7df8834b683bc5b3d13d282fb16a6fcf995ec45a)) - Maverick Tuping Fu
- refactor and add codeql - ([61ddafb]($REPO/commit/61ddafb814aeacd621bd4093efd4528a9254d8e8)) - Maverick Tuping Fu
- add .secrets.baseline for detect-secrets - ([b41f7ff]($REPO/commit/b41f7ffb45f81d8839947260607217f15f54c9f1)) - Maverick Tuping Fu
- 禁用分支保护，允许直接提交到main分支 - ([e662117]($REPO/commit/e6621171cb708ffa3689179f6f5aecc332f0cb5c)) - Maverick Tuping Fu

### 🐛 Bug Fixes

- fix main.rs test mod and cargo.toml license do not pass pre-commit - ([e4c0d68]($REPO/commit/e4c0d681be0c0aa390fb9d8a6afe3e9e8f7199cb)) - Maverick Tuping Fu
- fix main.rs test mod does not pass pre-commit - ([28fa27d]($REPO/commit/28fa27d62d14193340d61107f1a7ed6323c1924b)) - Maverick Tuping Fu
- .pre-commit-config.yaml - ([bccca51]($REPO/commit/bccca519db3d6301573afe6f267e2f40f3523aaa)) - Maverick Tuping Fu
- .pre-commit-config.yaml and workflow issues - ([19cc092]($REPO/commit/19cc092b6b20ed903cc3be283dcd4d721768eb59)) - Maverick Tuping Fu
- .pre-commit-config.yaml and add .secrets.baseline - ([435c819]($REPO/commit/435c819571a075d48099a6763e5b7445533e792f)) - Maverick Tuping Fu
- .pre-commit-config.yaml - 修复 gitleaks 和 detect-secrets 配置问题 - ([20363c2]($REPO/commit/20363c25708a2e91274821fa401613a28ffd0366)) - Maverick Tuping Fu

### 💼 Other

- change world whit rust in main.rs - ([8ddcd31]($REPO/commit/8ddcd31ab2ba7bf6c354aedc478784b0e80ca033)) - Maverick Tuping Fu
- 简化构建系统并优化 nextest 配置 - ([56beec0]($REPO/commit/56beec04b5823ca45c6690490ffae6acdb19507a)) - Maverick Tuping Fu
- 解决 CI/CD 测试失败问题 - ([b68ae2b]($REPO/commit/b68ae2b4ab0c0febf68eb6a9dcbdaa27f6f0946d)) - Maverick Tuping Fu

### 📚 Documentation

- improve README structure - ([3bc2d3c]($REPO/commit/3bc2d3cff0608f464ec9d8c1310ce2ab483173f3)) - Maverick Tuping Fu
- add environment setup section and standardize formatting in README - ([a3382b6]($REPO/commit/a3382b65d32f8e4b35d8e0d8607f9eed85c1722c)) - Maverick Tuping Fu

<!-- generated by git-cliff -->
