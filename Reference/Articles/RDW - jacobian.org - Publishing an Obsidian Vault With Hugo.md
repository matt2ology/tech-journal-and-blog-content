---
authors:
  - jacobian.org
categories: 
date: 2024-12-23
draft: false
source-url: https://jacobian.org/til/hugo-obsidian/
mediums: articles
notes: reference
tags:
  - readwise
  - reference/articles
  - consumed
title: Reference - Publishing an Obsidian Vault With Hugo
---
## Publishing an Obsidian Vault With Hugo

![rw-book-cover](https://jacobian.org/cards/til/hugo-obsidian-cloudflare.png)

published-date: 2024-03-06

**Link:** [Publishing an Obsidian Vault With Hugo](https://jacobian.org/til/hugo-obsidian/)

## Highlights
### id827038468

> My requirements
>   I want to:
>   • **Edit my content in Obsidian**.
>   • **Design and publish the web version with Hugo**. I want to use Hugo but only because it’s the tool I know. I’m not sure it’s actually the best tool for this – as you’ll see below it has some warts that makes this more difficult than it might with other static site generators. But I know Hugo pretty well, and am happy enough with it despite its warts.
>   • **Not have to worry about correct Hugo frontmatter** (dates, titles, etc). I *can* edit these in Obsidian via its Properties feature, but I want that to be optional. I want to be able to work on stuff in Obsidian and not thing about the Hugo part *at all* (unless I want to).
>   • **Publish automatically**. I don’t want an explicit “commit” or “push” or “publish” step; I just want to write and have stuff appear on the web.
> \- [(View Highlight)](https://read.readwise.io/read/01jfkdf9ekndj91qyaxmnybwq4)

### id827039573

> [obsidian-git](https://github.com/denolehov/obsidian-git)
>   Automate pushing from my vault to a Github repo
> \- [(View Highlight)](https://read.readwise.io/read/01jfkdjdrdwpwc16c0d4qyrtb6)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfkdjdrdwpwc16c0d4qyrtb6)
Why not just use normal Git?

### id827039614

> [Templater](https://github.com/SilentVoid13/Templater)
>   More powerful templates in Obsidian. I’m not using this very heavily yet, but it’s the tool I’ll use to ensure consistent frontmatter when and if I want to start using it more.
> \- [(View Highlight)](https://read.readwise.io/read/01jfkdkhg5z70v004bebx92swe)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfkdkhg5z70v004bebx92swe)
Why not something like QuickAdd. Why not just start with the, standard/native, Obsidian templates? If you're not heavily using the tool then why not be more simple in your process?

### id827039809

> [obsidian-export](https://github.com/zoni/obsidian-export)
>   Converts vault documents from Obsidian’s Markdown variant into “plain” markdown. Also adds empty frontmatter where it’s missing to prevent Hugo from complaining about files without frontmatter.
> \- [(View Highlight)](https://read.readwise.io/read/01jfkdq6nzp3pw4er4reb6swdd)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfkdq6nzp3pw4er4reb6swdd)
Again with the complex... Markdown is just a standard text file. Obsidian only comes into play if you use functionality/features like [Wikilinks](https://help.obsidian.md/Linking+notes+and+files/Internal+links#Supported+formats+for+internal+links) (e.g. `\[\[Three laws of motion\]\]`) instead of the standard Markdown (e.g. `\[Three laws of motion\]\(Three%20laws%20of%20motion.md\)`); or, when using Wikilinks they try linking to a block in a note.

### id827043470

> [Cloudflare Pages](https://pages.cloudflare.com/)
>   Where I’m publishing. I have no love for Cloudflare but their product is fast and free and stable, and I don’t dislike their CEO quite enough to have cause to look elsewhere.
> \- [(View Highlight)](https://read.readwise.io/read/01jfke4d2tz5p32emect14g3qv)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfke4d2tz5p32emect14g3qv)
> I don't dislike their CEO quite enough to have cause to look elsewhere.
Didn't know you were on first name bases...

### id827043746

> I have a Hugo site as a GitHub repo. It’s a normal Hugo site, nothing special here.
> \- [(View Highlight)](https://read.readwise.io/read/01jfke878k134b5t2s0rc1q62f)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfke878k134b5t2s0rc1q62f)
Then why not just use GitHub Pages?!

### id827043805

> [obsidian-git](https://github.com/denolehov/obsidian-git) is set up to auto-commit and auto-push changes to the vault. The key settings are:
>   • **Advanced -> Custom base path: `..`**. This is the key setting that tells obsidian-git that my `vault` folder is actually a subdirectory of the root git repo. Without this setting, pushes will fail.
> \- [(View Highlight)](https://read.readwise.io/read/01jfkea7aqwnzgqqm8shpazwdw)

### id827087249

> A pre-commit script (managed by [Husky](https://typicode.github.io/husky/)) that converts the vault:
>   rm -rf content/*
>   bin/obsidian-export vault/ content/ --frontmatter always
>   bin/make-index-files content/
>   git add -A content/
>   This:
>   • blows away the existing site content
>   • converts the obsidian content in `vault/` to plain markdown in `content/`, adding frontmatter
>   • makes missing `_index.md` files, [see below](https://jacobian.org/til/hugo-obsidian/#make-index-files)
>   • adds the converted `content/` dir to the in-flight git commit
>   Thus, when obsidian-git auto-commits, this script is run, and a converted site it pushed to github.
> \- [(View Highlight)](https://read.readwise.io/read/01jfkpgnqafffv0bxyxsffp91g)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfkpgnqafffv0bxyxsffp91g)
```sh
rm -rf content/*
bin/obsidian-export vault/ content/ --frontmatter always
bin/make-index-files content/
git add -A content/
```
> bin/obsidian-export vault/ content/ --frontmatter always
Why?! Doing unnecessary steps to be pretend to be hacker?

### id827102752

> Adding missing `_index.md` files
>   The last missing piece for me was adding missing `_index.md` files. This isn’t necessary if you don’t have multiple levels of content nesting, but I do, and so Hugo needs a little extra help here.
> \- [(View Highlight)](https://read.readwise.io/read/01jfkpr0dff37rx84vgyfe3xyc)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfkpr0dff37rx84vgyfe3xyc)
Over engineering solutions for a "simple" blog

### id827102995

> Hugo only partially translates your source content hierarchy into a site hierarchy. Hugo considers any top-level directories as “sections” and creates hierarchy for these, but doesn’t automatically do anything with deeper nesting. That is, if you have `content/aaa/one.md` and `content/bbb/two.md`, Hugo gets this, and your built site will have `aaa` and `bbb` sections, and your two documents will have URLs like `example.com/aaa/one/` and `exmaple.com/bbb/two/`. But, if you then add `content/aaa/ccc/three.md`, that document will be considered part of the `aaa` section, and will have a URL like `example.com/aaa/three.md` – the `ccc` subdirectory vanishes!
> \- [(View Highlight)](https://read.readwise.io/read/01jfkpw5ef3g40bwww7nkxdp3s)

### id827103069

> The way you tell Hugo that you want to preserve this deeper nesting is by adding an `_index.md` file. This forces Hugo to consider that directory a “section”. So, if you add `content/aaa/ccc/_index.md`, Hugo now considers `aaa/ccc` a “section”, and your `three.md` document will be at `example.com/aaa/ccc/three/`.
> \- [(View Highlight)](https://read.readwise.io/read/01jfkpx17fba1r1tz0jcqe5sw3)

### id827103111

> I don’t want to have to think about this, so I wrote this little script to do it as part of the pre-commit hook
> \- [(View Highlight)](https://read.readwise.io/read/01jfkpxpkmxqdpe8ap7kcd1g7j)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfkpxpkmxqdpe8ap7kcd1g7j)
Forces Hugo to consider sub folders as a "section" in the directory path.
`content/aaa` is a section, but won't consider `content/aaa/ccc` as its own independent section. So the author uses the following Python script:
```python
#!/usr/bin/env python
import sys
from pathlib import Path
def make_indexes(containing_dir: Path):
for dir, _, _ in containing_dir.walk():
# don't create a top-level _index
if dir == containing_dir:
continue
index_path = dir / "_index.md"
if not index_path.exists():
index_path.write_text(f"---\ntitle: {dir.name.title()}\n---\n")
if __name__ == "__main__":
make_indexes(Path(sys.argv[1]))
```



