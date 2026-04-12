# 🌐 Auto-Deploy Portfolio — GitHub Actions + GitHub Pages

A clean, minimal personal portfolio website that deploys automatically to the web every time you push code. No servers. No configuration. Just write, push, and go live.

**[View Live Site →](https://Abduu47.github.io/my-portfolio)**

---

## Overview

This project is a static portfolio website built with pure HTML and CSS, paired with a GitHub Actions CI/CD pipeline that publishes it to GitHub Pages on every push to `main`. It's designed to be lightweight, fast, and completely free to host — a perfect starting point for developers sharing their work online.

---

## Features

- **Zero-config deployment** — push your code and the site updates automatically
- **No frameworks or dependencies** — pure HTML and CSS, nothing to install
- **Free hosting** — powered entirely by GitHub Pages
- **CI/CD pipeline** — GitHub Actions handles every build and deploy
- **Responsive design** — works on mobile, tablet, and desktop
- **Sections for About, Projects, and Contact** — ready to personalise

---

## Tools Used

| Tool | Purpose |
|---|---|
| HTML5 & CSS3 | Structure and styling of the website |
| GitHub Pages | Free static site hosting |
| GitHub Actions | Automated deployment pipeline (CI/CD) |
| Git | Version control |

---

## Project Structure

```
my-portfolio/
├── .github/
│   └── workflows/
│       └── deploy.yml      # GitHub Actions workflow
├── index.html              # Main webpage
├── style.css               # All styles
└── README.md               # This file
```

---

## How It Works

Every push to the `main` branch triggers the following automated pipeline:

```
git push → GitHub Actions triggered → code checked out
        → site files packaged → deployed to GitHub Pages → live ✓
```

**The workflow in plain English:**

1. You edit your site locally and run `git push`
2. GitHub detects the push and wakes up the Actions workflow
3. A free Linux runner checks out your code
4. The HTML and CSS files are packaged as a Pages artifact
5. The artifact is published to GitHub Pages
6. Your live site reflects the changes — usually within 60 seconds

The full workflow lives in `.github/workflows/deploy.yml`:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches:
      - main

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/configure-pages@v5
      - uses: actions/upload-pages-artifact@v3
        with:
          path: '.'
      - id: deployment
        uses: actions/deploy-pages@v4
```

---

## Getting Started

To run this project locally, clone the repo and open `index.html` directly in your browser — no server needed.

```bash
git clone https://github.com/your-username/my-portfolio.git
cd my-portfolio
open index.html        # Mac
start index.html       # Windows
```

To deploy your own version:

1. Fork or clone this repo
2. Go to **Settings → Pages → Source** and select **GitHub Actions**
3. Push any change to `main`
4. Your site will be live at `https://your-username.github.io/my-portfolio`

---

## Making Updates

```bash
# Edit your files, then:
git add .
git commit -m "describe what you changed"
git push
```

GitHub Actions handles the rest. Check the **Actions** tab in your repo to watch the deployment in real time.

---

## Live Site

**[https://your-username.github.io/my-portfolio](https://your-username.github.io/my-portfolio)**

> Replace `your-username` with your actual GitHub username.

---

## License

This project is open source and available under the [MIT License](LICENSE).

---

*Built with HTML, CSS, and GitHub Actions · Hosted on GitHub Pages*
