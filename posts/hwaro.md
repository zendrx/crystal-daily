# Hwaro: A Fresh Static Site Generator in Crystal

Hwaro (화로) is a lightweight and fast static site generator written in Crystal. The name means Furnace in Korean — feed in your content, and it crafts a complete website.

Version 0.13.0 just dropped on April 26, 2026. And there was a commit just 7 hours ago (April 29). This project is actively maintained.

What Hwaro offers:

- Markdown with TOML, YAML, or JSON front matter
- Jinja2-compatible templates (via Crinja)
- Parallel builds and incremental caching
- Built-in dev server with live reload
- Auto-generated sitemap, RSS/Atom feeds, robots.txt
- OpenGraph, Twitter Cards, and JSON-LD structured data
- Image processing (resize, responsive images, blur-up placeholders)
- PWA support with manifest and service worker
- Import from WordPress, Jekyll, or Hugo
- Deployment targets for Netlify, Vercel, Cloudflare Pages, GitHub Pages, GitLab CI, and now Codeberg Pages (added today)

Installation:

Homebrew: brew tap hahwul/hwaro && brew install hwaro

From source: git clone https://github.com/hahwul/hwaro.git, then shards install && shards build --release

Hwaro has 24 stars, 3 forks, and 38 releases. It's young but moving fast.

If you're looking for a Hugo alternative written in Crystal, this is worth a test drive.

Find it on GitHub: hahwul/hwaro
