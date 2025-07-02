# 🚀 Rust 项目模板

一个简洁高效的 Rust 项目模板，帮助你快速开始新项目。

## 🛠️ 使用方法

1. **生成项目**
   ```bash
   cargo generate futuping/template
   ```
2. **安装 pre-commit 钩子**
   ```bash
   pre-commit install
   ```
3. **在 GitHub 上创建新仓库**

4. **在 `cliff.toml` 文件中，将 postprocessors 的 `replace` 字段替换为你的新仓库地址**

   ```toml
   postprocessors = [
       { pattern = '\$REPO', replace = "https://github.com/{new-repo}" },
   ]
   ```

5. **在 `Cargo.toml` 中，将 `name` 和 `description` 等字段替换为你的项目实际信息。**

6. **初始化提交**
   ```bash
   git commit -am "chore: init repo"
   ```
7. **推送代码到远程仓库**
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
