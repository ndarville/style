Style Guide for Markdown
========================

* [Elements][]
    - [Links][]
    - [`<pre>`][pre]
    - [Unordered Lists][ul]
    - [Horizontal Rules][hr]
    - [Headers][]
* [Notes][]


[elements]: https://github.com/ndarville/style/tree/master/markdown#elements
[links]: https://github.com/ndarville/style/tree/master/markdown#links
[pre]: https://github.com/ndarville/style/tree/master/markdown#pre
[ul]: https://github.com/ndarville/style/tree/master/markdown#unordered-lists
[hr]: https://github.com/ndarville/style/tree/master/markdown#horizontal-rules
[headers]: https://github.com/ndarville/style/tree/master/markdown#headers
[notes]: https://github.com/ndarville/style/tree/master/markdown#notes


Elements
--------

Element   | Right       | Wrong
----------|-------------|----------
Emphasis  | `**Foo**`   | `_Foo_`
Strong    | `*Foo**`    | `__Foo__`
Footnote* | `Foo[^bar]` | `Foo[^1]`

([Footnote-syntax support][fn-support].)

### Links ###

Links are straightforward, but follow these guidelines:

* Use the `[Foo][]` shorthand whenever convenient, as it eschews cruft.
* Use the `[Foo][bar]` syntax in the remaining cases, when it improves readability.
* Do not leave empty lines between list items, except for nested lists.
* Leave two empty lines above the link definitions:

    ```md
    Lorem ipsum dolor sit [amet][].


    [amet]: http://example.com
    ```

([Syntax support][link-support].)

### `<pre>` ###

* Use backticks, `, not tildes, ~.
* Use them regardless of whether you apply syntax-highlighting; do not indent.

([Syntax support][pre-support].)

### Unordered Lists  ###

Use `*` for the first level:

```md
* Foo
```

Not

```md
- Foo
+ Bar
```

Deeper levels are up to the writer and can be situational. I tend to use `-` for the first sublevel.

([Syntax support][ul-support].)

### Horizontal Rules ###

```md
* * * *
```

Do not use any other characters, nor should there be fewer or more asterisks than shown.

([Syntax support][hr-support].)

### Headers ###

Right:

```md
Heading 1
=========

Heading 2
---------

### Heading 3 ###
```

Wrong:

```md
# Heading 1 #

## Heading 2 ##

### Heading 3 ###
```

Always add hashes on both sides of the heading, not just the left.

Right:

```md
### Heading ###
#### Heading ####
##### Heading #####
```

Wrong:

```md
### Heading
#### Heading
##### Heading
```

([Syntax support][header-support].)

Notes
-----
*The footnote syntax is a part of Markdown Extra, not vanilla Markdown. Use vanilla syntax in the cases where Markdown Extra is not available.


[fn-support]: http://johnmacfarlane.net/babelmark2/?normalize=1&text=Foo%5B%5Ebar%5D.%0A%0ABaz%5B%5E1%5D.%0A%0A%5B%5Ebar%5D%3A+This+is+the+preferred+footnote+syntax.%0A%5B%5E1%5D%3A+This+is+the+better-sypported+footnote+syntax.
[link-support]: http://johnmacfarlane.net/babelmark2/?normalize=1&text=%5BFoo%5D%5B%5D%0A%0A%5BBar%5D%5Bbaz%5D%0A%0A%0A%5Bfoo%5D%3A+http%3A%2F%2Fexample.com%2F1%2F%0A%5Bbaz%5D%3A+http%3A%2F%2Fexample.com%2F2%2F
[pre-support]: http://johnmacfarlane.net/babelmark2/?normalize=1&text=%60%60%60%0ALorem+ipsum%0A%60%60%60%0A%0A%60%60%60md%0ALorem+**ipsum**.%0A%60%60%60
[ul-support]: http://johnmacfarlane.net/babelmark2/?normalize=1&text=*+Foo%0A*+Bar%0A++++-+Baz%0A*+Qux
[hr-support]: http://johnmacfarlane.net/babelmark2/?normalize=1&text=*+*+*+*
[header-support]: http://johnmacfarlane.net/babelmark2/?normalize=1&text=Foo%0A%3D%3D%3D%0A%0ABar%0A---%0A%0A%23%23%23+Baz+%23%23%23%0A%23%23%23%23+Qux+%23%23%23%23%0A%23%23%23%23%23+Quux+%23%23%23%23%23
