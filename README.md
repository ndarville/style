Style Guide
===========
[![Build Status][]](https://travis-ci.org/ndarville/style) [![Dependency Status][]](https://gemnasium.com/ndarville/style) [![devDependency Status][]](https://david-dm.org/ndarville/style#info=devDependencies)

A list of styles for different linters.

If you want an example project, check out [Hafnia Times][].

Overview of Packages for Each Language
--------------------------------------
 Format   | Linter
:---------|:-----------------------------------------
 HTML     | `npm install htmlhint` && `brew install tidy-html5`
 CSS/SASS | `npm install stylelint`
 JS       | `npm install jscs && npm install jshint`
 Markdown | `gem install mdl`
 Python   | `pip install pep8`
 CSV      | `gem install csvlint`
 Shell    | `brew install shellcheck`
 YAML     | `gem install kwalify`
 Go       | `go get -u github.com/golang/lint/golint`

Installation
------------
First, install the packages. You can do this using the command line like so:

```sh
# ( Go to the root of your project; code for doing this not included )

# Instal Ruby packages
wget https://raw.githubusercontent.com/ndarville/style/master/Gemfile
bundle install

# Install NPM packages
npm install ndarville/style

# Install Python packages
wget https://raw.githubusercontent.com/ndarville/style/master/requirements.txt

# Install Go packages
go get -u github.com/golang/lint/golint

# Download linter rules to your project folder
wget https://raw.githubusercontent.com/ndarville/style/master/html/.htmlhintrc
wget https://raw.githubusercontent.com/ndarville/style/master/html/.tidyrc
wget https://raw.githubusercontent.com/ndarville/style/master/css/.stylelintrc
wget https://raw.githubusercontent.com/ndarville/style/master/javascript/.jscsrc
wget https://raw.githubusercontent.com/ndarville/style/master/javascript/.jshintrc
wget https://raw.githubusercontent.com/ndarville/style/master/python/.pep8
wget https://raw.githubusercontent.com/ndarville/style/master/markdown/.mdlrc
```

To install tidy  the HTML5 linter, which is only tentatively supported for now:

```sh
brew tap homebrew/dupes
brew install homebrew/dupes/tidy --HEAD
wget https://raw.githubusercontent.com/ndarville/style/master/html/.tidyrc
tidy -config .tidyrc
```

Afterwards, download the required Sublime Text 3 packages:

Sublime Text Packages
---------------------
* Package Control
* Bracket Highlighter
* SCSS
* SublimeLinter
* GitCommitMsg
* Modific
* Emmet
* cobalt2
* Markdown Extended
* Advanved CSV
* Babel
* Autoprefixer
* [GhostText][]
* Git
* ColorConvert

### Linters ###

* [SublimeLinter-contrib-stylelint][]
* [SublimeLinter-jscs][]
    - [JSCS-Formatter][]
* [SublimeLinter-jshint][]
* [SublimeLinter-contrib-htmlhint][]
* [SublimeLinter-html-tidy][]
* [SublimeLinter-contrib-write-good][]
* [SublimeLinter-pep8][]
* [SublimeLinter-shellcheck][]
* (SublimeLinter-contrib-govet)
* (SublimeLinter-contrib-golint)

`jscs` now has [auto-fixing support][jscs-formatter]. You can using by either running the command with the `-x` option or by installing the ST3 jscs-formatter listed above.

Linter Rules
------------
* [stylelint][]
* [jscs][]
* [jshint][jshint]
* [tidy][]
* [mdl][]
* [pep8][pep8]
* (golint)
* (govet)

Continuous Integration (CI)
---------------------------
* [Travis CI][]
* [Percy][]
* [Linthub][]
* [Hound][]

Status
------
- [x] SASS/CSS linter
- [x] JavaScript linter
    - [x] jscs
    - [x] jshint
- [x] HTML (tentative)
- [x] Python linter
- [x] CSV linter
- [ ] Go linter
    - [ ] golint
    - [ ] govet
- [ ] Markdown linter
    - [x] mdl
    - [ ] Personal linter
- [x] Shell linter
- [x] YAML linter

Examples
--------
My website [ndarville.com][] and project at [Hafnia Times][] try to conform to the style guidelines. The latter is open source, which makes it easier for you to inspect the code.


[Build Status]: https://travis-ci.org/ndarville/style.svg
[Dependency Status]: https://gemnasium.com/ndarville/style.svg
[devDependency Status]: https://david-dm.org/ndarville/style/dev-status.svg

[Hafnia Times]: https://github.com/ndarville/style
[ghosttext]: http://christiannaths.com/#code-pen-plus-sublime-text

[SublimeLinter-contrib-stylelint]: https://github.com/kungfusheep/SublimeLinter-contrib-stylelint
[SublimeLinter-jscs]: https://github.com/SublimeLinter/SublimeLinter-jscs
[JSCS-Formatter]: https://github.com/TheSavior/SublimeJSCSFormatter
[SublimeLinter-jshint]: https://github.com/SublimeLinter/SublimeLinter-jshint
[SublimeLinter-contrib-htmlhint]: https://github.com/mmaday/SublimeLinter-contrib-htmlhint
[SublimeLinter-html-tidy]: https://github.com/SublimeLinter/SublimeLinter-html-tidy
[SublimeLinter-contrib-write-good]: https://github.com/ckaznocha/SublimeLinter-contrib-write-good
[SublimeLinter-pep8]: https://github.com/SublimeLinter/SublimeLinter-pep8
[SublimeLinter-shellcheck]: https://github.com/SublimeLinter/SublimeLinter-shellcheck

[jscs-formatter]: https://github.com/jscs-dev/node-jscs/releases/tag/v1.12.0

[stylelint]: http://stylelint.io/user-guide/rules/
[jscs]: http://jscs.info/rules
[jshint]: http://jshint.com/docs/options
[tidy]: http://www.html-tidy.org/quickref
[mdl]: https://github.com/mivok/markdownlint/blob/master/docs/RULES.md
[pep8]: https://www.python.org/dev/peps/

[travis ci]: https://travis-ci.org
[percy]: https://percy.io
[linthub]: https://linthub.io
[hound]: https://houndci.com

[ndarville.com]: https://ndarville.com
