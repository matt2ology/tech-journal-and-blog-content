---
authors: Ryan Schachte
categories:
date: 2024-12-23
draft: true
source-url: https://www.youtube.com/watch?v=LIFvgrRxdt4&ab_channel=RyanSchachte
mediums: articles
notes: reference
tags: readwise, reference/articles, consumed
title: Reference - Creating a Blog With Hugo and Github in 10 Minutes
---

## Creating a Blog With Hugo and GitHub in 10 Minutes

![rw-book-cover](https://i.ytimg.com/vi/LIFvgrRxdt4/hqdefault.jpg?sqp=-oaymwEjCNACELwBSFryq4qpAxUIARUAAAAAGAElAADIQj0AgKJDeAE=&rs=AOn4CLCNsEIVvwTC-frCL-9kz5iuBaTA4g)

published-date: 2020-12-21

**Link:** [Creating a Blog With Hugo and GitHub in 10 Minutes](https://www.youtube.com/watch?v=LIFvgrRxdt4&ab_channel=RyanSchachte)

## Highlights

### id820195256

> one repository on GitHub that houses the actual code that we're iterating on uh you know making our posts and our drafts etc. and then we're going to have another repository that we're actually deploying off of and this will be hosted through GitHub pages
> \- [(View Highlight)](https://read.readwise.io/read/01je7pdmmgwdrjkpjdys31m1ej)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01je7pdmmgwdrjkpjdys31m1ej)

1. Hugo development Repo: a repo that house the Hugo source code and framework
2. GitHub Pages: Another repo that will just house the output "pages" (i.e. the Markdown to HTML code)

### id820195555

> Hugo has some nice themes available on their site again the link
> \- [(View Highlight)](https://read.readwise.io/read/01je7pkzsqq51mj6wj5drkmzj5)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01je7pkzsqq51mj6wj5drkmzj5)
Hugo Themes: <https://themes.gohugo.io/themes/>

### id819842801

> URL that will be kind of the prefix to all of the sub pages that you visit for GitHub
> \- [(View Highlight)](https://read.readwise.io/read/01je4pz9jxdtjh8zy2w8tx3g0s)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01je4pz9jxdtjh8zy2w8tx3g0s)
In config.toml baseURL = `https://username.github.io/`

### id819842627

> we want to check is we want to see if this actually looks okay so we can actually preview this site locally in order to do that what we need to do is we just run Hugo server
> \- [(View Highlight)](https://read.readwise.io/read/01je4pwfyy8n30b0j9zdrcwvmn)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01je4pwfyy8n30b0j9zdrcwvmn)
`hugo server`

### id820252861

> For GitHub, it's very simple; you're just going to use the name of the project that you're deploying off.
> \- [(View Highlight)](https://read.readwise.io/read/01je7y5mrsd31wfchzhhfhxf78)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01je7y5mrsd31wfchzhhfhxf78)

```yml
baseURL = "https://username.github.io/"
languageCode ="en-us"
title = "My blog"
theme ="<theme>"
```

### id820253320

> run Hugo server
> \- [(View Highlight)](https://read.readwise.io/read/01je7ya7gx5766a8gem50nm1e2)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01je7ya7gx5766a8gem50nm1e2)
Run locally to see the output

> $ `hugo server`

### id819843255

> add a new post. In order to add a new post, you simply just need to go into hugo new posts and then the name of the post. So, we'll just call it mypost.md
> \- [(View Highlight)](https://read.readwise.io/read/01je4q3pzchk43krha06qvkay6)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01je4q3pzchk43krha06qvkay6)
To create a new post:

> $ `hugo new posts/filename.md`

### id819843556

> deploying off of the main branch
> \- [(View Highlight)](https://read.readwise.io/read/01je4qabhzvaj75v77y7k0dh09)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01je4qabhzvaj75v77y7k0dh09)
Main branch of `https://username.github.io`

### id820251697

> we created two repositories; what was the point of that?" So, the point of that is that this is where the code is going to live, but this is not where we want to house the static assets that are going to be used in our other blog. So, what we're going to do is add our other blog as a sub module, and that is going to basically allow us to store just the static assets that were generated in a separate repo. This is a good way to organize your code.
> \- [(View Highlight)](https://read.readwise.io/read/01je7xrecfbb7yf6r6znk8574f)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01je7xrecfbb7yf6r6znk8574f)

1. Development branch that was created via: `hugo new site websitename`
2. The public site (`https://username.github.io`)
3. From the "development repo": `git submodule add -b main https://github.com/username/username.github.io public`

### id826778011

> add a git sub module and that's basically going to be a reference to this repository and we're just going to really easily deploy out of this
> \- [(View Highlight)](https://read.readwise.io/read/01jfhmc4sccks6kpga24f0f6he)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfhmc4sccks6kpga24f0f6he)
The Hugo, "blog", repository will have the GitHub Pages, `username.github.io`, repository as the "public" folder as a submodule

### id826778160

> my intentions behind this is the static files that get generated will actually add them into the public folder automatically
> \- [(View Highlight)](https://read.readwise.io/read/01jfhmh0xtr6v1h59fy7d7xzqw)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfhmh0xtr6v1h59fy7d7xzqw)
From the Hugo "Blog" repository every time you enter the command `hugo` to build your site and "transpiles" the markdown files publishing the files to the public directory as static HTML files.
But do note, and a reminder that, Hugo does not clear the public directory before building your site. Existing files are overwritten, but not deleted. This behavior is intentional to prevent the inadvertent removal of files that you may have added to the public directory after the build.
Depending on your needs, you may wish to manually clear the contents of the public directory before every build.

### id826778717

> generate my static files and the static files again will go into public so all i need to do to build the code is simply run hugo
> \- [(View Highlight)](https://read.readwise.io/read/01jfhmtmc6jnss1nr2x5hq25ve)

### id826778885

> git remote v the origin is pointing to my simple engineer github repository and that's because we're in the public sub
> module
> \- [(View Highlight)](https://read.readwise.io/read/01jfhmxef83nngf3tjnefnxr0a)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfhmxef83nngf3tjnefnxr0a)
`git remote -v`
In directory path, blog/public, (the submodule) you'll see that the origin is pointing to the `username.github.io` repository

### id826780133

> it will automatically get deployed and the reason it automatically gets deployed is if we go into settings
> and we scroll down you'll notice that there is a github pages thing and it says your site is ready to be published at this url and the branch that we're deploying off of is the main branch
> \- [(View Highlight)](https://read.readwise.io/read/01jfhn603hbvngtmadtssawffr)
