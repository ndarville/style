Style Guide for Markdown
========================

Elements
--------

Element   | Right       | Wrong
----------|-------------|----------
Emphasis  | `**Foo**`   | `_Foo_`
Strong    | `*Foo**`    | `__Foo__`
Footnote* | `Foo[^bar]` | `Foo[^1]`

### `<pre>` ###

* Use backticks, `, not tildes, ~.
* Use them regardless of whether syntax-highlighting is applied; do not indent.

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
