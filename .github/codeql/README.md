# 🔍 CodeQL 安全分析配置

## 概述

GitHub CodeQL 是一个强大的静态代码分析引擎，专门用于检测代码中的安全漏洞和质量问题。本项目已配置完整的 CodeQL 分析流程，为 Rust 代码提供全面的安全保障。

## 🎯 分析能力

### Rust 专用检测
- **内存安全**: 检测潜在的内存安全问题
- **并发安全**: 发现数据竞争、死锁等并发问题
- **Unsafe 代码审计**: 分析 unsafe 代码块的安全性
- **整数溢出**: 检测数值计算中的溢出风险

### 通用安全检测
- **注入攻击**: SQL 注入、命令注入等
- **路径遍历**: 文件系统访问安全问题
- **加密问题**: 弱密码算法、密钥管理问题
- **输入验证**: 用户输入处理的安全问题

## 🔧 配置文件

### `codeql-config.yml`
```yaml
name: "CodeQL Security Analysis for Rust"

queries:
  - uses: security-and-quality    # 安全和质量查询
  - uses: security-extended       # 扩展安全查询

paths-ignore:
  - 'target/**'                   # 构建产物
  - 'tests/fixtures/**'           # 测试数据
  
paths:
  - 'src/**'                      # 源代码
  - 'examples/**'                 # 示例代码
  - 'tests/**'                    # 测试代码

packs:
  - codeql/rust-queries           # Rust 查询包
```

## 🚀 运行方式

### 自动触发
- **推送到 main**: 每次推送主分支时运行
- **Pull Request**: 每个 PR 都会触发安全扫描
- **定期扫描**: 每周日自动运行完整扫描

### 手动触发
在 GitHub Actions 页面可以手动触发 "CodeQL 安全分析" 工作流。

## 📊 查看结果

### GitHub Security 页面
1. 进入仓库的 **Security** 标签
2. 选择 **Code scanning alerts**
3. 查看详细的安全分析报告

### 分析报告包含
- **漏洞严重程度**: Critical, High, Medium, Low
- **详细描述**: 问题的具体说明和影响
- **修复建议**: 具体的代码修改建议
- **代码位置**: 精确到行的问题定位

## ⚙️ 自定义配置

### 添加自定义查询
如需添加项目特定的安全检查，可以在 `codeql-config.yml` 中添加：

```yaml
queries:
  - uses: security-and-quality
  - uses: ./custom-queries        # 自定义查询目录
```

### 调整扫描范围
修改 `paths` 和 `paths-ignore` 来调整扫描范围：

```yaml
paths:
  - 'src/**'
  - 'my-custom-dir/**'            # 添加自定义目录

paths-ignore:
  - 'legacy-code/**'              # 忽略遗留代码
```

## 🛡️ 安全策略

### 阻止合并有安全问题的 PR
建议在 GitHub 设置中启用：
1. **Settings** → **Branches**
2. 对 `main` 分支启用保护规则
3. 选择 **Require status checks**
4. 添加 "CodeQL 安全分析" 检查

### 通知配置
在 **Settings** → **Security & analysis** 中可以配置：
- 安全告警的邮件通知
- 依赖漏洞警报
- Secret scanning 告警

## 📈 持续改进

### 定期审查
- 每月审查安全分析结果
- 更新查询规则和配置
- 根据项目需求调整扫描范围

### 集成开发流程
- 在 pre-commit 中添加基础安全检查
- 使用 IDE 插件进行实时安全提示
- 定期进行安全培训和代码审查

## 🔗 相关资源

- [GitHub CodeQL 文档](https://docs.github.com/en/code-security/code-scanning)
- [CodeQL for Rust](https://codeql.github.com/docs/codeql-language-guides/codeql-for-rust/)
- [Security Best Practices](https://docs.github.com/en/code-security)

---

> 💡 **提示**: CodeQL 分析是项目安全体系的重要组成部分，建议与其他安全工具（如 gitleaks、cargo audit 等）结合使用，构建多层次的安全防护。 