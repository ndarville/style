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

# Download linter rules
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
* (Python)

Status
------
- [x] JavaScript linter
- [ ] SASS linter
- [ ] Python linter


[hafnia]: https://github.com/hafniatimes/hafniatimes.github.io
