📄 README.md（完整说明版）

`markdown

ServerBox Logos 自动切换方案

本仓库提供常见 Linux 发行版的 Logo 文件，并通过 GitHub Actions 自动转换为 PNG 格式，发布到 GitHub Pages。  
在 ServerBox 中可通过统一的 URL 模板自动加载对应发行版的 Logo。

---

🚀 使用方法

在 ServerBox 设置 Logo URL 模板为：

`
https://*.github.io/serverbox-logos/{DIST}-{BRIGHT}.png
`

- {*} 由 自己名称。
- {DIST} 会由 ServerBox 自动替换为当前服务器的发行版名称。
- {BRIGHT} 会由 ServerBox 自动替换为 light 或 dark。

---

🐧 支持的发行版列表

| 发行版名称 | ServerBox {DIST} 值 | 原始文件名示例 | 是否需要映射 |
|------------|-----------------------|----------------|--------------|
| Ubuntu     | ubuntu              | ubuntu.svg / ubuntu.png | 否 |
| Debian     | debian              | debian.svg | 否 |
| Arch Linux | arch                | archlinux.svg / archlinux.png | ✅ 是（需映射为 arch.svg） |
| CentOS     | centos              | centos.svg | 否 |
| Fedora     | fedora              | fedora.svg | 否 |
| openSUSE   | suse                | opensuse.svg | ✅ 是（需映射为 suse.svg） |
| Rocky Linux| rocky               | rockylinux.svg | ✅ 是（需映射为 rocky.svg） |
| Alpine     | alpine              | alpine.svg | 否 |
| Deepin     | deepin              | deepin.svg | 否 |
| Kali Linux | kali                | kali.svg | 否 |
| Armbian    | armbian             | armbian.svg | 否 |
| Synology DMS    | synology             | synology.svg | 否 |

---

⚙️ 自动化流程

- 上传文件：将原始 Logo 文件放入 logos/ 文件夹。  
- GitHub Actions：自动运行脚本，统一命名并转换为 PNG。  
- GitHub Pages：发布到 gh-pages 分支，提供访问地址。  
- ServerBox 使用：通过 {DIST}-{BRIGHT}.png 自动加载对应 Logo。

---

🔧 如何扩展新发行版

1. 上传新发行版的 Logo 文件到 logos/ 文件夹。  
2. 如果文件名和 ServerBox 的 {DIST} 值不一致，在工作流的 Normalize filenames 步骤中添加映射规则。  
3. 更新 README 的支持发行版表格。  
4. 提交到 main 分支，等待 Actions 自动运行。

---

📜 版权声明

- 所有 Logo 的版权归各发行版官方所有。  
- 本仓库仅用于技术演示和 ServerBox 使用。  
- 脚本和工作流配置采用 MIT License。
`

---

📄 README-QuickStart.md（快速开始版）

`markdown

快速开始

只需 4 步，就能在 ServerBox 上使用自动切换的发行版 Logo：

---

1. Fork 仓库
- 打开本仓库页面，点击右上角 Fork  
- 在你的 GitHub 账号下创建副本

---

2. 上传 Logo 文件
- 在仓库主页点击 Add file → Upload files  
- 将各发行版的 SVG/PNG 文件上传到 logos/ 文件夹  
- 确保文件名和 ServerBox 的 {DIST} 值一致（如 ubuntu.svg → ubuntu）

---

3. 自动生成 PNG
- GitHub Actions 会自动运行工作流：  
  - 将原始 Logo 转换为 PNG  
  - 按照 {DIST}-{BRIGHT}.png 命名（例如 ubuntu-dark.png、debian-light.png）  
  - 发布到 gh-pages 分支并启用 GitHub Pages

---

4. 在 ServerBox 使用
- 在 ServerBox 设置 Logo URL 模板为：

  `
  https://*.github.io/serverbox-logos/{DIST}-{BRIGHT}.png
  `

- 示例效果：  
  - Ubuntu 深色主题 → ubuntu-dark.png  
  - Debian 浅色主题 → debian-light.png  
  - Arch 深色主题 → arch-dark.png
`

---

📄 README-FAQ.md（常见问题版）

`markdown

常见问题 (FAQ)

---

1. 为什么 Logo 在 ServerBox 上不显示？
- 可能原因：文件名和 ServerBox 的 {DIST} 值不匹配。  
- 解决方法：检查 gh-pages 分支是否存在对应的文件，例如 arch-dark.png。如果原始文件是 archlinux.svg，需要在工作流里映射为 arch.svg。

---

2. GitHub Actions 报错 “exit code 128”
- 可能原因：工作流没有权限推送到 gh-pages 分支，或者仓库为空。  
- 解决方法：  
  - 在工作流文件顶部添加：
    `yaml
    permissions:
      contents: write
    `
  - 确认仓库至少有一个提交（例如 README.md）。

---

3. GitHub Pages 部署后访问不到文件
- 可能原因：publish_dir 设置错误，或者 Pages 配置未启用。  
- 解决方法：  
  - 确认工作流的 publish_dir 指向 ./png。  
  - 在仓库 Settings → Pages 中启用 gh-pages 分支作为部署源。

---

4. 为什么需要映射表？
- 原因：ServerBox 使用简化的 {DIST} 值，而官方 Logo 文件名可能不同。  
- 示例：  
  - archlinux.svg → arch.svg  
  - opensuse.svg → suse.svg  
  - rockylinux.svg → rocky.svg

---

5. 如何添加新发行版？
1. 上传新发行版的 Logo 文件到 logos/ 文件夹。  
2. 如果文件名和 {DIST} 不一致，在工作流的 Normalize filenames 步骤中添加映射规则。  
3. 更新 README 的支持发行版表格。  
4. 提交到 main 分支，等待 Actions 自动运行。

---

6. GitHub Pages 更新延迟
- 说明：GitHub Pages 部署后可能需要几分钟才能生效。  
- 解决方法：稍等片刻，或清理浏览器缓存后再访问。
`

---

--
