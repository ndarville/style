Contributing
============

Git
---
* Must follow the [general Git guidelines][git].

Markdown
--------
* Must follow the [general Markdown guidelines][markdown].
* Must pass a check by `mdl` using the [`.mdlrc` linter rules][mdlrc].

HTML
----
* Must follow the [general HTML guidelines][html].
* Must pass a check by `htmlhint` using the [`.htmlhintrc` linter rules][htmlhintrc].

SASS
----
* Must pass a check by `scss-lint` using the [`.scss-lint.yml` linter rules][scss-lint].

CSS
---
* Must pass a check by `csslint` using the [`.csslintrc` linter rules][csslintrc].

JavaScript
----------
* Must follow the [general JavaScript guidelines][javascript].
* Must pass a check by `jscs` using the [`.jscsrc` linter rules][jscsrc].
* Must pass a check by `jshint` using the [`.jshintrc` linter rules][jshintrc].

Python
------
* Must pass a check by `pep8` using the [`.pep8` linter rules][pep8].

Really?!
--------
Really. But you don’t have to do those things by yourself in advance; it just has to be done, before the Pull Request can be accepted. This process can be automated to an extent with the help of tools like [linthub][] and Travis CI, but only to an extent.

These measures are to ensure that everything works and keeps working, and that that everyone is able to read and edit the code together—not to discourage people nor scare people with limited technical experience away.


[git]: https://github.com/ndarville/style/blob/master/git/
[markdown]: https://github.com/ndarville/style/tree/master/markdown
[mdlrc]: https://github.com/ndarville/style/blob/master/markdown/.mdlrc
[html]: https://github.com/ndarville/style/tree/master/html
[htmlhintrc]: https://github.com/ndarville/style/blob/master/html/.htmlhintrc
[scss-lint]: https://github.com/ndarville/style/blob/master/sass/.scss-lint.yml
[csslintrc]: https://github.com/ndarville/style/blob/master/css/.csslintrc
[javascript]: https://github.com/ndarville/style/tree/master/javascript
[jscsrc]: https://github.com/ndarville/style/blob/master/javascript/.jscsrc
[jshintrc]: https://github.com/ndarville/style/blob/master/javascript/.jshintrc
[pep8]: https://github.com/ndarville/style/blob/master/python/.pep8
[linthub]: https://linthub.io
[travis ci]: https://travis-ci.org
