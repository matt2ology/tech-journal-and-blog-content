---
authors:
  - Matt2ology
categories:
date: 2025-01-13T02:11:44-08:00
draft: false
notes: blog
tags:
title: Blog - Readwise Obsidian Export Formatting
---

## Readwise Obsidian Export Formatting

Consider using [Zotero](https://www.zotero.org/) as a free alternative to [Readwise service](https://readwise.io/) and their [Reader app](https://readwise.io/read).

This post contains my customized Readwise format when exporting highlights and initial notes to Obsidian. You can create your own by following the link to [Readwise documentation: How can I customize the Readwise to Obsidian Export?](https://docs.readwise.io/readwise/docs/exporting-highlights/obsidian#how-can-i-customize-the-readwise-to-obsidian-export)

### Group Files in Category Folders

- Books -> `books`
- Articles -> `articles`
- Tweets -> `tweets`
- Podcasts -> `podcasts`

### File name

Have "Use Custom File Name" toggled on.

Dynamically generates a string identifier for content, typically used for SEO-friendly URLs or file names. It uses the `author` and `title` fields, applies several formatting and cleaning steps (e.g., converting to lowercase, removing special characters, replacing spaces with hyphens), and truncates the resulting segments to fixed lengths (20 characters for `author` and 30 for `title`).

```django
rwd-{{author|lower|replace("and","")|replace(" ","-")|replace("...","")|truncate(20)}}-{{title|lower|replace(""","")|replace(""","")|replace("'","")|replace("'","")|replace("/","-")|replace(" ","-")|replace(" ","-")|replace("...","")|truncate(30)}}
```

### Page title

```django
## {{ full_title }} (Highlights)
```

### Page metadata

```django
{% if image_url -%}

![rw-book-cover]({{image_url}})

Source published date: {{published_date}}

{% endif -%}
{% if url -%}
**Link:** [{{full_title}}]({{url}})
{% endif -%}
```

### Highlights header

```django
{% if is_new_page %}
## Highlights
{% elif has_new_highlights -%}
## New highlights added {{date|date('F j, Y')}} at {{time}}
{% endif -%}
```

### Highlight

Generates a Markdown entry for a highlight, organizing it into:

1. A heading based on the location or ID of the highlight.
2. The highlight's text presented as a blockquote.
3. An optional link or location description below the text.
4. A bolded section for any accompanying note, optionally linked to the location.

```django
{% if highlight_location == "View Highlight" %}### id{{ highlight_id }}{% elif highlight_location == "View Tweet" %}### id{{ highlight_id }}{% else %}### {{highlight_location}}{% endif %}

> {{ highlight_text }}{% if highlight_location and highlight_location_url %}
> \- [({{ highlight_location }})]({{ highlight_location_url }})
{% elif highlight_location %}
({{ highlight_location }})
{% else %}
<!-- Adding a blank line -->
{% endif %}{% if highlight_note %}
**Initial thought or note on:** {% if highlight_location and highlight_location_url %}[({{highlight_location}})]({{highlight_location_url}}){% elif highlight_location %}({{highlight_location}}){% endif %}
{{ highlight_note }}
{% endif %}
```

#### 1. Header Based on Highlight Location

The template creates a Markdown heading (`###`)

- If `highlight_location` is "View Highlight" or "View Tweet", the heading includes `id{{ highlight_id }}`.
- Otherwise, it uses `highlight_location` as the heading text.

```django
{% if highlight_location == "View Highlight" %}### id{{ highlight_id }}
{% elif highlight_location == "View Tweet" %}### id{{ highlight_id }}
{% else %}### {{highlight_location}}{% endif %}
```

#### 2. Highlight Text

The highlight text is rendered as a blockquote using the `>` Markdown syntax.

```django
> {{ highlight_text }}
```

#### 3. Link to Highlight Location

- If both `highlight_location` and `highlight_location_url` are present:
  - A Markdown link (`[text](URL)`) is created under the highlight text.
- If only `highlight_location` is present:
  - The location is shown in parentheses without a link.
- Otherwise:
  - A blank line is inserted as a placeholder.

```django
{% if highlight_location and highlight_location_url %}
> \- [({{ highlight_location }})]({{ highlight_location_url }})
{% elif highlight_location %}
({{ highlight_location }})
{% else %}
<!-- Adding a blank line -->
{% endif %}
```

#### 4. Highlight Note

If a `highlight_note` exists:

- A bold label `**Initial thought or note on:**` is displayed.
- If `highlight_location` and `highlight_location_url` are available:
  - A Markdown link to the location is appended.
- If only `highlight_location` is available:
  - The location is shown in parentheses.
- The `highlight_note` is displayed below.

```django
{% if highlight_note %}
**Initial thought or note on:** {% if highlight_location and highlight_location_url %}[({{highlight_location}})]({{highlight_location_url}}){% elif highlight_location %}({{highlight_location}}){% endif %}
{{ highlight_note }}
{% endif %}
```

### YAML front matter

```django
authors: {{author}}
categories:
date: {{date|date("Y-m-d")}}
draft: true
{% if url -%}
source-url: {{url}}
{% else %}
sources: {{source}}
{% endif -%}
media: {{category}}
notes: reference
tags: readwise, reference/{{category}}{% for tag in document_tags %}, {{tag}}{% endfor %}
title: Reference - {{title}}
```
