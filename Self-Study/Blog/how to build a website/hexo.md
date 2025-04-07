Hexo 是一个快速、简洁且功能强大的静态博客框架，适合搭建个人博客或网站。以下是如何使用 Hexo 的基本流程：

### 1. 安装 Node.js 和 Git
首先，你需要确保已经安装了 [Node.js](https://nodejs.org/) 和 [Git](https://git-scm.com/)
### 2. 安装 Hexo
打开终端/命令提示符，运行以下命令安装 Hexo：
```bash
npm install -g hexo-cli
```

### 3. 初始化博客
选择一个文件夹作为你的网站目录，然后在该文件夹中初始化一个 Hexo 项目：
```bash
hexo init blog
cd blog
npm install
```
上面的命令会创建一个名为 `blog` 的新目录，里面包含 Hexo 的文件结构。

### 4. 生成静态文件
Hexo 生成的博客是静态文件。你可以通过以下命令生成这些文件：
```bash
hexo generate
```
这个命令会在 `public/` 目录下生成所有的静态文件。

### 5. 本地预览
在本地启动服务器以预览你的博客：
```bash
hexo server
```
然后你可以在浏览器中访问 `http://localhost:4000` 查看你的博客。

### 6. 部署博客
Hexo 支持多种部署方式，如 GitHub Pages、Vercel 等。最常见的是部署到 GitHub Pages。你可以通过修改 `_config.yml` 文件来配置部署选项。

#### 配置 GitHub Pages：
1. 修改 `config.yml` 文件中的 `deploy` 部分，填入你的 GitHub 仓库地址：
```yaml
deploy:
  type: git
  repo: https://github.com/yourusername/yourrepo.git
  branch: gh-pages
```
2. 安装 Hexo 的 git 部署插件：
```bash
npm install hexo-deployer-git --save
```
3. 运行以下命令将博客部署到 GitHub Pages：
```bash
hexo deploy
```

### 7. 自定义主题和插件
- **主题**：Hexo 有许多开源主题，你可以在 [Hexo Themes](https://hexo.io/themes/) 上找到。安装主题的方法通常是将主题文件夹下载到 `themes` 目录下，然后修改 `_config.yml` 文件的 `theme` 字段。
- **插件**：Hexo 有许多插件用于扩展功能，比如 SEO 优化、RSS 订阅等。可以在 [Hexo 插件文档](https://hexo.io/plugins/) 中找到更多信息。

### 常用命令：
- `hexo new "post name"`：创建新文章。
- `hexo generate` 或 `hexo g`：生成静态文件。
- `hexo server` 或 `hexo s`：启动本地服务器预览。
- `hexo deploy` 或 `hexo d`：部署博客到远程。

