Style Guide
===========
[![Build Status](https://travis-ci.org/ndarville/style.svg)](https://travis-ci.org/ndarville/style) [![Dependency Status](https://gemnasium.com/ndarville/style.svg)](https://gemnasium.com/ndarville/style) [![devDependency Status](https://david-dm.org/ndarville/style/dev-status.svg)](https://david-dm.org/ndarville/style#info=devDependencies)

A list of styles for different linters.

If you want an example project, check out [Hafnia Times][].

Overview of Packages for Each Language
--------------------------------------
 Format   | Linter
:---------|:-----------------------------------------
 SASS     | `gem install scss-lint`
 CSS      | `npm install csslint`
 JS       | `npm install jscs && npm install jshint`
 Markdown | `gem install mdl`
 Python   | `pip install pep8`
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
wget https://raw.githubusercontent.com/ndarville/style/master/sass/.scss-lint.yml
wget https://raw.githubusercontent.com/ndarville/style/master/css/.csslintrc
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

### Linters ###
* [SublimeLinter-scss-lint](https://github.com/attenzione/SublimeLinter-scss-lint)
* [SublimeLinter-jscs](https://github.com/SublimeLinter/SublimeLinter-jscs)
* [SublimeLinter-jshint](https://github.com/SublimeLinter/SublimeLinter-jshint)
* [SublimeLinter-html-tidy](https://github.com/SublimeLinter/SublimeLinter-html-tidy)
* [SublimeLinter-contrib-write-good](https://github.com/ckaznocha/SublimeLinter-contrib-write-good/)
* (Python)
* (SublimeLinter-contrib-govet)
* (SublimeLinter-contrib-golint)

#### A Note on CSS ####
I have left out [SublimeLinter-csslint](https://github.com/SublimeLinter/SublimeLinter-csslint), because:

* It only works on CSS files; when used with HTML files, it mistakenly lints JavaScript and returns some wrong errors.
* It does not support CSS specific to SVG.

You are better off writing your CSS in SASS and linking externally to the compiled CSS file.

Linter Rules
------------
* [`sass-lint`](https://github.com/causes/scss-lint/blob/master/lib/scss_lint/linter/README.md)
* css
* [`jscs`](http://jscs.info/rules)
* [`jshint`](http://jshint.com/docs/options)
* [`tidy`](http://www.html-tidy.org/quickref)
* [`mdl`](https://github.com/mivok/markdownlint/blob/master/docs/RULES.md)
* (pep8)
* (golint)
* (govet)

Status
------
- [x] SASS linter
- [x] JavaScript linter
    - [x] jscs
    - [x] jshint
- [x] HTML (tentative)
- [ ] Python linter
- [ ] Go linter
    - [ ] golint
    - [ ] govet
- [ ] Markdown linter
    - [x] mdl
    - [ ] Personal linter

Related Services
----------------
- [linthub](https://linthub.io). Automates linting for pull requests.


[Hafnia Times]: https://github.com/ndarville/style
