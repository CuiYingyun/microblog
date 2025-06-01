# 🌱 Minimalist Microblog

A clean, distraction-free microblog powered by GitHub Issues and Hugo. Easily write, tag, and publish posts with a beautiful, mobile-friendly interface.

**Demo:** [Live Site](https://www.cuiyingyun.com/)


## ✨ Features

- **Microblog Style:** Full content display, no click-through required
- **GitHub Issues as CMS:** Write and manage posts directly from GitHub
- **Mobile Friendly:** Responsive design for all devices
- **Tag Support:** Organize content with GitHub labels
- **Dark Mode:** Automatic and manual theme switching
- **No Database Required:** All content stored in GitHub Issues
- **Minimalist Design:** Pure black & white, subtle borders, right-aligned metadata
- **Congo Theme Powered:** Built on the highly customizable [Congo theme](https://jpanther.github.io/congo/) for Hugo
- **Multilingual Support:** Theme supports 30+ languages out of the box
- **Modern Hugo Features:** Utilizes latest Hugo capabilities for optimal performance


## 🚀 Quick Start

> **📖 Based on Two Excellent Projects**  
> This microblog combines the power of two outstanding open-source projects:
> - **[issues-blog](https://github.com/imfing/issues-blog)** - GitHub Issues as CMS integration
> - **[Congo Theme](https://jpanther.github.io/congo/)** - Modern, highly customizable Hugo theme
> 
> For initial setup and deployment, please follow the comprehensive [Quick Start Guide](https://imfing.github.io/issues-blog/posts/quick-start/) from the original issues-blog project.

### Initial Setup (Follow Original Guide)

1. **Create Repository:** Use [this template](https://github.com/imfing/issues-blog) → "Use this template" → "Create a new repository"
2. **Edit Configuration:** 
   - Modify `go.mod` (first line) to your `<user>/<repo>`
   - Update `config/_default/config.toml` → set `baseURL` to your domain
3. **Create Content:** Add issues to your repository using Markdown
4. **Deploy:** Close issues to trigger GitHub Actions → Enable GitHub Pages

For detailed instructions, see the [original quick start guide](https://imfing.github.io/issues-blog/posts/quick-start/).

### Local Development & Customization

Once you have the basic setup working, use these instructions for local development and customization:

#### 1. Environment Setup

- **Install Hugo (extended version required):**
  ```bash
  brew install hugo
  ```
  To install a specific version (e.g., 0.145.0):
  ```bash
  brew uninstall hugo
  brew install https://raw.githubusercontent.com/Homebrew/homebrew-core/5e5c3e1c33c8cef9e7d3cf3cfec74027e0698ece/Formula/h/hugo.rb
  ```
- **Install Deno (for GitHub Issues integration):**
  ```bash
  brew install deno
  ```

#### 2. Local Development

##### Method 1: Test Data (Recommended)

1. Start the Hugo development server:
   ```bash
   hugo server -D
   ```
2. Open your browser and visit the local server address (usually http://localhost:1313/).
3. Edit files in the `content/posts/` directory. Hugo will auto-refresh the site.

##### Method 2: Real Data from GitHub Issues

1. Set environment variables:
   ```bash
   export GITHUB_TOKEN="your-github-token"
   export GITHUB_REPOSITORY="owner/repo"
   ```
2. Run:
   ```bash
   make dev
   ```
   This fetches content from GitHub Issues and starts the dev server.


## 🛠️ Customization & Debugging

### Congo Theme Configuration

This project uses the [Congo theme](https://jpanther.github.io/congo/) which provides extensive customization options:

- **Theme Parameters:** Extensive configuration via `config/_default/params.toml`
- **Multi-language Support:** 30+ languages supported out of the box
- **Color Schemes:** Built-in color schemes (congo, avocado, cherry, fire, ocean, sapphire, slate)
- **Layout Options:** Multiple homepage layouts (page, profile, custom)
- **Advanced Features:** Analytics integration, SEO optimization, social sharing

📖 **For complete theme configuration options, see:** [Congo Documentation](https://jpanther.github.io/congo/docs/configuration)

### Template Editing
- Edit files in `layouts/` for instant changes.
- Key files:
  - `layouts/index.html` – Home page
  - `layouts/posts/list.html` – Post list
  - `layouts/partials/extend-head.html` – Custom head (appearance switcher, etc.)

### Styling
- Edit `assets/css/custom.css` for custom styles.
- Use browser dev tools (F12) for live CSS tweaks, then copy changes to `custom.css`.

**Common adjustments:**
- Top margin: `.microblog-container` `padding-top`
- Post spacing: `.microblog-post` `margin-bottom`
- Border: `.microblog-post` `border`
- Padding: `.microblog-post` `padding`
- Date position: `.microblog-post .post-meta` `margin-top`/`padding-top`

### Configuration
- **Site title:** `config/_default/languages.en.toml` (`title`)
- **Navigation:** `config/_default/menus.en.toml`
- **Parameters:** `config/_default/params.toml`
- **Congo Theme Settings:** See [Congo configuration docs](https://jpanther.github.io/congo/docs/configuration) for all available options

### Content
- Add Markdown files to `content/posts/`
- Test text, code, images, etc.
- **About page:** Edit `content/about.md`

### View Output
```bash
hugo --gc --minify
ls -la public/
```


## 📁 Project Structure

```
.
├── layouts/              # Templates
│   ├── index.html       # Home page
│   ├── posts/
│   │   └── list.html    # Post list
│   └── partials/
│       └── extend-head.html  # Custom head (CSS, appearance switcher)
├── assets/
│   └── css/
│       └── custom.css   # Custom styles
├── content/
│   ├── posts/           # Posts
│   └── about.md         # About page
├── config/
│   └── _default/
│       ├── config.toml  # Main config
│       ├── languages.en.toml  # Language & title
│       ├── menus.en.toml      # Navigation
│       └── params.toml        # Theme params
└── scripts/
    └── main.ts          # GitHub Issues sync
```


## 🌍 Pages

- **Home** (`/`) – All microblog posts
- **Posts** (`/posts/`) – Post list
- **Tags** (`/tags/`) – All tags
- **About** (`/about/`) – About page


## 🎨 Appearance Switcher

- Light/dark mode toggle in the top navigation bar
- Code in `layouts/partials/extend-head.html`
- Features:
  - Auto-detects and adds to navigation
  - Supports light/dark mode
  - Uses localStorage for user preference
  - Responsive icon (sun/moon)


## 🧩 Common Issues

- **Hugo Version Errors:**
  ```bash
  hugo version
  ```
- **Styles Not Applied:**
  - Clear browser cache
  - Restart Hugo server
  - Check `layouts/partials/extend-head.html` for CSS
- **Content Not Displayed:**
  - Ensure posts are in `content/posts/`
  - Check frontmatter
  - Run `hugo server -D` for drafts
- **Appearance Switcher Not Visible:**
  - Check browser console for JS errors
  - Ensure `layouts/partials/extend-head.html` exists
  - Clear browser cache and refresh


## 🚢 Deployment Checklist

**IMPORTANT:**
> **Before deploying, always edit `config/_default/config.toml` and set `baseURL` to your own domain.**
> If you skip this, domain mapping will not work correctly, even if you set up DNS or custom domains.

**For Custom Domain Deployment:**
> **If using a custom domain, you MUST update the CNAME configuration in `.github/workflows/build.yml`:**
> ```yaml
> - name: Add CNAME for custom domain
>   run: echo 'your-domain.com' > public/CNAME # Replace with your domain
> ```
> Otherwise, every GitHub Actions run will reset your custom domain settings and cause deployment failures.

**Remove test files before deploying:**
```bash
rm content/posts/test-*.md
```
Or use:
```bash
make clean
```
