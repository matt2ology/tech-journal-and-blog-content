---
authors: david hwang
categories:
date: 2025-01-16
draft: true
source-url: https://www.youtube.com/watch?v=_QSr2_pxIJs&ab_channel=davidhwang
media: articles
notes: reference
tags: readwise, reference/articles, consumed
title: Reference - Deploy Hugo Blog to Github Pages via Github Actions W/ a Custom Domain
---

## Deploy Hugo Blog to Github Pages via Github Actions W/ a Custom Domain

![rw-book-cover](https://i.ytimg.com/vi/_QSr2_pxIJs/maxresdefault.jpg)

published-date: 2023-02-20

**Link:** [Deploy Hugo Blog to Github Pages via Github Actions W/ a Custom Domain](https://www.youtube.com/watch?v=_QSr2_pxIJs&ab_channel=davidhwang)

## Highlights

### id827478104

> We'll be building and deploying a blog powered by Hugo to GitHub Pages via a custom GitHub action to build a blog
> \- [(View Highlight)](https://read.readwise.io/read/01jfpkrtbz859t8m1hknbqqbcn)

### id827478140

> I drafted a blog post on how you can set up Hugo, configure GitHub actions, and link a custom domain to GitHub Pages, so feel free to go over that.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpkt2m0avaezxhr9yaznedf)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpkt2m0avaezxhr9yaznedf)
[Deploying a Blog Powered by Hugo to Github Pages w/ Custom Domain via Github Actions February 19, 2023 · 4 min · David Hwang](https://theplaybook.dev/docs/deploy-hugo-to-github-pages/)

### id827478757

> you can use Homebrew to install Hugo if you're on a Mac
> \- [(View Highlight)](https://read.readwise.io/read/01jfpkw7gk0sphydbpv679jd6k)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpkw7gk0sphydbpv679jd6k)
Install Hugo on MacOS

```sh
brew install hugo
```

### id827479976

> If you don't have Homebrew installed on your Mac, you can go to brew.sh and copy this command and paste it in your terminal.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpky7mbhgcs413awmasd3gj)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpky7mbhgcs413awmasd3gj)
[Homebrew Homepage](https://brew.sh/)

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### id827481375

> Once you have Brew, you can install Hugo, and you can do Hugo new site and name it however you want with the -f flag, specifying the type of config file that you want to use.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpm0pakmyhcjmp7p0678fpd)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpm0pakmyhcjmp7p0678fpd)
Again that is the following; however, the `-f` flag is optional and will default to `config.toml` if no flag option is provided.

```sh
brew install hugo
hugo new site my-demo-site -f yml
cd my-demo-site
```

The reason he uses YAML as his config file is that the Hugo [PaperMod](https://github.com/adityatelange/hugo-PaperMod/wiki/Installation) theme assumes one to use it.
The author of the theme, Aditya Telange, writes his opinion in their installation guide:

> We'll be using `yml`/`yaml` format for all examples down below, it is recommend to use `yaml` over `toml` as it is easier to read.
>
> You can find any [YAML to TOML](https://www.google.com/search?q=yml+to+toml) converters if needed.

### id827481666

> one of the first things we want to do is edit the config file and get rid of this base URL that's provided for us and just leave that empty for now.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpm4sans3168mfejvr50xm3)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpm4sans3168mfejvr50xm3)
from:

```yml
baseURL: http://example.org/
languageCode: en-us
title: My New Hugo Site
```

to:

```yml
baseURL:
languageCode: en-us
title: My New Hugo Site
```

### id827481829

> Then we can create a new page using the Hugo new command. Here, I'm going to create a test.md file under the docs directory, and you can see how the docs/test MD has been created under the content directory.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpm7n2gqcewadxfhc0edyej)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpm7n2gqcewadxfhc0edyej)

```sh
hugo new docs/test.md
```

### id827481923

> we first want to install the theme.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpm9999at5hzk4dj3hm3at1)

### id827482043

> In our case, we will be using PaperMod
> \- [(View Highlight)](https://read.readwise.io/read/01jfpmavzk250m80vcn7cghh74)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpmavzk250m80vcn7cghh74)
Hugo theme: [PaperMod](https://themes.gohugo.io/themes/hugo-papermod/)
GitHub repository: [PaperMod Repo](https://github.com/adityatelange/hugo-PaperMod)

### id827484238

> So, the first thing you want to do is actually clone this repository.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpmz08n07x6pgvwtn2xcqj7)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpmz08n07x6pgvwtn2xcqj7)
The author of the video uses "Method 1 - Git Clone"

```sh
git clone https://github.com/adityatelange/hugo-PaperMod themes/PaperMod --depth=1
cd themes/PaperMod
git pull
```

**Method 2 - Git Submodule (recommended):**

```sh
git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
git submodule update --init --recursive # needed when you reclone your repo (submodules may not get cloned automatically)
```

### id827484355

> Paste that command here, and then we also want to add this as the submodule
> \- [(View Highlight)](https://read.readwise.io/read/01jfpn37rgjnknza4bwed05j32)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpn37rgjnknza4bwed05j32)
The author of the video does both: `git clone` and `git submodule add`.
He doesn't know what he is doing.
You only need to do one (method 1) OR the other (method 2).
**Method 1 - Git Clone**:

```sh
git clone https://github.com/adityatelange/hugo-PaperMod themes/PaperMod --depth=1
cd themes/PaperMod
git pull
```

OR
**Method 2 - Git Submodule (recommended):**

```sh
git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
git submodule update --init --recursive # needed when you reclone your repo (submodules may not get cloned automatically)
```

### id827484991

> One other thing we want to do is edit this config.yaml down here. I'm going to specify the theme as paper mod
> \- [(View Highlight)](https://read.readwise.io/read/01jfpn9xy44ntb5sh1qtn1763h)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpn9xy44ntb5sh1qtn1763h)

```yml
baseURL:
languageCode: en-us
title: My New Hugo Site
theme: PaperMod
```

### id827485054

> let's just add some content inside our test.md file before we actually render it. One of the important things that we have to do here is to set draft as false, otherwise it will not render on the page. And let's just say this is a test page with the content saying it's a test page.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpncepj0mjsvc5csc7a8aq6)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpncepj0mjsvc5csc7a8aq6)

```sh
nano content/docs/test.md
```

```markdown
---
title: "Test"
date: 2024-12-20
draft: false
---

## Test Page

This is a test page!
```

### id827486120

> run Hugo server to run this locally. That's going to run on localhost 1313 to see our page running on the port. You can click this test post that we just created, and you can see how that's added to our docs. Test path.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpnnbfrzyq43xzjksx2bamb)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpnnbfrzyq43xzjksx2bamb)

```sh
hugo server
```

### id827486389

> now that we have created our repositories, the next thing we want to do is to add the configuration file for the GitHub Actions
> \- [(View Highlight)](https://read.readwise.io/read/01jfpnr2pqc72e29qgfqjs57cd)

### id827486478

> there are actually two important steps that we want to do here before pushing any changes.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpnt3r2kqbg4nda70ewb0cj)

### id827486494

> The first is to create the GH Pages branch. Otherwise, the GitHub Actions will later throw an error when we try to run one of the steps in the job. So now you can see we have the GitHub Pages branch, and that is a special branch that GitHub uses for its GitHub Pages.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpnte99dv885v630466hvkq)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpnte99dv885v630466hvkq)
Create a branch: `gh-pages`

### id827486680

> the other thing you want to do is come to actions, General, scroll down to the bottom and set the read and write permissions, and save this here.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpnxz0ngr2dv4c8xfhfjtrn)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpnxz0ngr2dv4c8xfhfjtrn)
Repo that houses Hugo code > Settings > Code and automation > Actions > General > Workflow permissions > select "Read and write permissions" > click "save"

### id827487866

> We want to create our deploy.yaml file under .github/workflows, so we first want to actually create these directories, name it .github/workflows, and inside that, I'm going to create a deploy.yaml file.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpp9tzq69gxy25qe6t20k4h)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpp9tzq69gxy25qe6t20k4h)

```sh
mkdir -p .github/workflows
nano .github/workflows/deploy.yml
```

In the command mkdir -p .github/workflows, the -p flag stands for "parents" and serves the following purposes:

1. **Create Parent Directories:** It ensures that any intermediate directories in the specified path (`.github/workflows`) that do not already exist are created. For example, if `.github` doesn't exist, the command will create it along with the `workflows` directory.
2. **No Error if Exists:** If the directory or any part of the path already exists, no error will be thrown. Without `-p`, trying to create an already existing directory would result in an error.
   Practical Use Case: This is especially useful for creating nested directory structures in a single command without having to manually check if the intermediate directories exist.
   In the context of `mkdir -p .github/workflows`, it's commonly used in projects with GitHub Actions to ensure the required directory structure exists for workflow files.

### id827490490

> I will just copy this entire GitHub Action workflow here.
> \- [(View Highlight)](https://read.readwise.io/read/01jfppsvhnnx3hdaswc7vtvtmn)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfppsvhnnx3hdaswc7vtvtmn)
Author goes out of process from step-by-step to imposing you to copy and paste a solution without explanation, logic, or reason. "Trust me bro".
[Add a .github/workflows/deploy.yml file under the project root directory](https://theplaybook.dev/docs/deploy-hugo-to-github-pages/)

### id827490658

> So just copy this entire thing here
> \- [(View Highlight)](https://read.readwise.io/read/01jfppz5g2bcfy759k7d6s7w0p)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfppz5g2bcfy759k7d6s7w0p)

```yml
name: Publish to GH Pages
on:
push:
branches:
- main
pull_request:
jobs:
deploy:
runs-on: ubuntu-latest
steps:
- name: Checkout source
uses: actions/checkout@v3
with:
submodules: true
- name: Checkout destination
uses: actions/checkout@v3
if: github.ref == 'refs/heads/main'
with:
ref: gh-pages
path: built-site
- name: Setup Hugo
run: |
curl -L -o /tmp/hugo.tar.gz 'https://github.com/gohugoio/hugo/releases/download/v0.110.0/hugo_extended_0.110.0_linux-amd64.tar.gz'
tar -C ${RUNNER_TEMP} -zxvf /tmp/hugo.tar.gz hugo
- name: Build
run: ${RUNNER_TEMP}/hugo
- name: Deploy
if: github.ref == 'refs/heads/main'
run: |
cp -R public/* ${GITHUB_WORKSPACE}/built-site/
cd ${GITHUB_WORKSPACE}/built-site
git add .
git config user.name 'dhij'
git config user.email 'davidhwang.ij@gmail.com'
git commit -m 'Updated site'
git push
```

### id827490767

> paste it. Save it
> \- [(View Highlight)](https://read.readwise.io/read/01jfpq1xvj17zs2gtetht30sfw)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpq1xvj17zs2gtetht30sfw)
**TL;DR:** This ensures the site is updated and published automatically whenever changes are pushed to the `main` branch.

- **Source branch:** `main` contains the Hugo project files.
- Destination branch: `gh-pages` hosts the built static site.
- The workflow automates:

1. Fetching the latest source code.
2. Building the site using Hugo.
3. Deploying the generated files to the `gh-pages` branch, which is often used for GitHub Pages hosting.
   This GitHub Actions workflow is designed to automate the process of building and publishing a Hugo-based site to GitHub Pages. Here’s a detailed breakdown of each part of the YAML file:
   **Workflow Name and Triggers**

- **Name:** `Publish to GH Pages` is the identifier for this workflow.
- **Triggers:**
- `push`: The workflow runs whenever there’s a push to the `main` branch.

```yml
name: Publish to GH Pages
on:
push:
branches:
  - main
pull_request:
```

**Job: `deploy`**

- `deploy`: The single job in this workflow.
- `runs-on: ubuntu-latest`: Specifies that the job will run on a virtual machine with the latest version of Ubuntu.

```yml
jobs:
deploy:
runs-on: ubuntu-latest
```

**Step 1: Checkout Source**

- **Purpose:** Checks out the source code from the repository.
- `submodules: true`: Ensures that any Git submodules are also checked out.

```yml
- name: Checkout source
uses: actions/checkout@v3
with:
submodules: true
```

**Step 2: Checkout Destination**

- **Purpose:** If the workflow is running on the `main` branch, it checks out the `gh-pages` branch into a subdirectory called `built-site`. This is where the static site files will be deployed.
- **Conditional Execution:** The `if` condition ensures this step only runs for pushes to the main branch.
- `path`: The `built-site` directory is used to separate the destination (`gh-pages` branch) from the source code.

```yml
- name: Checkout destination
uses: actions/checkout@v3
if: github.ref == 'refs/heads/main'
with:
ref: gh-pages
path: built-site
```

**Step 3: Setup Hugo**

- **Purpose:** Downloads and sets up Hugo, a static site generator.
- **Process:**

1. `curl` fetches the specified Hugo version archive.
2. The archive is extracted into the temporary runner directory (`${RUNNER_TEMP}`).
   **Step 4: Build the Site**

- **Purpose:** Runs Hugo to generate the static site files.
- **Output:** The built site files are stored in the public directory by default.

```yml
- name: Build
run: ${RUNNER_TEMP}/hugo
```

**Step 5: Deploy to `gh-pages`**

- **Conditional Execution:** Only runs for pushes to the main branch.
- **Process:**

1. Copies the built files (`public/*`) into the `built-site` directory (checked-out `gh-pages` branch).
2. Adds the new or updated files to the Git index.
3. Configures Git author details (`user.name` and `user.email`).
4. Commits the changes with the message "`Updated site`".
5. Pushes the updated `gh-pages` branch to the remote repository.

### id827494143

> before you push any changes, we actually have to edit that base URL that we got rid of, so I'm going to edit the config.yaml. And here, our base URL will be github.io slash the name of the repository, which in our case is the Playbook demo. And based on my understanding, you also need this trailing dash right here.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpr3vsc3s9tcfc7vc8ay4st)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpr3vsc3s9tcfc7vc8ay4st)

```yml
baseURL: "https://<username>.github.io/<repo_name>/"
languageCode: en-us
title: My New Hugo Site
```

### id827494334

> I'm going to save that, and let's just check the status. I'll just add all of those and commit this at the first test page.
> And push the changes
> \- [(View Highlight)](https://read.readwise.io/read/01jfprb1a7rh03v4mtefbpq6qx)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfprb1a7rh03v4mtefbpq6qx)
With that now saved you then can add all and commit.

```sh
git status
git add .
git commit -m "Added test page"
```

### id827494442

> go to Actions. Let this load
> \- [(View Highlight)](https://read.readwise.io/read/01jfprd47tbn0ha4s5yc3s15az)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfprd47tbn0ha4s5yc3s15az)
Repo that houses Hugo code > Actions > All workflows "Showing runs from all workflows" > "Added test page"

### id827494579

> while that is loading, let's actually go back to the steps here. I did include what each of these steps are for, and if you do have questions, feel free to comment down below.
> \- [(View Highlight)](https://read.readwise.io/read/01jfprjk1sc13f6453tjn5rfjs)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfprjk1sc13f6453tjn5rfjs)
Oh now he shares what each step does... Definitely not a friendly step-by-step guide.

### id827494695

> The first step checks out our repository under the GitHub workspace and sets the submodules to true, which ensures that our submodule for the theme repository is fetched as well. This GitHub workspace is a variable that is set by GitHub itself. You can come to the GitHub docs to see how it sets the workspace to something like /home/ Runner/work, and so on. We're actually going to see that as part of our log here. In case you're not familiar with GitHub Actions, if you see Checkout, it's going to check out the source. It is going to show you how you initialize a Git repository under /home/ Runner/work/The Playbook demo. So that's going to check out our repository.
> \- [(View Highlight)](https://read.readwise.io/read/01jfprpv6ywa2vj3xb2tjj6t0r)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfprpv6ywa2vj3xb2tjj6t0r)
**TL;DR:** This ensures the site is updated and published automatically whenever changes are pushed to the `main` branch.

- **Source branch:** `main` contains the Hugo project files.
- Destination branch: `gh-pages` hosts the built static site.
- The workflow automates:

1. Fetching the latest source code.
2. Building the site using Hugo.
3. Deploying the generated files to the `gh-pages` branch, which is often used for GitHub Pages hosting.

### id827494803

> We also have to check out our destination branch, which will be GH Pages. GH Pages is a special branch that GitHub recognizes. So, I wrote down here that GitHub Pages is a special branch that GitHub recognizes and uses to publish to your GitHub Pages site. So, what we are doing in this step is referencing that GitHub Pages through this build site directory.
> \- [(View Highlight)](https://read.readwise.io/read/01jfprsf7cd9hqez41rvn5j3ex)

### id827494894

> actions / checkout Repository
> \- [(View Highlight)](https://read.readwise.io/read/01jfprvm4rqx75baccsebmw6w4)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfprvm4rqx75baccsebmw6w4)
[Action for checking out a repo](https://github.com/actions/checkout)

### id827494998

> down here you can see the path is referring to the relative path under the GitHub workspace to place the Repository. So, we are placing the build site directory under the GitHub workspace path, and this is used to reference the gh-pages branch. We configure this here, which we’ll use later. But before we set up Hugo, we install Hugo from the releases page and use that Hugo command to build our aesthetic sites, which will be stored in the public directory by default.
> And during the last step, we are copying all our static site output in the public directory into the build site directory, which references the GitHub Pages. So when we do a git push, that's going to push to GitHub Pages, which GitHub then recognizes and uses to publish to the GitHub Pages site.
> \- [(View Highlight)](https://read.readwise.io/read/01jfprypys7gp8996qvnax9jsp)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfprypys7gp8996qvnax9jsp)

```yaml
# Relative path under $GITHUB_WORKSPACE to place the repository
path: built-site
```

### id827495225

> So that's why when we look at these actions, we can see two different workflows have run. The first one is for the main branch, and the second one is by the GitHub Pages to publish our changes to the GitHub Pages. This is something we didn't configure, and it's just done by the bot.
> \- [(View Highlight)](https://read.readwise.io/read/01jfps2wf15dsxw32mjfy6wft4)

### id827495707

> The last thing we want to do is link a custom domain to GitHub Pages because we don't want to be using this default github.io path URL that's given to us by default.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpsefzv3qmct7hzmzzszgp8)

### id827495717

> The first thing you want to do is purchase your domain from a DNS provider such as Namecheap or GoDaddy. Once you have purchased that, you can go to settings, pages, and enter your domain here.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpsex6tjnzcz074va6w4erp)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpsex6tjnzcz074va6w4erp)
Project repository > Settings > General > Pages > GitHub Pages > Custom domain > enter your domain in the text field box

### id827497046

> when you save your custom domain, at first, this DNS check is going to fail. So, what you actually need to do is go into your DNS provider. In Namecheap, you can click your domain and come to Advanced DNS. You can add these four IP addresses to GitHub Pages as A records and a CNAME record that’s pointing to your github.io URL.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpsjt3j7x7qhg8jq1jbd466)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpsjt3j7x7qhg8jq1jbd466)
The author uses [namecheap.com](https://www.namecheap.com/)
There are other options for Domain Name System (DNS) providers:

- [godaddy.com](https://www.godaddy.com/)
- [cloudflare.com](https://www.cloudflare.com/)

### id827497754

> So, if you go into this page shared by the GitHub docs, it shows you how you can configure an apex domain by saving these as A records. These are IP addresses for GitHub Pages, which will then handle the rest of the stuff for us. It says here how you would also want to set up a subdomain, so it tells you how you can add this as the CNAME record.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpt197yk1yngh95vcab47dh)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpt197yk1yngh95vcab47dh)
[Author's section on Link Custom Domain to Github Pages](https://theplaybook.dev/docs/deploy-hugo-to-github-pages/#link-custom-domain-to-github-pages)
[GitHub - Configuring an apex domain](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#configuring-an-apex-domain)
