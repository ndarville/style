Style Guide for HTML
====================

General
-------
1. 4-space indentation
2. Use slashes in self-closing elements (eg `<img />`, `<hr />`), including `<meta>`

Attribute Order
---------------
* class
* id, name
* rel, data-*, hreflang
* src, for, type, href, value
* step
* title, alt, placeholder
* (checked), (selected), (disabled), (required), (autofocus)
* aria-*, role

hreflang

HTML5 Containers
----------------
Use HTML5 containers like

* `<main role="main">`
* `<header role="banner">`
* `<section role="region">`
* `<nav role="navigation">`
* `<footer role="contentinfo">`

### Navigation ###

Do not use

```html
<ul id="site-navigation" role="navigation">
    <li><a href="#">Home</a></li>
    <li><a href="#">About</a></li>
    <li><a href="#">404</a></li>
</ul>
```

Instead, use

```html
<nav role="navigation">
    <a href="#">Home</a>
    <a href="#">About</a>
    <a href="#">404</a>
</ul>
```

Two significant differences between the two:

1. First, `ul#site-navigation` is replaced with `nav`.
2. Second, the navigation no longer contains list items, only links.

    The argument for this is that a screenreader will read the first case as

    >List item 1: Home; List item 2: About; List item 3: 404.

    Which is *way* too belaboured for a user. The latter example is better UX.

You can optionally wrap the links in `<span>`. You can also give the `<nav>` element an id.

`<meta>`
--------
* `name="description" content="{{ page.description }}"`
* `name="author" content="{{ page.author }}"`

* `http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"`
* `name="viewport" content="width=device-width, initial-scale=1"`

### Open Graph ###

* `property="og:title" content="{{ page.title }}"`
* `property="og:description" content="{{ page.description }}"`
* `property="og:url" content="{{ page.permalink }}"`

#### Optional ####

* `property="og:type" content="article"`
* `property="og:image" content="image.png"`

### Twitter (Optional) ###

* `name="twitter:creator" content="@pessimism"`
* `name="twitter:site" content="@HafniaTimes"`
* `name="twitter:card" content="summary_large_image"`

### Language ###

* `<html lang="en">`
* `property="og:locale" content="en"`

#### Alternate Languages ####

* `<link rel="alternate" hreflang="da" href="/da" />`
* `property="og:locale:alternate" content="da"`

Language Codes
--------------
There are three types of language metadata:

1. `<html lang="">`
2. `<link rel="alternate" hreflang=""> /`
3. `<meta property="og:locale" content="" />` [#][hreflang]
    - (And of course `og:locale:alternate`)

Unless required by specificity, stick to the [`ISO 639-1` language format][iso].


[hreflang]: https://support.google.com/webmasters/answer/189077?hl=en
[iso]: https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes
