Style Guide for HTML
====================

General
-------
1. 4-space indentation
2. Use slashes in self-closing elements (eg `<img />`, `<hr />`), including `<meta>`

URIs
----
In accordance with [RFC3986, Section 3][rfc3986]:

> `foo://example.com:8042/over/there?name=ferret#nose`

Link Text
---------
In accordance with [HTML Techniques for Web Content Accessibility Guidelines 1.0, Section 6.1][link-text].

**Do not** use `click here` as link text.

**Do not** use call-to-action verbs like `go to our page`.

Use the page or content your are linking to as the text instead.

Bad:

> [Click here] to visit GitHub.

Also bad:

> Click here to [visit GitHub].

Good:

> Click here to visit [GitHub].

Attribute Order
---------------
* class
* id, name, content
* rel, data-*, hreflang
* src, srcset, for, type, charset, sizes, href, media, value
* step
* title, alt, placeholder
* (checked), (selected), (disabled)
* (required), (autocapitalize), (autofocus)
* async, defer, integrity, crossorigin
* aria-*, role

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

Images
------
```html
<picture>
    <source
        type="image/jpeg"
        srcset="image.jpeg 1x, image@2x.jpeg 2x" />
    <img
        class="image"
        src="image.jpeg"
        alt="Alt text"
        title="Title text" />
</picture>
```

Scripts
-------
For externally loaded content, always use a checksum hash (`integrity` for scripts, ie **S**ub**r**esource **I**ntegrity Hash) and `crossorigin="anonymous"`. See [srihash.org][].

### `async` and `defer` ###

`defer` and `async` only work for `<script>` tags where `src` is defined.

The two boolean attributes exist to prevent blocking.

async vs defer vs async+defer

#### `async` ####

1. Download in the background without blocking
2. When finished downloading,
    - block and execute
3. Rendering resumes

#### `defer` ####

1. Download in the background without blocking
2. When finished downloading,
    - block and execute *according to the order specified in the DOM*
3. Rendering resumes

Unfortunately, browsers use `defer` differently, which usually makes it run similarly to `async`.

#### `async defer` ####

`async` overrides `defer`, so using `<script async defer>` is equivalent to `async` with better browser support.

#### Further Reading ####

* [Stack Overflow on `async` and `defer`][a-d]

### Example Script ###

```js
<script
    id="github-bjs"
    type="text/javascript" charset="utf-8"
    src="//buttons.github.io/buttons.js"
    async defer
    integrity="sha384-egYe2iLG/VUblwMVWC7scltVz2CuhgfU0q4mfHYmtuemlb5VSNAyNCpMxbH5uLxJ" crossorigin="anonymous">
</script>
```

### Further Reading ###

* [HTML spec on scripting][scripting]

Optimizations and Enhancements
------------------------------

### Prefetching and Prerendering ###

`<meta http-equiv="x-dns-prefetch-control" content="on" />`

* [prefetch][]: prefetch resource for **future** page
* subresource: higher priority than prefetch for **current** page
* [prerender][]: prerender future page in background
* [dns-prefetch][]: advance DNS lookup for **current** page

#### Others ####

* [preconnect][]: start connection handshake early
* preload: forced prefetching

#### Examples ####

Place your pre-* tags at the very top, preface them with `http-equiv="x-dns-prefetch-control"`, and group them together based on URIs.

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta http-equiv="x-dns-prefetch-control" content="on" />
        <link rel="dns-prefetch" href="//fonts.gstatic.com" />
        <link rel="preconnect" href="//fonts.gstatic.com" crossorigin />
        <link rel="dns-prefetch" href="//brick.a.ssl.fastly.net" />
        <link rel="preconnect" href="//brick.a.ssl.fastly.net" crossorigin />
```

#### Further Reading ###

1. [Preconnect, prefetch, prerender ...
][pre-slides]
    - [This chart][pre-chart] explains it particularly well.
2. [Prefetching, preloading, prebrowsing][pre-css]

### `next` and `prev` ###

Remember to use `<link rel="next" />` and `<link rel="prev" />`, if there is a sequential relation between two of your pages.

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


[rfc3986]: //tools.ietf.org/html/rfc3986#section-3
[link-text]: //www.w3.org/QA/Tips/noClickHere
[hreflang]: https://support.google.com/webmasters/answer/189077?hl=en
[srihash.org]: https://srihash.org
[a-d]: //stackoverflow.com/a/10731231
[scripting]: https://html.spec.whatwg.org/#scripting-2
[prefetch]: //caniuse.com/#feat=link-rel-prefetch
[prerender]: //caniuse.com/#feat=link-rel-prerender
[dns-prefetch]: //caniuse.com/#search=dns-prefetch
[preconnect]: //caniuse.com/#feat=link-rel-preconnect
[pre-slides]: https://docs.google.com/presentation/d/18zlAdKAxnc51y_kj-6sWLmnjl6TLnaru_WH0LJTjP-o/present?slide=id.p19
[pre-chart]: https://docs.google.com/presentation/d/18zlAdKAxnc51y_kj-6sWLmnjl6TLnaru_WH0LJTjP-o/present?slide=id.gc03305a_0106
[pre-css]: https://css-tricks.com/prefetching-preloading-prebrowsing/
[iso]: https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes
