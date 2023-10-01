+++
title = 'HUGO First Steps'
date = 2023-10-01T00:28:15+01:00
ReadingTime = 10
Truncated = true
Content = 'HUGO'
draft = false
+++

## HUGO

### The world’s fastest framework for building websites

Hugo is one of the most popular open-source static site generators. With its amazing speed and flexibility, Hugo makes building websites fun again.

### Installing on Windows

#### Assumptions

We’ll call your website example.com for the purpose of this tutorial.

- You will use C:\Hugo\Sites as the starting point for your site.
- You will use C:\Hugo\bin to store executable files.
- Setup Your Directories

You’ll need a place to store the Hugo executable, your content (the files that you build), and the generated files (the HTML that Hugo builds for you).

- Open Windows Explorer.
- Create a new folder: C:\Hugo (assuming you want Hugo on your C drive – it can go anywhere.)
- Create a subfolder in the Hugo folder: C:\Hugo\bin.
- Create another subfolder in Hugo: C:\Hugo\Sites.
  
##### Technical users

- Download the latest zipped Hugo executable from the Hugo Releases page.

- Extract all contents to your "C:\Hugo\bin" folder.

- The hugo executable will be named as hugo_hugo-version_platform_arch.exe. Rename that executable to hugo.exe for ease of use.

- In CMD or your preferred CLI, add the hugo.exe executable to your PATH by navigating to C:\Hugo\bin (or the location of your hugo.exe file) and use the command set PATH=%PATH%;C:\Hugo\bin. If the hugo command does not work after a reboot, you may have to run the command prompt as administrator.

```goat
      .               .                .               .--- 1          .-- 1     / 1
     / \              |                |           .---+            .-+         +
    /   \         .---+---.         .--+--.        |   '--- 2      |   '-- 2   / \ 2
   +     +        |       |        |       |    ---+            ---+          +
  / \   / \     .-+-.   .-+-.     .+.     .+.      |   .--- 3      |   .-- 3   \ / 3
 /   \ /   \    |   |   |   |    |   |   |   |     '---+            '-+         +
 1   2 3   4    1   2   3   4    1   2   3   4         '--- 4          '-- 4     \ 4

```

## Hosting

<https://gohugo.io/hosting-and-deployment/hosting-on-github/>

```yaml
# Sample workflow for building and deploying a Hugo site to GitHub Pages
name: Deploy Hugo site to Pages

on:
  # Runs on pushes targeting the default branch
  push:
    branches:
      - main

  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

# Sets permissions of the GITHUB_TOKEN to allow deployment to GitHub Pages
permissions:
  contents: read
  pages: write
  id-token: write

# Allow only one concurrent deployment, skipping runs queued between the run in-progress and latest queued.
# However, do NOT cancel in-progress runs as we want to allow these production deployments to complete.
concurrency:
  group: "pages"
  cancel-in-progress: false

# Default to bash
defaults:
  run:
    shell: bash

jobs:
  # Build job
  build:
    runs-on: ubuntu-latest
    env:
      HUGO_VERSION: 0.115.4
    steps:
      - name: Install Hugo CLI
        run: |
          wget -O ${{ runner.temp }}/hugo.deb https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_linux-amd64.deb \
          && sudo dpkg -i ${{ runner.temp }}/hugo.deb          
      - name: Install Dart Sass
        run: sudo snap install dart-sass
      - name: Checkout
        uses: actions/checkout@v3
        with:
          submodules: recursive
          fetch-depth: 0
      - name: Setup Pages
        id: pages
        uses: actions/configure-pages@v3
      - name: Install Node.js dependencies
        run: "[[ -f package-lock.json || -f npm-shrinkwrap.json ]] && npm ci || true"
      - name: Build with Hugo
        env:
          # For maximum backward compatibility with Hugo modules
          HUGO_ENVIRONMENT: production
          HUGO_ENV: production
        run: |
          hugo \
            --gc \
            --minify \
            --baseURL "${{ steps.pages.outputs.base_url }}/"          
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v1
        with:
          path: ./public

  # Deployment job
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages

```

## Test

Setup hugo.toml with ```canonifyURLs = true``` for The / baseURL '<https://joaosgomes.github.io/gohugo/>'
