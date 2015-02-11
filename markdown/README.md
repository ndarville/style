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

### Links ###

Links are straightforward, but follow these guidelines:

* Use the `[Foo][]` shorthand whenever convenient, as it eschews cruft.
* Use the `[Foo][bar]` syntax in the remaining cases, when it improves readability.

### `<pre>` ###

* Use backticks, `, not tildes, ~.
* Use them regardless of whether you apply syntax-highlighting; do not indent.

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

Deeper levels are up to the writer and can be situational.

### Horizontal Rules ###

```md
* * * *
```

Do not use any other characters, nor should there be fewer or more asterisks than shown.

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

Notes
-----
*The footnote syntax is a part of Markdown Extra, not vanilla Markdown. Use vanilla syntax in the cases where Markdown Extra is not available.
