---
authors: MissCoding
categories:
  - reference
date: 2025-01-21
draft: true
source-url: https://www.youtube.com/watch?v=LSJ5S8VG5aU
media: articles
notes: reference
tags: readwise, reference/articles, consumed, media-consumed
title: Reference - MissCoding - Creating a Free Blog or Static Content Website With Hugo and GitHub Pages With Custom Domain and Ads
---
## Creating a Free Blog or Static Content Website With Hugo and GitHub Pages With Custom Domain and Ads (Highlights)

![rw-book-cover](https://i.ytimg.com/vi/LSJ5S8VG5aU/maxresdefault.jpg)

Source published date: 2022-07-21

**Link:** [Creating a Free Blog or Static Content Website With Hugo and GitHub Pages With Custom Domain and Ads](https://www.youtube.com/watch?v=LSJ5S8VG5aU)

## Highlights
### id827457597

> I'm going to show you how to create a blog and host it using GitHub Pages for free. I'll also show you how to add a custom domain and Google Ads.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpatkfsdmxpvtex9e0vjsy6)

### id827457610

> first off, I'm just going to create a repository that’s going to hold my Hugo blog configuration and any of my Markdown blog files.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpavav2y90ft8ecajyavjzq)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpavav2y90ft8ecajyavjzq)
This repo will hold the Hugo framework and directory structure.

### id827457727

> I’m also going to create a second repository that will be for my GitHub Pages. It’s going to hold all my static content.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpawvdajecgn4bwz82enhm9)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpawvdajecgn4bwz82enhm9)
This repo will be `username.github.io` the GitHub Pages repository. This will hold the generated static pages from Hugo.

### id827459714

> go ahead and install Hugo, so you can run the command `brew install hugo`
> \- [(View Highlight)](https://read.readwise.io/read/01jfpb1a31mgm422nndfjaskqs)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpb1a31mgm422nndfjaskqs)
On MacOS

### id827460040

> Then I’m going to use the command hugo new site, and then the site name to create the code for my blog.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpb2qyc9py3tjhcbrdd4jpb)

### id827460045

> once that’s done, I can go and change into that directory.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpb2zr2zmdm495tqc9g4g8w)

### id827460047

> Now I’m going to go ahead and add all that code to git
> \- [(View Highlight)](https://read.readwise.io/read/01jfpb3941et1wc634ac77znh8)

### id827460052

> I’m going to want to do is I’ll just go to my blog repo, as they’ll have all the instructions. I’m just going to want to follow these different instructions. I’m not adding a README for this one, so I can skip that step.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpb3xqnvnkaxwcjf8vfxcrz)

### id827460056

> then I can go ahead and I can add the files and commit
> \- [(View Highlight)](https://read.readwise.io/read/01jfpb44eszdwq9jdx83yph4cj)

### id827460075

> Next up, you're going to want to make sure that you're on the main branch, and you're also going to want to add the remote origin.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpb4t05133b2grzaxk0aqf9)

### id827460088

> So I'm just going to copy this line here; so it's adding the remote origin of my repo, and then I can push my changes there.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpb597y2bqkf72r2tgqhgs8)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpb597y2bqkf72r2tgqhgs8)
> $ git remote add origin https://github.com/username/username.github.io

### id827460470

> I also want to add a git ignore. So what I usually use for creating it ignores is this top tail site, because you can add as many different tech as you want and then just create a git ignore file so that it covers anything that’s kind of relevant
> \- [(View Highlight)](https://read.readwise.io/read/01jfpb71c5xg2y54h5qy6axhyv)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpb71c5xg2y54h5qy6axhyv)
[Toptail site - `.gitignore`](https://www.toptal.com/developers/gitignore)
`.gitignore` for [Hugo](https://gohugo.io/)
```plaintext
# Created by https://www.toptal.com/developers/gitignore/api/hugo
# Edit at https://www.toptal.com/developers/gitignore?templates=hugo
### Hugo ###
# Generated files by hugo
/public/
/resources/_gen/
/assets/jsconfig.json
hugo_stats.json
# Executable may be added to repository
hugo.exe
hugo.darwin
hugo.linux
# Temporary lock file while building
/.hugo_build.lock
# End of https://www.toptal.com/developers/gitignore/api/hugo
```
`.gitignore` for [Microsoft's Visual Studio Code](https://code.visualstudio.com/)
```plaintext
# Created by https://www.toptal.com/developers/gitignore/api/visualstudiocode
# Edit at https://www.toptal.com/developers/gitignore?templates=visualstudiocode
### VisualStudioCode ###
.vscode/*
!.vscode/settings.json
!.vscode/tasks.json
!.vscode/launch.json
!.vscode/extensions.json
!.vscode/*.code-snippets
# Local History for Visual Studio Code
.history/
# Built Visual Studio Code Extensions
*.vsix
### VisualStudioCode Patch ###
# Ignore all local history of files
.history
.ionide
# End of https://www.toptal.com/developers/gitignore/api/visualstudiocode
```

### id827461226

> Hugo has a whole heap of lists of themes, but this is one that I found that I like, so it's called B-list.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpbt46564xvzanm7a14a44k)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpbt46564xvzanm7a14a44k)
[Blist theme for Hugo - Blist is a clean and fast blog theme for your Hugo site](https://github.com/apvarun/blist-hugo-theme)
`git submodule add https://github.com/apvarun/blist-hugo-theme.git themes/blist`

### id827461943

> you're also going to want to install a few things, like this PostCSS CLI, and you're also going to want to install some Node modules. I've already installed the PostCSS CLI, so I'm going to just go ahead and copy these package.json and package lock.json files into my blog directory. And I'm just going to go to the command line and go npm install.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpc5wmhr4b06bbjszvb0v3r)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpc5wmhr4b06bbjszvb0v3r)
To use the "Blist" theme you'd have to do the following:
Configuring theme to a Hugo website
1. Copy `package.json` and `package-lock.json` to the root folder of your website
2. Run `npm install` to install required packages for theme
3. Run `npm i -g postcss-cli` to use PostCSS with Hugo build
4. Set `theme = 'blist`' in the root directory's config.toml
5. Run `npm start` to start your local server
Make sure to commit the above changes to your repository.

### id827463270

> edit your config.toml file, which basically is the configuration for your blog or site.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpccvx7q3kqgv56vgzw84m1)

### id827463455

> The example site has a comp example config, so I've copied that. I'm just going to make some changes when necessary.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpceyfzhdwkypwpts1bz5vn)

### id827463600

> I don't need that base URL; I've already got that included
> \- [(View Highlight)](https://read.readwise.io/read/01jfpcf980jzp2f0eqb2vestje)

### id827463612

> I don't need that title because I've already set that.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpcft93ee6w2pypena35vkb)

### id827463654

> I created that in the en directory, and I'm going to go edit some of the text that’s going to show on the homepage.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpch3m386f6mg1bj77rtz47)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpch3m386f6mg1bj77rtz47)
`en` = "English" content directory path `./content/en/`

### id827463810

> You’ve got a few different parameters. You’ve got like whether you want to enable dark mode toggling, whether you want to enable search, the copyright message, um, your fav icon if you have one, and just some other different color.
>   Configs and you've also got some social media configs as well, so you can configure your different Instagram, YouTube accounts, whatever you want to sort of show.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpcmpzekzrc43sw5nscrwkt)

### id827463828

> base URL is important because otherwise, without it, your theme is not going to usually show correctly.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpcndxdrx4f430saz2seezz)

### id827463859

> I can check what it looks like. And you can do that by running the command Hugo server.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpcpc54ehm4w77xwbnktdy3)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpcpc54ehm4w77xwbnktdy3)
> $ hugo server

### id827463916

> Now that I’ve got that going, what I’m going to want to do is show you how to actually put this onto your actual live URL and host it on your GitHub page.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpcr9vmsgxwa3vx6eq9186m)

### id827463950

> I'm just going to also exclude node modules in the git ignore and I’m just going to do some cleanup there, just so that node modules isn’t checked in because.
>   It's not really good to do that.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpcs0hhx3sqsj0ma95kqw9c)

### id827464007

> now that I've done that, what I'm going to do is I'm going to grab this URL for my GitHub page repo, and I'm going to add another sub module. So what I'm doing is I'm adding it to the public folder, and why I'm doing that is because that's where all the static content gets generated.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpctdvg8a2zdb8pc00a630b)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpctdvg8a2zdb8pc00a630b)
In the directory/repo that has their Hugo framework they'll add the following as a submodule:
```sh
git submodule add https://github.com/username/username.github.io public
```

### id827464160

> it's ignored by the git ignore.
>   So it's telling me that, um, I have to use -f if I want to force this add. I'm just going to force it through using the force command with that -f. Okay, so another issue happened; the public folder already exists because it was generated by Hugo. But if I go ahead and delete it, I should be able to add it.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpcyznfj0zfkeydtjgs5tzx)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpcyznfj0zfkeydtjgs5tzx)
Ignored from the [Toptal suggested `.gitignore` template](https://www.toptal.com/developers/gitignore) that was added earlier.
```sh
git submodule add -f https://github.com/username/username.github.io public
```

### id827464504

> to generate those files you go hugo dash t and then your theme name. So my theme is called B List. And once that generates, you can go ahead and change into your public directory.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpd8egb5hr538gw0v51etjg)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpd8egb5hr538gw0v51etjg)
```plaintext
hugo -t blist
```

### id827464606

> To add pages, you go *hugo new* and then specify the path to the page. I'm going to add a hello world markdown file to the blog directory
> \- [(View Highlight)](https://read.readwise.io/read/01jfpdbm3mvs1jt4j492e9mfms)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpdbm3mvs1jt4j492e9mfms)
```plaintext
hugo new blog/hello_world.md
```

### id827464654

> I’m going to add an about markdown file to the page directory. That's just because of what I've set up in my config.toml file.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpddc0zqy6yxhxnngca21as)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpddc0zqy6yxhxnngca21as)
```plaintext
hugo new page/about.md
```

### id827464799

> I can sort of show you where you might put your images. So you typically put them in the static folder, and then you'd update your config file to align with that.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpdhgx7zdxdt91vyc14ntm8)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpdhgx7zdxdt91vyc14ntm8)
Images go into the `./static` folder.
Then update the `config.toml` file with the path of the `introPhoto`.
```toml
[languages.en.params]
introTitle = "Hey! I'm me"
introPhoto = "me.jpg"
```

### id827465485

> first I'm going to generate the static files. That's right, got to generate them before I try to commit them to the GitHub Pages repo.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpds8zd7d3h979yv48hnd24)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpds8zd7d3h979yv48hnd24)
```sh
hugo -t blist
```

### id827465976

> now that’s done, I'm just going to do.
>   A change directory and set public folder, and I'm going to add the files and commit them.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpdtnj28pkbmjvxwt896rgb)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpdtnj28pkbmjvxwt896rgb)
```sh
cd public
git add .
git commit -m "updated blog"
git push
```

### id827466045

> But what if we want to add a subdomain?
>   Well, you can just specify it here. It's really that simple. So I've got my own website, tripwiretech.com, and I want to add a subdomain called "miscoding tripwire." If I hit save, it's going to add a CNAME file into this GitHub Pages repo, and then I need to go to my DNS provider and configure it because it hasn't been configured yet. So I'm just going to copy that URL because that's where I want my CNAME record to point to.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpdynts7j3w080qmxwrtrey)

### id827466271

> the theme isn’t showing. So that’s what I mentioned earlier, and that you need to update that base URL here.
>   So I’m going to update this base URL to be miscoding.tripwiretech.com. And once I’ve done that, I can just go ahead and I can commit that to my blog.
>   Repo and my GitHub Pages repo. So once that's done, I'm going to go ahead and push those changes.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpe1tzq0qxance8tvwyp4qa)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpe1tzq0qxance8tvwyp4qa)
```toml
baseURL = "https://name.website.com/"
```

### id827466398

> I need to do a pull since it added that CNAME file to my repo, so I just need to pull that change and then I can now push. I'll do the same for my blog repo as well.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpe5g55vctvvspbwnxr2d5d)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpe5g55vctvvspbwnxr2d5d)
First in the "public", the repository that holds the static files for `https://github.com/username/username.github.io`, (i.e. the folder path `./public`)
and then again in the Hugo framework directory/repo (i.e. the level above the `public` directory (`cd ..`) - the root directory of the Hugo repository: `./`

### id827467115

> I'm going to show you how to add Google Ads. You're going to need to go to Google.
>   AdSense allows you to add your domain, and then you can specify that you want to add a sub domain. You can see this madden subdomain option. I’m just going to add misscoding.tripwiretech.com. You might want to note that it says my site isn’t ready to show ads; that’s because my main domain doesn’t have anything at the moment. So Google’s not able to sort of do its thing and check.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpehcjaytv4vx53dbgaa7mn)

### id827467180

> You’re going to want to copy this script here, which will automatically add ads to your pages. What you’re going to do is you’re going to actually edit your theme. A good way to do this would actually be to either create a pull request back to your theme to add ads if they don’t allow for it already, or you could fork if the license allows and add your own functionality on top.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpek6mxmnrcn131x2p0t2xg)

### id827467233

> If you’re adding this, you would typically want to actually parameterize it because you obviously don’t want everyone using your ad ID and publisher ID. So yes, this is my ads.html file.
>   This is what I've added as a file so that I can edit inside the header.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpemgszveq326b838s862em)

### id827467272

> So I've gone to this head file; this is actually going to add to every single page on my website. If I only wanted specific pages, I'd want to go and add it to a different part of the layout.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpenwsyg5jxth9t679rj30r)

### id827467333

> When you're referencing your partial HTML, you should be putting it in quotes. There.
>   And so once I go and generate this again, my static pages should actually have that script included for the Google Ads.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpepvq2zm2darn2wawhfe6h)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfpepvq2zm2darn2wawhfe6h)
Put the script that Google Ad Sense provided into a partial; for example, `ads.html` within your "partials folder (i.e. `./layouts/partials/ads.html`).
```html
{{ partial "ads" . }}
```
and then you can generate your site
```sh
hugo -t blist
```

### id827467511

> I need to be in the public repo, in the public directory, because I've changed what the static content will be.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpexzzk14n93ec739r4rjy6)

### id827467611

> inspect the page, you're going to see the script that indicates that you would have Google Ads. So you can see ads by Google, ads by Google and a few different other scripts that indicate that Google Ads have been included.
> \- [(View Highlight)](https://read.readwise.io/read/01jfpf0qetmwh2b20y2vkc79z4)

