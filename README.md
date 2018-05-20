Style Guide
===========
[![Build Status][]](https://travis-ci.org/ndarville/style) [![Dependency Status][]](https://gemnasium.com/ndarville/style) [![devDependency Status][]](https://david-dm.org/ndarville/style#info=devDependencies)

A list of styles for different linters.

If you want an example project, check out [Hafnia Times][].

Overview of Packages for Each Language
--------------------------------------
 Format   | Linter
:---------|:--------------------------------------------
 HTML     | `yarn add htmlhint && gem install html-proofer && brew install tidy-html5`
 CSS/SASS | `yarn add stylelint stylefmt`
 JS       | `yarn add jscs jshint`
 Markdown | `gem install markdownlint-cli`
 Python   | `pip install pep8 glom`
 CSV      | `gem install csvlint && pip install csvkit`
 Shell    | `brew install shellcheck`
 YAML     | `gem install kwalify && pip install yq`
 Go       | `go get -u github.com/golang/lint/golint`

Notifications when the job finishes:

* [noti][]
* [ntfy][]

Installation
------------
Install the packages and download the linter rules using the command line:

### Direct Download and Installation (Recommended) ###

```sh
# ( Go to the root of your project; code for doing this not included )

# Install Node.js packages and download repo to node_modules/style
yarn cache clean && yarn --silent ndarville/style

# Install Ruby packages
wget https://raw.githubusercontent.com/ndarville/style/master/Gemfile
bundle install

# Install Python packages
wget https://raw.githubusercontent.com/ndarville/style/master/requirements.txt
pip install -r requirements.txt

# Install Go packages
go get -u github.com/golang/lint/golint
```

I prefer a pipsi and pipenv Python installation flow to pip’s:

```sh
# https://jacobian.org/writing/python-environment-2018/
# https://github.com/mitsuhiko/pipsi/issues/89
wget https://raw.githubusercontent.com/ndarville/style/master/Pipfile
pipenv install
```

```sh
# Download linter rules to your project folder
wget https://raw.githubusercontent.com/ndarville/style/master/html/.htmlhintrc
wget https://raw.githubusercontent.com/ndarville/style/master/html/.tidyrc
wget https://raw.githubusercontent.com/ndarville/style/master/css/.stylelintrc
wget https://raw.githubusercontent.com/ndarville/style/master/javascript/.jscsrc
wget https://raw.githubusercontent.com/ndarville/style/master/javascript/.jshintrc
wget https://raw.githubusercontent.com/ndarville/style/master/python/.pep8
wget https://raw.githubusercontent.com/ndarville/style/master/markdown/.markdownlintrc
```

### Download and installation with `node_modules/` ###

```sh
# ( Go to the root of your project; code for doing this not included )

# Install Node.js packages and download repo to node_modules/style
## Use yarn instead of npm, npm is a mess
## https://yarnpkg.com/lang/en/docs/migrating-from-npm/
yarn cache clean && yarn add ndarville/style # Used to be --silent in npm

# Install Ruby packages from node_modules/style
bundle install node_modules/style/Gemfile

# Install Python packages from node_modules/style
pip requirements -r node_modules/style/requirements.txt

# Install Go packages
go get -u github.com/golang/lint/golint
```

You can access the linter rules that were downloaded to

* `node_modules/style/master/html/.htmlhintrc`
    - `htmlhint --config node_modules/style/html/.htmlhintrc`
* `node_modules/style/master/html/.tidyrc`
* `node_modules/style/master/css/.stylelintrc`
    - `stylelint --config node_modules/style/css/.stylelintrc`
* `node_modules/style/master/javascript/.jscsrc`
    - `jscs --config node_modules/style/javascript/.jscsrc`
* `node_modules/style/master/javascript/.jshintrc`
    - `jshint --config node_modules/style/javascript/.jshintrc`
* `node_modules/style/master/python/.pep8`
    - `pep8 --config node_modules/style/python/.pep8`
* `node_modules/style/master/markdown/.markdownlintrc`
    - `markdownlint --config node_modules/style/markdown/.markdownlintrc`

### tidy ###

To install tidy, the HTML5 linter, which is only tentatively supported for now:

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
* SublimeLinter
* Bracket Highlighter
* Emmet
* cobalt2
* Advanced CSV
* [Siteleaf Liquid Syntax][liquid]
* Babel
* ColorConvert
* [GhostText][]
* SCSS
    - Autoprefixer
* Git
    - GitCommitMsg (not supported by ST3, looks like)
    - GitGutter
* INI
* [markdown-liquid-syntax][]
* HTML-CSS-JS-Prettify
* [sublimetext-Pandoc][]
* SublimePrettyJson
* [MarkdownEditing][]
    - Fixes default Markdown handling and highlighting

### Linters ###

* [SublimeLinter-contrib-stylelint][]
    - [sublime-stylefmt][]
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
* [markdownlint][]
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
    - [x] htmlhint
    - [x] htmlproofer
    - [ ] tidy
- [x] Python linter
- [x] CSV linter
- [ ] Go linter
    - [ ] golint
    - [ ] govet
- [ ] Markdown linter
    - [x] markdownlint
    - [ ] Personal linter
- [x] Shell linter
- [x] YAML linter

Examples
--------
My website [ndarville.com][] and project at [Hafnia Times][] try to conform to the style guidelines. The latter is open source, which makes it easier for you to inspect the code.


[Build Status]: https://travis-ci.org/ndarville/style.svg
[Dependency Status]: https://gemnasium.com/ndarville/style.svg
[devDependency Status]: https://david-dm.org/ndarville/style/dev-status.svg

[noti]: https://github.com/variadico/noti
[ntfy]: https://github.com/dschep/ntfy

[Hafnia Times]: https://github.com/ndarville/style
[liquid]: https://github.com/siteleaf/liquid-syntax-mode
[markdown-liquid-syntax]: https://github.com/ndarville/markdown-liquid-syntax
[ghosttext]: http://christiannaths.com/#code-pen-plus-sublime-text
[sublimetext-pandoc]: https://github.com/tbfisher/sublimetext-Pandoc
[markdownediting]: https://github.com/SublimeText-Markdown/MarkdownEditing

[SublimeLinter-contrib-stylelint]: https://github.com/kungfusheep/SublimeLinter-contrib-stylelint
[sublime-stylefmt]: https://github.com/dmnsgn/sublime-stylefmt
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
[markdownlint]: https://github.com/DavidAnson/markdownlint#rules--aliases
[pep8]: https://www.python.org/dev/peps/

[travis ci]: https://travis-ci.org
[percy]: https://percy.io
[linthub]: https://linthub.io
[hound]: https://houndci.com

[ndarville.com]: https://ndarville.com
