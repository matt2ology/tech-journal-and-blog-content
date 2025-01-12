---
authors:
  - Matt2ology
categories:
  - how-to
date: 2025-01-11T23:55:35-08:00
draft: false
notes: blog
tags: 
title: "Blog - From Notes to Website: Automating Hugo with GitHub Pages and Obsidian"
---

## From Notes to Website: Automating Hugo with GitHub Pages and Obsidian

For this "how-to" I've tried to write the instructions as agnostic as I can (i.e. the steps can be followed regardless of one's operating system); however, before preceding note, at the time of writing, that I am:

- Working in a windows 11 environment (version: 24H2, OS build: 26100.2605); using PowerShell 7.4.6
- Hugo version: `hugo v0.139.4-3afe91d4b1b069abbedd6a96ed755b1e12581dfe+extended windows/amd64 BuildDate=2024-12-09T17:45:23Z VendorInfo=gohugoio`

To set up and automate deployment for a static website using Hugo, with Obsidian notes as the content source and GitHub Pages as the deployment target, you can follow these steps:

### Prerequisites

- Install [Git](https://git-scm.com/downloads)
    - `git --version`
- Install [Hugo](https://gohugo.io/installation/)
    - `hugo version`
- Install [Obsidian](https://obsidian.md/download)

### 1. Repository Structure

1. **Main Repository**: Host the [Hugo](https://gohugo.io/) project (`hugo-site`).
    - Repository: `hugo-site`
2. **Content Submodule**: Use [Obsidian notes](https://obsidian.md/) for managing content (`obsidian-notes-repo`).
    - Submodule: A separate repository containing Markdown files for your notes.
3. **Public Submodule**: Use the [GitHub Pages](https://pages.github.com/) repository (`username.github.io`) to deploy the generated static site.
    - Submodule: A separate repository for the generated static site.

### 2. Initial Setup

1. **Content Repository**: Set up an Obsidian vault (i.e. a folder on your local file system where Obsidian stores your notes) and initialize a Git repository there.

    ```bash
    git init obsidian-notes-repo
    ```

2. **Public Repository**: [Create the `username.github.io` repository on GitHub](https://pages.github.com/).
3. **Hugo Repository**: Create the folder that will house the static site generator framework

    Using [PowerShell](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7.4) or Bash:
    
    ```bash
    git init hugo-site && cd hugo-site
    ```
    
    Using [Windows Command Prompt](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/windows-commands) (i.e. cmd.exe)
    
    ```cmd
    mkdir hugo-site && cd hugo-site && git init
    ```

#### Add Submodules

1. **Add Obsidian Notes Submodule**:
   ```bash
git submodule add https://github.com/username/obsidian-notes-repo content
   ```
2. **Add Public Deployment Submodule**:
   ```bash
   git submodule add -b main https://github.com/username/username.github.io public
    ```

#### Checkpoint - Verify Directory Structure

Following the steps listed so far should result in the following directory structure


```plaintext
C:.
\---projects
    +---hugo-site
    |   +---content
    |   |   +---.obsidian
    |   \---public
    +---obsidian-notes-repo
    \---username.github.io
```

#### Create Hugo project skeleton

[Hugo directory structure](https://gohugo.io/getting-started/directory-structure/)

```bash
hugo new site . --force
```

>Without `--force` you'll get the following prompt:
>> Error: C:\Users\username\projects\hugo-site already exists and is not empty. See --force.

#### Set up `.gitmodules`

```plaintext
[submodule "content"]
    path = content
    url = https://github.com/username/obsidian-notes-repo
[submodule "public"]
    path = public
    url = https://github.com/username/username.github.io
```

### 3. Configure GitHub Actions

Create a GitHub Actions workflow to automate pulling the latest content, building the Hugo site, and deploying it.

#### Create `.github/workflows/deploy.yml`

```yaml
name: Deploy Hugo Site

# GitHub Account Settings:
# 01. Settings / Developer Settings / Personal access tokens / Tokens (classic) > Personal access tokens (classic)
# 02. Regenerate the token > Generate new token (classic) - For general use
# 03. Note - What's this token for name: GH_PAT_HUGO
# 04. Set Expiration
# 05. Select scopes > check the workflow box (Update GitHub Action workflows)
# 06. Copy secret value
# 07. Go to repo's settings > Secrets and variables > Actions > Actions secrets and variables > Secrets tab > Repository secrets > New repository secret
# 08. Actions secrets / New secret > Secret Name Should be the same as when created: GH_PAT_HUGO
# 09. Paste the secret value
# 10. Click "Add secret"

on:
  push:
    branches:
      - main # Trigger the workflow when code is pushed to the 'main' branch
  workflow_dispatch: # Allow manual triggering of the workflow via the GitHub Actions UI
  schedule:
    - cron: '0 0 */14 * *' # Run every 14 days at midnight UTC

jobs:
  deploy:
    runs-on: ubuntu-latest
    # Specify the OS environment where the workflow will run

    steps:
    # Clone the repository and ensure any submodules are cloned recursively
    - name: Checkout Repository
      uses: actions/checkout@v3
      with:
        submodules: recursive

    # Install the latest version of Hugo to generate the static site
    - name: Set Up Hugo
      uses: peaceiris/actions-hugo@v2
      with:
        hugo-version: 'latest'

    # Commit submodule changes if there are updates, otherwise continue
    - name: Update Content Submodule
      run: |
        git submodule update --remote --merge content # Update the specified submodule to its latest remote version and merge changes
        git add content # Stage changes in the submodule
        git commit -m "Update content submodule" || echo "No changes to commit"

    # Generate the static site using Hugo, with minified output for optimized performance
    - name: Build Hugo Site
      run: hugo --minify

    # Authenticate using the GitHub token to push changes
    # Specify the directory containing the built static site to deploy to GitHub Pages
    - name: Deploy to GitHub Pages
      uses: peaceiris/actions-gh-pages@v3
      with:
        github_token: ${{ secrets.GH_PAT_HUGO }}
        publish_dir: ./public
```

### 4. Workflow Explained

1. **Checkout Repository**:
    - Ensures the Hugo repository and its submodules are cloned.
2. **Set Up Hugo**:
    - Installs Hugo for the build process.
3. **Update Content Submodule**:
    - Updates the `content` submodule to pull the latest changes from the Obsidian notes repository.
    - Commits the updated submodule reference.
4. **Build Hugo Site**:
    - Runs Hugo to generate the static website in the `public` directory.
5. **Deploy to GitHub Pages**:
    - Deploys the contents of the `public` directory (a submodule) to the `username.github.io` repository.

### 5. Maintain Your Workflow

1. **Obsidian Workflow**:
    - Update your notes and push changes to the `obsidian-notes-repo` repository.
2. **Trigger GitHub Actions**:
    - Push changes to the `main` branch of the `hugo-site` repository to trigger the deployment workflow.
3. **Monitor Submodules**:
    - Periodically ensure that the `public` and `content` submodules are synchronized with their respective remote repositories.

### 6. Ignore Obsidian Markdown Templates

When managing content using Obsidian you're most likely to use your own templates when
creating notes. For this reason your Obsidian Markdown templates front matter may not
adhere to what Hugo expects.

> You may get issues like the following:
> > ERROR the "date" front matter field is not a parsable date: see C:\Users\username\projects\hugo-site\content\Templates\templateName.md
 
[Configure Hugo modules `excludeFiles`](https://gohugo.io/hugo-modules/configuration/#module-config-mounts) - configuration options for a module

To fix this possible issue consider adding the following to your Hugo project's TOML file; `C:\Users\username\projects\hugo-site\hugo.toml`

```toml
[module]
    [[module.mounts]]
        excludeFiles = 'Templates/*'
        source = 'content'
        target = 'content'
```
