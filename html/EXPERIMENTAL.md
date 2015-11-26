Experimental HTML Guidelines
============================

Tables
------
> * <mark>Simple tables can have two levels of headers. Each header cell should have `scope="col"` or `scope="row"`.</mark>
> * Complex tables are tables with more than two levels of headers. Each header should be given a unique id and each data cell should have a headers attribute with each related header cell’s id listed.

- [18F on tables][]

Buttons
-------
`<a href="#" role="button">Submit</a>`

vs

`<button role="button">Submit</button>`

vs

`<input type="submit" value="Submit" role="button" />`

Button and input elements are interchangeable, but anchor tags are a different matter, writes [MDN][]:

> Warning: Be careful when marking up links with the button role. Buttons are expected to be triggered using the Space key, while links are expected to be triggered through the Enter key. In other words, when links are used to behave like buttons, adding role="button" alone is not sufficient. It will also be necessary to add a key event handler that listens for the Space key in order to be consistent with native buttons.

Use input elements by defaults and use buttons for a separate purpose or behaviour.

* ["When To Use The Button Element"][csstricks-buttons]
* ["The Difference Between Anchors, Inputs and Buttons"][davidwalsh-buttons]

Typefaces
---------

### Performance and Optimization ###

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

This defeats **FOIT** (see below) by loading the fallback fonts first and then applying the custom fonts, once they’ve finished downloading.

#### External Loading ####

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

#### Local Loading ####

Or load them locally using [localfont.com][].

```html
<!-- Delay download of font until document is loaded -->
<link rel="stylesheet" type="text/css" href="/static/typefaces/css/fonts.css" media="deferred" onload="if(media!='all')media='all'" />
<noscript><link rel="stylesheet" type="text/css" href="/static/typefaces/css/fonts.css" media="all" /></noscript>
```

#### What’s with the Media Type? ####

It defers the downloading (ie blocking) of the fonts, until the page has finished loading. That way, the fonts won’t block the rendering of the page; fonts are often the bottleneck in loading a page.

This solution will result in, brief, FOUT (see below), but between FOIT and FOUT, the latter is preferable, unless the target audience always uses a high-speed Internet connection.

### `@font-face` Example ###

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
         local("EBGaramond"),
}
         url("EBGaramond12-Regular.eot?") format("eot"),  // "?" for IE
         url("EBGaramond12-Regular.ttf") format("truetype"),
         url("EBGaramond12-Regular.woff2") format("woff2"),
         url("EBGaramond12-Regular.woff") format("woff");
    unicode-range: // Optional for limiting characters
        U+0061-007A, // a-z
        U+0041-005A, // A-Z
        U+002D;      // -
```

Read more about this and *all the many caveats* in [“Bulletproof `@font-face` syntax”][fontface-syntax] by Paul Irish.

### FOUT, FOIT, FOFT ###

Flash of text that is:

* unstyled
* invisible
* faux

Learn more about at this [GitHub issue about the travails of font loading and rendering][font-issue].


[18F on tables]: https://playbook.cio.gov/designstandards/tables/
[mdn]: https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_button_role
[csstricks-buttons]: https://css-tricks.com/use-button-element
[davidwalsh-buttons]: http://davidwalsh.name/html5-buttons
[Font Face Observer]: https://github.com/bramstein/fontfaceobserver
[localfont.com]: http://www.localfont.com
[preconnecting]: https://github.com/ndarville/goal-tracker/issues/5
[fontface-syntax]: http://www.paulirish.com/2009/bulletproof-font-face-implementation-syntax/
[font-issue]: https://github.com/ndarville/goal-tracker/issues/3
