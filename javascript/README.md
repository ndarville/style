Style Guide for JavaScript
==========================

Comments
--------

### Headers ###

```js
// Section A
// =========
var foo = bar;
```

### Documentation ###

```js
// This explains and clarifies what the next piece of code does
function foo(bar) { print "baz"; }
```

### Multi-line ###

```js
/**
 *  Lorem ipsum dolor sit amet, consectetur adipiscing elit.
 *  Phasellus semper pharetra magna, non gravida tellus consectetur non.
 */
```

Optimizations
-------------

### `visibilitychange` ###

Pause redrawing and polling in a background tab with this:

```js
var doVisualUpdates = true;

document.addEventListener("visibilitychange", function() {
    doVisualUpdates = !document.hidden;
});
```

To use this in react, check out [react-user-focus][].


[react-user-focus]: https://github.com/Skilgarriff/react-user-focus
