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

### `//` vs `https://` ###

Protocol-relative URLs (`//`) are now considered an antipattern. Use `https://` and `http://` instead.

* [Eric Mill on this][eric-mill]
* [Paul Irish][]

Link Text
---------
In accordance with [HTML Techniques for Web Content Accessibility Guidelines 1.0, Section 6.1][link-text].

**Do not** use `click here` as link text.

**Do not** use call-to-action verbs like `go to our page`.

Use the page or content your are linking to as the text instead.

### Bad ###

> [Click here] to visit GitHub.

### Also bad ###

> Click here to [visit GitHub].

### Good ###

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
* style

HTML5 Containers
----------------
Use HTML5 containers like

* `<main role="main">`
* `<header role="banner">`
* `<section role="region">`
* `<nav role="navigation">`
* `<footer role="contentinfo">`
* `<aside role="complementary">`

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
</nav>
```

Two significant differences between the two:

1. First, `ul#site-navigation` is replaced with `nav`.
2. Second, the navigation no longer contains list items, only links.

    The argument for this is that a screenreader will read the first case as

    > List item 1: Home; List item 2: About; List item 3: 404.

    Which is *way* too belaboured for a user. The latter example is better UX.

You can optionally wrap the links in `<span>`. You can also give the `<nav>` element an id.

Footnotes
---------
* Place footnote link for paragraphs *after* the fullstop, with a space
    - except if a sentence follows in the same paragraph.
* Be sure to namespace the footnote IDs, if several footnotes exist on the same page in different contexts, eg different blog posts on a front page.
* Wrap block footnotes in `<aside>`.

```html
The bad example implies a 100% certainty betrayed by factors like variance and methodology.<sup id="fn-link-1"><a href="#fn-text-1">1</a></sup>

<!--***-->

<aside role="complementary">
    <ol class="footnotes">
        <li><sup id="fn-text-1"><a href="#fn-link-1">1</a></sup> To gain a better understanding of all the caveats of conducting a poll and interpreting the results, check out the <a href="https://ndarville.com/projects/metapoll">Metapoll</a> project.</li>
    </ol>
</aside>
```

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

Figures
-------
`<figure>` is an easy way to wrap media, tables or lists contexually, especially for labelling purposes.

```html
<figure aria-labelledby="fig-cap1" role="group">
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
    <figcaption id="fig-cap1">Description.</figcaption>
</figure>
```

Alerts
------
> * Use the ARIA `role="alert"` to inform assistive technologies of a time-sensitive and important message that is not interactive. If the message is interactive, use the `alertdialogue` role instead.

- [18F on alerts][]

Forms
-----
Always use `for` in `<label>` and `id` in `<input>`. When sending data to a webserver, include `name` in your `<input>`.

> * All form control tags should have an associated label.
> * Any additional information—such as required, optional, or example text—should be wrapped within the label tags. For example: <label for="name">Favorite Pie <span>Optional</span></label>. This way screen readers know what additional information is related to each field.

Use [aria-describedby][] for error messages.

> * <mark>Avoid placeholder text for accessibility reasons. Most browsers’ default rendering of placeholder text does not provide a high enough contrast ratio.</mark>
> * Avoid breaking numbers with distinct sections (such as phone numbers, Social Security Numbers, or credit card numbers) into separate input fields. For example, use one input for phone number, not three (one for area code, one for local code, and one for number). Each field needs to be labeled for a screen reader and the labels for fields broken into segments are often not meaningful.

Choose input type based on the size and length of input; in ascending order:

* Radio
* Checkbox
* Dropdown (options)
* Text input with autocomplete (eg `<datalist>`)

> * When most users will (or should) pick a particular option, make it the default: `<option selected="selected">Default</option>`

### Checkboxes ###

>Surround a related set of checkboxes with a `<fieldset>`. The `<legend>` provides context for the grouping. Do not use fieldset and legend for a single check.

Think of `<legend>` as `<label>` for an input group.

> Avoid using negative language in labels as they can be counterintuitive.

- [18F on form controls][]

### Templates ###

> * Display form controls in the same order in HTML as they do on screen. Do not use CSS to rearrange the form controls. Screen readers narrate forms in the order they appear in the HTML.
> * Keep your form blocks in a vertical pattern. It’s an ideal approach for accessibility, due to limited vision that makes it hard to scan from right to left.
>
> * Leave the title and suffix fields as text boxes instead of offering drop downs. There are many possible titles and suffixes; text boxes accommodate them all.

- [18F on form templates][]

Scripts
-------
For externally loaded content, always use a checksum hash (`integrity` for scripts, ie **S**ub**r**esource **I**ntegrity Hash) and `crossorigin="anonymous"`. See [srihash.org][].

### `async` and `defer` ###

`defer` and `async` only work for `<script>` tags where `src` is defined.

The two boolean attributes exist to prevent blocking.

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
    src="https://buttons.github.io/buttons.js"
    async defer
    integrity="sha384-egYe2iLG/VUblwMVWC7scltVz2CuhgfU0q4mfHYmtuemlb5VSNAyNCpMxbH5uLxJ" crossorigin="anonymous">
</script>
```

### Further Reading ###

* [HTML spec on scripting][scripting]

Typefaces
---------

### `@font-face` CSS ###

```scss
@font-face {
    font-family: "EB Garamond";
    font-style: normal;
    font-weight: 400;
@if $avoid-local-font == true {
    src: local("☺"︎);
} @else {
    // PostScript font name for Safari `local`,
    // Full font name for rest
    src: local("EB Garamond"),
         local("EBGaramond");
}
    src: url("EB-Garamond-regular.eot"); // IE9 compat mode
    src: url("EB-Garamond-regular.eot?") format("embedded-opentype"), // "?" for IE6-IE8
         url("EB-Garamond-regular.ttf") format("truetype"),
         url("EB-Garamond-regular.woff2") format("woff2"),
         url("EB-Garamond-regular.woff") format("woff");
    unicode-range: // Optional for limiting characters
        U+0061-007A, // a-z
        U+0041-005A, // A-Z
        U+002D;      // -
```

Read more about this and *all the many caveats* in [“Bulletproof `@font-face` syntax”][fontface-syntax] by Paul Irish.

### Performance and Optimization ###

#### Defeating FOIT ####

Change your stylesheet from including the custom font that looks like so:

```css
body { font-family: "Raleway", "HelveticaNeue", "Helvetica Neue", Helvetica, Arial, sans-serif; }
```

To this:

```diff
- body { font-family: "Raleway", "HelveticaNeue", "Helvetica Neue", Helvetica, Arial, sans-serif; }
+ body { font-family: "HelveticaNeue", "Helvetica Neue", Helvetica, Arial, sans-serif; }
+ .fonts-loaded body { font-family: "Raleway", "HelveticaNeue", "Helvetica Neue", Helvetica, Arial, sans-serif; }
```

At the bottom of the HTML body, add the following using [Font Face Observer][]:

```html
<script type="text/javascript" src="/static/js/fontfaceobserver.js"></script>
<script type="text/javascript">
    var raleway300 = new FontFaceObserver("Raleway", {"weight": 300}),
        raleway400 = new FontFaceObserver("Raleway", {"weight": 400}),
        raleway600 = new FontFaceObserver("Raleway", {"weight": 600});

    Promise.all([
        raleway300.check(),
        raleway400.check(),
        raleway600.check()
    ]).then(function() {
        document.documentElement.className += "fonts-loaded";
    });
</script>
```

This defeats **FOIT** (see below) by loading the fallback fonts first and then applying the custom fonts, once, and only once, they’ve finished downloading.

#### Deferred Font Loading ####

##### External #####

Either retrieve web fonts from Google Fonts:

```html
<!-- Preconnect to external font -->
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<!-- Delay download of font until document is loaded -->
<link rel="stylesheet" type="text/css" href="https://fonts.googleapis.com/css?family=Raleway:300,400,600" media="deferred" onload="if(media!='all')media='all'" />
<noscript><link rel="stylesheet" type="text/css" href="https://fonts.googleapis.com/css?family=Raleway:300,400,600" media="all" /></noscript>
```

Just place the `preconnect` immediately before the font loading to parallelize the operation; little need to put it in the front.

* For more on [preconnecting][] with examples and data

You can explore using `dns-prefetch` as well.

##### Local #####

Or load them locally using [localfont.com][].

```html
<!-- Delay download of font until document is loaded -->
<link rel="stylesheet" type="text/css" href="/static/typefaces/css/fonts.css" media="deferred" onload="if(media!='all')media='all'" />
<noscript><link rel="stylesheet" type="text/css" href="/static/typefaces/css/fonts.css" media="all" /></noscript>
```

#### What’s with the Media Type? ####

It defers the downloading (ie blocking) of the fonts, until the page has finished loading. That way, the fonts won’t block the rendering of the page; fonts are often the bottleneck in loading a page.

This solution will result in, brief, FOUT (see below), but between FOIT and FOUT, the latter is preferable, unless the target audience always uses a high-speed Internet connection.

### FOUT, FOIT, FOFT ###

Flash of text that is:

* unstyled
* invisible
* faux

Learn more about at this [GitHub issue about the travails of font loading and rendering][font-issue].

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
        <link rel="dns-prefetch" href="https://fonts.gstatic.com" />
        <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
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
* If HTTPS: `property="og:image:secure_url" content="https://ndarville.com/hotlink-ok/image.png"`
* If HTTP: `property="og:image" content="https://ndarville.com/hotlink-ok/image.png"`
* `property="og:image:type" content="image/png"`
* `property="og:image:width" content="192"`
* `property="og:image:height" content="192"`

### Twitter (Optional) ###

* `name="twitter:creator" content="@pessimism"`
* `name="twitter:site" content="@HafniaTimes"`
* `name="twitter:description" content="A Danish publication in English promoting open data and transparency in tech and politics."`
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


[rfc3986]: https://tools.ietf.org/html/rfc3986#section-3
[eric-mill]: https://github.com/konklone/cdns-to-https
[Paul Irish]: http://www.paulirish.com/2010/the-protocol-relative-url/
[link-text]: http://www.w3.org/QA/Tips/noClickHere
[hreflang]: https://support.google.com/webmasters/answer/189077?hl=en
[18F on alerts]: https://playbook.cio.gov/designstandards/alerts/
[aria-describedby]: https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_aria-describedby_attribute
[18F on form controls]: https://playbook.cio.gov/designstandards/form-controls/
[18F on form templates]: https://playbook.cio.gov/designstandards/form-templates/
[srihash.org]: https://srihash.org
[a-d]: https://stackoverflow.com/a/10731231
[scripting]: https://html.spec.whatwg.org/#scripting-2
[fontface-syntax]: http://www.paulirish.com/2009/bulletproof-font-face-implementation-syntax/
[Font Face Observer]: https://github.com/bramstein/fontfaceobserver
[localfont.com]: http://www.localfont.com
[preconnecting]: https://github.com/ndarville/goal-tracker/issues/5
[font-issue]: https://github.com/ndarville/goal-tracker/issues/3
[prefetch]: https://caniuse.com/#feat=link-rel-prefetch
[prerender]: https://caniuse.com/#feat=link-rel-prerender
[dns-prefetch]: https://caniuse.com/#search=dns-prefetch
[preconnect]: https://caniuse.com/#feat=link-rel-preconnect
[pre-slides]: https://docs.google.com/presentation/d/18zlAdKAxnc51y_kj-6sWLmnjl6TLnaru_WH0LJTjP-o/present?slide=id.p19
[pre-chart]: https://docs.google.com/presentation/d/18zlAdKAxnc51y_kj-6sWLmnjl6TLnaru_WH0LJTjP-o/present?slide=id.gc03305a_0106
[pre-css]: https://css-tricks.com/prefetching-preloading-prebrowsing/
[iso]: https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes
