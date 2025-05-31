# 本地调试指南

## 环境准备

1. 安装 Hugo (需要 extended 版本)：
   ```bash
   brew install hugo
   ```
   
   如需安装特定版本（如 0.145.0）：
   ```bash
   brew uninstall hugo
   brew install https://raw.githubusercontent.com/Homebrew/homebrew-core/5e5c3e1c33c8cef9e7d3cf3cfec74027e0698ece/Formula/h/hugo.rb
   ```

2. 安装 Deno (用于从 GitHub Issues 获取内容)：
   ```bash
   brew install deno
   ```

## 本地调试步骤

### 方法一：使用测试数据调试（推荐）

1. 直接运行 Hugo 开发服务器：
   ```bash
   hugo server -D
   ```

2. 访问 http://localhost:1313/microblog/ 查看效果

3. 修改 `content/posts/` 目录下的测试文件，Hugo 会自动刷新

### 方法二：从 GitHub Issues 获取真实数据

1. 设置环境变量：
   ```bash
   export GITHUB_TOKEN="your-github-token"
   export GITHUB_REPOSITORY="owner/repo"
   ```

2. 运行 make 命令：
   ```bash
   make dev
   ```

   这会先从 GitHub Issues 获取内容，然后启动开发服务器

## 调试技巧

### 1. 模板调试
- 编辑 `layouts/` 目录下的文件，保存后会自动刷新
- 主要模板文件：
  - `layouts/index.html` - 首页模板
  - `layouts/posts/list.html` - 文章列表页模板
  - `layouts/partials/extend-head.html` - 自定义头部内容（包含显示模式切换功能）

### 2. 样式调试
- 编辑 `assets/css/custom.css`，保存后会自动刷新
- 使用浏览器开发者工具（F12）进行实时调试：
  1. 在 Elements/元素 面板中选择要调整的元素
  2. 在 Styles/样式 面板中实时修改 CSS 值
  3. 满意后将修改写入 `custom.css` 文件

#### 常见样式调整：
- **内容区域上边距**：修改 `.microblog-container` 的 `padding-top`
- **微博间距**：修改 `.microblog-post` 的 `margin-bottom`
- **边框样式**：修改 `.microblog-post` 的 `border`
- **内边距**：修改 `.microblog-post` 的 `padding`
- **日期位置**：修改 `.microblog-post .post-meta` 的 `margin-top` 和 `padding-top`

### 3. 配置调试
- **站点标题**：在 `config/_default/languages.en.toml` 中修改 `title`
- **导航菜单**：在 `config/_default/menus.en.toml` 中配置菜单项
  - Posts - 文章列表
  - Tags - 标签页面
  - Cui.Yingyun - 个人信息页面
- **站点参数**：在 `config/_default/params.toml` 中调整各种参数
  - `showTitle` - 是否显示站点标题（当前设为 false）
  - `showCopyright` - 是否显示版权信息（当前设为 false）
  - `showAppearanceSwitcher` - 是否在footer显示模式切换（当前设为 false，已移至header）

### 4. 内容调试
- 创建测试 Markdown 文件在 `content/posts/` 目录
- 测试不同类型的内容：文本、代码块、引用、图片等
- **About页面**：编辑 `content/about.md` 文件来修改个人信息

### 5. 查看生成的文件
```bash
hugo --gc --minify
ls -la public/
```

## 文件结构说明

```
.
├── layouts/              # 模板文件
│   ├── index.html       # 首页模板
│   ├── posts/
│   │   └── list.html    # 文章列表模板
│   └── partials/
│       └── extend-head.html  # 引入自定义CSS和显示模式切换功能
├── assets/
│   └── css/
│       └── custom.css   # 自定义样式
├── content/
│   ├── posts/           # 文章内容
│   └── about.md         # 个人信息页面
├── config/
│   └── _default/        # 配置文件
│       ├── config.toml  # 基础配置
│       ├── languages.en.toml  # 语言和站点标题配置
│       ├── menus.en.toml      # 导航菜单配置
│       └── params.toml        # 主题参数配置
└── scripts/
    └── main.ts          # GitHub Issues 同步脚本
```

## 页面说明

1. **首页** (`/`) - 显示所有微博内容
2. **Posts页面** (`/posts/`) - 文章列表页，与首页相同
3. **Tags页面** (`/tags/`) - 显示所有标签
4. **About页面** (`/about/`) - 个人信息页面，显示 Markdown 内容

## 显示模式切换功能

显示模式切换按钮已通过 JavaScript 自动添加到顶部导航栏的 Tags 按钮旁边。相关代码在 `layouts/partials/extend-head.html` 中。

功能特点：
- 自动检测并添加到导航菜单末尾
- 支持亮色/暗色模式切换
- 使用 localStorage 保存用户偏好
- 响应式图标（太阳/月亮）

## 常见问题

### 1. Hugo 版本错误
如果遇到模板错误，可能是 Hugo 版本问题。检查版本：
```bash
hugo version
```

### 2. 样式没有生效
- 清除浏览器缓存
- 重启 Hugo 服务器
- 检查 `layouts/partials/extend-head.html` 是否正确引入 CSS

### 3. 内容不显示
- 确认文章在 `content/posts/` 目录下
- 检查文章的 frontmatter 格式是否正确
- 运行 `hugo server -D` 以显示草稿

### 4. 显示模式切换按钮不显示
- 检查浏览器控制台是否有 JavaScript 错误
- 确认 `layouts/partials/extend-head.html` 文件存在
- 尝试清除浏览器缓存并刷新页面

## 部署前清理

部署前删除测试文件：
```bash
rm content/posts/test-*.md
```

或使用 make 命令：
```bash
make clean
``` 