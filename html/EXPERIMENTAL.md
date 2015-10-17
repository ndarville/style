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

### `@font-face` ###

```scss
@font-face {
    font-family: "EB Garamond;
    font-style: normal;
    font-weight: 400;
@if $avoid-local-font == true {
    src: local("☺"︎),
} @else {
    // PostScript font name for Safari `local`
    // Full font name for rest
    src: local("EB Garamond"), local("EBGaramond"),
}
         url("EBGaramond12-Regular.eot?"), format("eot");  // "?" for IE
         url("EBGaramond12-Regular.ttf"), format("truetype"),
         url("EBGaramond12-Regular.woff2") format("woff2"),
         url("EBGaramond12-Regular.woff") format("woff");
    unicode-range:
        U+0061-007A, // a-z
        U+0041-005A, // A-Z
        U+002D;      // -
```


[18F on tables]: https://playbook.cio.gov/designstandards/tables/
[mdn]: https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_button_role
[csstricks-buttons]: https://css-tricks.com/use-button-element
[davidwalsh-buttons]: http://davidwalsh.name/html5-buttons
[fontface-syntax]: http://www.paulirish.com/2009/bulletproof-font-face-implementation-syntax/
