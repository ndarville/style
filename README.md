Style Guide
===========
[![Build Status][]](https://travis-ci.org/ndarville/style) [![Dependency Status][]](https://gemnasium.com/ndarville/style) [![devDependency Status][]](https://david-dm.org/ndarville/style#info=devDependencies)

A list of styles for different linters.

If you want an example project, check out [Hafnia Times][].

Overview of Packages for Each Language
--------------------------------------
 Format   | Linter
:---------|:--------------------------------------------
 HTML     | `npm install htmlhint && gem install html-proofer && brew install tidy-html5`
 CSS/SASS | `npm install stylelint stylefmt`
 JS       | `npm install standard`
 Markdown | `gem install markdownlint-cli`
 Python   | `pip install pep8`
 CSV      | `gem install csvlint`
 Shell    | `brew install shellcheck`
 YAML     | `gem install kwalify`
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

# Install NPM packages and download repo to node_modules/style
npm cache clean && npm install --silent ndarville/style

# Install Ruby packages
wget https://raw.githubusercontent.com/ndarville/style/master/Gemfile
bundle install

# Install Python packages
wget https://raw.githubusercontent.com/ndarville/style/master/requirements.txt
pip requirements -r requirements.txt

# Install Go packages
go get -u github.com/golang/lint/golint
```

```sh
# Download linter rules to your project folder
wget https://raw.githubusercontent.com/ndarville/style/master/html/.htmlhintrc
wget https://raw.githubusercontent.com/ndarville/style/master/html/.tidyrc
wget https://raw.githubusercontent.com/ndarville/style/master/css/.stylelintrc
wget https://raw.githubusercontent.com/ndarville/style/master/python/.pep8
wget https://raw.githubusercontent.com/ndarville/style/master/markdown/.markdownlintrc
```

### Download and Installation with `node_modules/` ###

```sh
# ( Go to the root of your project; code for doing this not included )

# Install NPM packages and download repo to node_modules/style
npm cache clean && npm install --silent ndarville/style

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
* Markdown Extended
* Advanced CSV
* Babel
* ColorConvert
* [GhostText][]
* SCSS
- Autoprefixer
* Git
- GitCommitMsg (Not supported by ST3, looks like)
- Modific

### Linters ###

* [SublimeLinter-contrib-stylelint][]
    - [sublime-stylefmt][]
* [SublimeLinter-contrib-htmlhint][]
* [SublimeLinter-html-tidy][]
* [SublimeLinter-contrib-standard][]
* [SublimeLinter-contrib-write-good][]
* [SublimeLinter-pep8][]
* [SublimeLinter-shellcheck][]
* (SublimeLinter-contrib-govet)
* (SublimeLinter-contrib-golint)

Linter Rules
------------
* [stylelint][]
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
[ghosttext]: http://christiannaths.com/#code-pen-plus-sublime-text

[SublimeLinter-contrib-stylelint]: https://github.com/kungfusheep/SublimeLinter-contrib-stylelint
[sublime-stylefmt]: https://github.com/dmnsgn/sublime-stylefmt
[SublimeLinter-contrib-standard]: https://packagecontrol.io/packages/SublimeLinter-contrib-standard
[SublimeLinter-contrib-htmlhint]: https://github.com/mmaday/SublimeLinter-contrib-htmlhint
[SublimeLinter-html-tidy]: https://github.com/SublimeLinter/SublimeLinter-html-tidy
[SublimeLinter-contrib-write-good]: https://github.com/ckaznocha/SublimeLinter-contrib-write-good
[SublimeLinter-pep8]: https://github.com/SublimeLinter/SublimeLinter-pep8
[SublimeLinter-shellcheck]: https://github.com/SublimeLinter/SublimeLinter-shellcheck

[stylelint]: http://stylelint.io/user-guide/rules/
[tidy]: http://www.html-tidy.org/quickref
[markdownlint]: https://github.com/DavidAnson/markdownlint#rules--aliases
[pep8]: https://www.python.org/dev/peps/

[travis ci]: https://travis-ci.org
[percy]: https://percy.io
[linthub]: https://linthub.io
[hound]: https://houndci.com

[ndarville.com]: https://ndarville.com
