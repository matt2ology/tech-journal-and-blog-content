---
authors:
  - Matt2ology
categories:
  - blog
date: 2025-01-22T01:32:20-08:00
draft: false
notes: blog
tags: 
title: Don't Comment Hugo Shortcodes Links And Cross References
---

## Don't comment Hugo shortcodes links and cross references

<!-- [Propose edits or changes on GitHub](link to GitHub repo of file) -->

[Propose edits or changes on GitHub](https://github.com/matt2ology/tech-journal-and-blog-content/blob/main/post/blog/dont-comment-hugo-shortcodes-links-and-cross-references.md)

[SEE TO -> Hugo Documentation: Content Management - Links and Cross References](https://gohugo.io/content-management/cross-references/)

Another late night of debugging and too stubborn to abide by my own prescribe and new
year's sleep schedule...

In my Obsidian content templates I had the following as a reminder to how Hugo internal
document linking is formatted:

```markdown
<!-- Idea 1: Key point or insights written in your own words \[reference\]\(\{\{\< relref "path/to/target-document.md#my-target-header" \>\}\}\) -->
```

Don't do this because Hugo will still try to parse the format as if it was not commented out
via Markdown.

```bash
ERROR [en] REF_NOT_FOUND: Ref "path/to/target-document.md": "/home/runner/work/matt2ology.github.io/matt2ology.github.io/content/post/literature/greg-deckler-learn-power-bi.md:23:74": page not found
```

## Additional learning - Flexibility with Permalinks

### `relref`

- **`relref`**: It does not take into account Hugo's URL generation rules, meaning if you use `relref`, it will just generate a link based on the file's directory structure. This means it can break if Hugo changes the URL structure of a page (e.g., if permalinks are set differently or URLs are customized).

- **`relref`** is ideal when you want to create links **relative to the current file** and don't need to account for the final URL structure. It’s simpler and efficient in straightforward projects where URLs are standard and do not involve complex configurations.

### `ref`

- **`ref`**: Is more flexible with permalinks because it resolves to the **final URL** of the target page. If Hugo is configured to use specific permalinks (e.g., custom URL structures), `ref` will use the correct URL, even if the file is moved or renamed.

- **`ref`** is ideal for more **dynamic projects** where permalinks are customized or when you want the link to be flexible in terms of the file structure. `ref` will always point to the **correct, final URL**, making it better for large sites with custom URL schemes, or when links need to be resilient to directory structure changes.
