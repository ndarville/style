Experimental HTML Guidelines
============================

Tables
------
> * <mark>Simple tables can have two levels of headers. Each header cell should have `scope="col"` or `scope="row"`.</mark>
> * Complex tables are tables with more than two levels of headers. Each header should be given a unique id and each data cell should have a headers attribute with each related header cell’s id listed.

- [18F on tables][]

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
[fontface-syntax]: http://www.paulirish.com/2009/bulletproof-font-face-implementation-syntax/
