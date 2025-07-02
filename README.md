# 🚀 Rust 项目模板

一个简洁高效的 Rust 项目模板，帮助你快速开始新项目。


## ⚙️ 环境设置

1. **安装 Rust。**
   ```bash
   curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
   ```
2. **安装 VSCode 插件。**
   推荐安装以下插件：

   | 插件名                | 功能描述           |
   |----------------------|--------------------|
   | crates               | Rust 包管理        |
   | Even Better TOML     | TOML 文件支持      |
   | Better Comments      | 优化注释显示       |
   | Error Lens           | 错误提示优化       |
   | GitLens              | Git 增强           |
   | Github Copilot       | 代码提示           |
   | indent-rainbow       | 缩进显示优化       |
   | Prettier - Code formatter | 代码格式化   |
   | REST client          | REST API 调试      |
   | rust-analyzer        | Rust 语言支持      |
   | Rust Test lens       | Rust 测试支持      |
   | Rust Test Explorer   | Rust 测试概览      |
   | TODO Highlight       | TODO 高亮          |
   | vscode-icons         | 图标优化           |
   | YAML                 | YAML 文件支持      |
3. **安装 cargo generate。**
   cargo generate 是一个用于生成项目模板的工具。它可以使用已有的 github repo 作为模版生成新的项目。
   ```bash
   cargo install cargo-generate
   ```
   新项目会使用 `futuping/template` 模版生成基本的代码：
   ```bash
   cargo generate futuping/template
   ```
4. **安装 pre-commit。**
   pre-commit 是一个代码检查工具，可以在提交代码前进行代码检查。
   ```bash
   pip install pre-commit
   ```
   >安装成功后在当前项目根目录下运行 `pre-commit install` 。
5. **安装 Cargo deny。**
   Cargo deny 是一个 Cargo 插件，可以用于检查依赖的安全性。
   ```bash
   cargo install cargo-deny --locked
   ```
6. **安装 typos。**
   typos 是一个拼写检查工具。
   ```bash
   cargo install typos-cli
   ```
7. **安装 git cliff。**
   git cliff 是一个生成 changelog 的工具。
   ```bash
   cargo install git-cliff
   ```
8. **安装 cargo nextest。**
   cargo nextest 是一个 Rust 增强测试工具。
   ```bash
   cargo install cargo-nextest --locked
   ```


## 🛠️ 使用方法

1. **生成项目。**
   ```bash
   cargo generate futuping/template
   ```
2. **安装 pre-commit 钩子。**
   ```bash
   pre-commit install
   ```
3. **在 GitHub 上创建新仓库。**

4. **在 `cliff.toml` 文件中，将 postprocessors 的 `replace` 字段替换为你的新仓库地址。**

   ```toml
   postprocessors = [
       { pattern = '\$REPO', replace = "https://github.com/{new-repo}" },
   ]
   ```

5. **在 `Cargo.toml` 中，将 `name` 和 `description` 等字段替换为你的项目实际信息。**

6. **初始化提交。**
   ```bash
   git commit -am "chore: init repo"
   ```
7. **推送代码到远程仓库。**
   ```bash
   git remote add origin https://github.com/{new-repo}.git
   git branch -M main
   git push -u origin main
   ```
> 📢 注意事项：
>
> - 请根据实际情况替换 `{new-repo}` 为你的仓库名。
> - 并设置本地 git 的默认分支为 `main`：
>   ```bash
>   git config --global init.defaultBranch main
>   ```
