---
authors:
  - Matt2ology
categories:
  - blog
  - how-to
date: 2025-01-11T23:55:35-08:00
draft: false
notes: blog
tags:
title: "Blog - From Notes to Website: Automating Hugo with GitHub Pages and Obsidian"
---

## From Notes to Website: Automating Hugo with GitHub Pages and Obsidian

For this "how-to" I've tried to write the instructions as agnostic as I can (i.e. the steps can be followed regardless of one's operating system); however, before preceding note, at the time of writing, that I am primarily developing in a windows environment.

To set up and automate deployment for a static website using [Hugo](https://gohugo.io/), with [Obsidian](https://obsidian.md/) notes as the content source management and [GitHub Pages](https://pages.github.com/) as the deployment target.

Using Obsidian to manage markdown files for a Hugo-based static site deployed on 
GitHub Pages offers several benefits, including efficient local content management, easy 
linking between notes, and full compatibility with markdown. Obsidian’s organizational 
features, such as tags, backlinks, and folder structures, help structure content for Hugo, 
making it easier to manage large sites. Additionally, Obsidian works offline and across 
platforms, allowing flexibility in content creation. It also integrates well with Git for version 
control, enabling smooth collaboration and history tracking. The approach promotes a 
clear separation of concerns by decoupling content creation (managed in Obsidian) from 
the site generation and deployment process (handled by Hugo and GitHub Pages), 
allowing each tool to focus on its strengths. This separation enhances organization, 
scalability, and maintainability for the static site.

If this sounds beneficial to you or your workflow you can follow these steps:

### Prerequisites

In addition to the [prerequisites describe on Hugo's own site](https://gohugo.io/installation/windows/) you'd also need to install [Obsidian](https://obsidian.md/download).

### 1. Repository Structure

1. **Hugo Framework/GitHub Pages Repository**: use [GitHub Pages](https://pages.github.com/) user repository (`username.github.io`) to deploy the generated static site.
2. **Content Submodule**: use [Obsidian notes](https://obsidian.md/) for managing content (`obsidian-notes-repo`).
   - Submodule: a separate repository containing Markdown files for your notes.
3. **Theme Submodule:** there are many [Hugo themes](https://themes.gohugo.io/) to select from take your pick.
    - I will be using Hugo theme "[Stack](https://github.com/CaiJimmy/hugo-theme-stack)" by [Jimmy Cai](https://jimmycai.com/)

### 2. Initial Setup

1. **Content Repository**: Set up an Obsidian vault (i.e. a folder on your local file system where Obsidian stores your notes) and initialize a Git repository there.

   ```bash
   git init obsidian-notes-repo
   ```

2. **Public Repository**: [Create the `username.github.io` repository on GitHub](https://pages.github.com/).

#### Add Submodules

Using [PowerShell](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7.4) (on Windows) or Bash (on Linux) within your **user** site GitHub Pages repository (i.e. your `username.github.io`). Also see the [Types of GitHub Pages sites](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages#types-of-github-pages-sites).

1. **Add Obsidian Notes Submodule:**
   ```bash
   git submodule add https://github.com/username/obsidian-notes-repo content
   ```
2. **Add a theme:** I'll be using [Jimmy Cai](https://jimmycai.com/)'s [Hugo Stack theme](https://github.com/CaiJimmy/hugo-theme-stack)
   ```bash
   git submodule add https://github.com/CaiJimmy/hugo-theme-stack/ themes/hugo-theme-stack
   ```

#### Checkpoint - Verify Directory Structure

Following the steps listed so far should result in the following directory structure

```plaintext
C:.
\---projects
    +---username.github.io   <- GitHub Repository
    |   +---content          <- Submodule in GitHub Repository
    |   |   +---.obsidian
    |   \---theme
    +---obsidian-notes-repo  <- GitHub Repository
```

#### Create Hugo project skeleton

[Hugo directory structure](https://gohugo.io/getting-started/directory-structure/)

Run the following command within your GitHub Page user repository (i.e. `username.github.io`)

```bash
hugo new site . --format yaml --force
```

With the command I've [configure Hugo](https://gohugo.io/getting-started/configuration/) to use [YAML over the default TOML format](https://www.barenakedcoder.com/blog/2020/03/config-files-ini-xml-json-yaml-toml/) (i.e. `hugo.yaml`) for that I, personally, find it easier to work with as a configuration file.

To have Hugo configured with the default `hugo.toml` file run the same command without `--format yaml`, so that it's just the following: `hugo new site . --force`

> Without `--force` you'll get the following prompt:
>
> > Error: C:\Users\username\projects\hugo-site already exists and is not empty. See --force.
> 
> This is because the directory is already populated with a `content` folder and a `themes` folder.

#### Set up `.gitmodules`

```plaintext
[submodule "content"]
    path = content
    url = https://github.com/username/obsidian-notes-repo
[submodule "themes/hugo-theme-stack"]
	path = themes/hugo-theme-stack
	url = https://github.com/CaiJimmy/hugo-theme-stack/
```

Note if you're not using [Jimmy Cai](https://jimmycai.com/)'s [Hugo Stack theme](https://github.com/CaiJimmy/hugo-theme-stack) your `themes/` submodule will read differently than what I have listed

### 3. Configure GitHub Actions

Hosting on GitHub Pages with continuous deployment is as easy as following the steps found here: <https://gohugo.io/hosting-and-deployment/hosting-on-github/>

The downside of using their prescribed [.github/workflows/hugo.yaml](https://gohugo.io/hosting-and-deployment/hosting-on-github/) is that you'd have to manually pull changes from the `content` (`obsidian-notes-repo`) submodule and update the submodule reference in the main `username.github.io` repository.

I will provide my GitHub Action workflow to automate:

1. `obsidian-notes-repo`: the formatting of the Markdown files
2. `username.github.io`: update the `content` (`obsidian-notes-repo`) submodule and reference
3. `username.github.io`: build and deploy the Hugo site with the latest content

You'll need to create a Personal Access Token (PAT).
You can find how to do that here: <https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens>

##### GitHub Account Settings for Personal Access Token (PAT)

You can also follow my abridged steps below

1. Settings / Developer Settings / Personal access tokens / Tokens (classic) > Personal access tokens (classic)
2. Regenerate the token > Generate new token (classic) - For general use
3. What's this token for name: GH_PAT
4. Set Expiration
5. Select scopes > check the workflow box (Update GitHub Action workflows)
6. Copy secret value
7. Go to repo's settings > Secrets and variables > Actions > Actions secrets and variables > Secrets tab > Repository secrets > New repository secret
8. Actions secrets / New secret > Secret Name Should be the same as when created: GH_PAT
9. Paste the secret value
10. Click "Add secret"

#### `obsidian-notes-repo`: automate formatting Markdown files

Create the following file in path: `.github\workflows\format-markdown.yml`

```plaintext
C:.
\---projects
    +---username.github.io   <- GitHub Repository
    |   +---content          <- Submodule in GitHub Repository
    |   |   +---.obsidian
    |   \---theme
    +---obsidian-notes-repo  <- GitHub Repository
    |   +---.github
    |       \---workflows
    |               format-markdown.yml  <- File created
```

In that file I have the following:

```yaml
name: Format Markdown

on:
  push:
    branches:
      - "main" # Ensures the workflow runs only when changes are pushed to the main branch, avoiding unnecessary actions for other branches.

  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

jobs:
  markdown-format:
    runs-on: ubuntu-latest
    # Uses a reliable and up-to-date Linux environment for consistent execution of the workflow.

    steps:
      - name: Checkout code
        uses: actions/checkout@v3
        with:
          token: ${{ secrets.GH_PAT }} # Provides access to the repository to retrieve and modify its content.

      # Prepares the environment to run Node.js-based tools, ensuring compatibility with Prettier.
      - name: Set up Node.js
        uses: actions/setup-node@v3
        with:
          node-version: "16"

      # Installs Prettier globally to enforce consistent Markdown formatting rules across the repository.
      - name: Install Prettier
        run: npm install -g prettier

      # Automatically formats all Markdown files, ensuring consistent code style and readability.
      - name: Format Markdown files
        run: prettier --write "**/*.md"

      # Configures Git credentials for the bot, stages any formatting changes, and commits them if there are modifications.
      - name: Commit changes
        run: |
          git config --global user.name "github-actions[bot]"
          git config --global user.email "github-actions[bot]@users.noreply.github.com" 
          git add .
          git diff --quiet && git diff --staged --quiet || git commit -m "Formatted Markdown files"
      # Outputs the repository's remote URL to verify that it is correctly set up for pushing changes.
      - name: Debug remote URL
        run: git remote -v
      # Verifies that the GitHub Personal Access Token (PAT) is correctly injected as an environment variable for authentication.
      - name: Debug PAT (Sensitive info hidden)
        run: echo $GH_PAT | cut -c1-4 && echo "***"
        env:
          GH_PAT: ${{ secrets.GH_PAT }}
      # Pushes the committed changes back to the main branch, ensuring the repository reflects the latest formatted content.
      - name: Push changes
        env:
          GH_PAT: ${{ secrets.GH_PAT }}
        run: |
          git remote set-url origin https://x-access-token:${GH_PAT}@github.com/${{ github.repository }}.git
          git push origin HEAD
```

#### `username.github.io`: automate updating content and deploying the Hugo site

You'll still need to follow the step 3 and step 4 in Hugo's document on [HOSTING AND DEPLOYMENT Host on GitHub Pages](https://gohugo.io/hosting-and-deployment/hosting-on-github/) (i.e. from the main menu choose **Settings** > **Pages** Change the **Source** to `GitHub Actions`).

Create the following directory `.github\workflows\` to create the following two files:

1. `.github\workflows\hugo.yml`
2. `.github\workflows\update-submodlue-reference.yml`

```plaintext
C:.
\---projects
    +---username.github.io   <- GitHub Repository
    +---.github
    |   \---workflows
    |           hugo.yml                        <- Create file
    |           update-submodule-reference.yml  <- Create file
    |   +---content          <- Submodule in GitHub Repository
    |   |   +---.obsidian
    |   \---theme
    +---obsidian-notes-repo  <- GitHub Repository
```

##### Workflow to build and deploy the Hugo site with the latest content

```yaml
name: Update Submodule Reference

on:
  # Runs on pushes targeting the default branch
  push:
    branches: ["main"]
  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

  # Runs every 14 days on a schedule (cron expression)
  schedule:
    - cron: "0 0 */14 * *" # Every 14 days at midnight UTC

jobs:
  update-submodule:
    runs-on: ubuntu-latest

    permissions:
      contents: write # Required to push changes to the repository

    steps:
      # Checkout the repository, including submodules
      - name: Checkout code
        uses: actions/checkout@v3
        with:
          submodules: "true" # Ensure submodules are checked out

      # Forcefully update the submodule and resolve conflicts by resetting
      - name: Update submodule and resolve merge conflicts
        run: |
          cd ./content/

          # Fetch the latest changes from the submodule's remote
          git fetch origin

          # Force reset the submodule to the latest commit (use 'main' or your desired branch)
          git reset --hard origin/main  # Adjust 'main' to the correct branch name

          # Go back to the main repository
          cd -

      - name: Configure Git identity for the commit
        run: |
          git config --global user.name "github-actions[bot]"
          git config --global user.email "github-actions[bot]@users.noreply.github.com"

      - name: Check for submodule reference changes
        run: |
          git diff ./content/
          if ! git diff --quiet ./content/; then
            echo "Submodule reference updated."
            git add ./content/
            git commit -m "Resolved submodule merge conflict by accepting incoming changes"
            git push
          else
            echo "No changes in submodule reference."
          fi
        env:
          GITHUB_TOKEN: ${{ secrets.GH_PAT }}
```

##### Workflow to update the `content` (`obsidian-notes-repo`) submodule and reference

```yaml
name: Deploy Hugo site to Pages

on:
  workflow_run:
    workflows: ["Update Submodule Reference"]
    types:
      - completed # This ensures the dependent workflow runs after Workflow 1 completes

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
      HUGO_VERSION: 0.128.0
    steps:
      - name: Install Hugo CLI
        run: |
          wget -O ${{ runner.temp }}/hugo.deb https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_linux-amd64.deb \
          && sudo dpkg -i ${{ runner.temp }}/hugo.deb
      - name: Install Dart Sass
        run: sudo snap install dart-sass
      - name: Checkout
        uses: actions/checkout@v4
        with:
          submodules: recursive # Ensures submodules are cloned recursively
      - name: Setup Pages
        id: pages
        uses: actions/configure-pages@v5
      - name: Install Node.js dependencies
        run: "[[ -f package-lock.json || -f npm-shrinkwrap.json ]] && npm ci || true"
      - name: Build with Hugo
        env:
          HUGO_CACHEDIR: ${{ runner.temp }}/hugo_cache
          HUGO_ENVIRONMENT: production
        run: |
          hugo \
            --gc \
            --minify \
            --baseURL "${{ steps.pages.outputs.base_url }}/"
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
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
        id: deployment
        uses: actions/deploy-pages@v4
```

### Ignore Obsidian Markdown templates when building your Hugo site

When managing content using Obsidian you're most likely to use your own templates when
creating notes. For this reason your Obsidian Markdown templates front matter may not
adhere to what Hugo expects.

> You may get issues like the following:
>
> > ERROR the "date" front matter field is not a parsable date: see C:\Users\username\projects\hugo-site\content\Templates\templateName.md

[Configure Hugo modules `excludeFiles`](https://gohugo.io/hugo-modules/configuration/#module-config-mounts) - configuration options for a module

To fix this possible issue consider adding the following to your Hugo project's YAML file; `C:\Users\username\projects\hugo-site\hugo.yaml`

```YAML
module:
  mounts:
    - excludeFiles: Templates/*
      source: content
      target: content
```

If you're using TOML as your configuration file add the following:

```toml
[module]
    [[module.mounts]]
        excludeFiles = 'Templates/*'
        source = 'content'
        target = 'content'
```

[Propose edits or changes on GitHub](https://github.com/matt2ology/tech-journal-and-blog-content/blob/main/post/blog/from-notes-to-website-automating-hugo-with-github-pages-and-obsidian.md)
