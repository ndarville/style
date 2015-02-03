Style Guide
===========
[![Dependency Status](https://gemnasium.com/ndarville/style.svg)](https://gemnasium.com/ndarville/style) [![devDependency Status](https://david-dm.org/ndarville/style/dev-status.svg)](https://david-dm.org/ndarville/style#info=devDependencies)

A list of styles for different linters.

If you want an example project, check out [Hafnia Times][hafnia].

Overview of Packages for Each Language
--------------------------------------
 Format | Linter
:-------|:-----------------------------------------
 CSS    | `npm install csslint`
 SASS   | `gem install scss-lint`
 JS     | `npm install jscs && npm install jshint`
 Python | `pip install pep8`

Installation
------------
First, install the packages. You can do this using the command line like so:

```sh
# ( Go to the root of your project; code for this not included )

# Instal Ruby packages
$ curl https://raw.githubusercontent.com/ndarville/style/master/Gemfile > Gemfile
$ bundle install

# Install NPM packages
$ npm install ndarville/style

# Install Python packages
$ curl https://raw.githubusercontent.com/ndarville/style/master/requirements.txt > requirements.txt

# Download linter rules to your project folder
$ curl https://raw.githubusercontent.com/ndarville/style/master/js/.jscsrc > .jscsrc
$ curl https://raw.githubusercontent.com/ndarville/style/master/sass/.scss-lint.yml > .scss-lint.yml
$ curl https://raw.githubusercontent.com/ndarville/style/master/python/.pep8 > .pep8
```

Afterwards, download the required Sublime Text 3 packages:

Sublime Text Packages
---------------------
* Package Control
* Bracket Highlighter
* SCSS
* SublimeLinter

### Linters ###
* [SublimeLinter-scss-lint](https://github.com/attenzione/SublimeLinter-scss-lint)
* [SublimeLinter-jscs](https://github.com/SublimeLinter/SublimeLinter-jscs)
* (SublimeLinter-jshint)
* (Python)

Linter Rules
------------
* [`sass-lint`](https://github.com/causes/scss-lint/blob/master/lib/scss_lint/linter/README.md)
* [`jscs`](http://jscs.info/rules)
* [`jshint`](http://jshint.com/docs/options/)
* (pep8)

Status
------
- [ ] JavaScript linter
    - [x] jscs
    - [ ] jshint
- [x] SASS linter
- [ ] Python linter


[hafnia]: https://github.com/hafniatimes/hafniatimes.github.io
