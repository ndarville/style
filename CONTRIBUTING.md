Contributing
============

General Guidelines
------------------
1. Limit your pull requests to a single issue.

    I consider this a guideline more than law of the land. There will probably be exceptions where it makes sense to bundle related issues, but keep this guideline in mind as a rule of thumb.

    When filing a pull request, keep the following in mind, too:

2. Limit your commits to a single type of improvement:

    To reapply rule #1 to commits and not just pull requests, do not merge commits with different purposes such as spelling, newline, whitespace corrections, as well as any other improvements.

    This also improves the quality of your commits significantly.

    Generally, it is better to submit your changes in a *single* commit. If you know your git, you should [squash][] several commits into a single one. This way, it will be much more manageable for everyone.

    To all rules there are exceptions, though.

3. Include screenshots, whenever relevant.

    Use [GitHub’s built-in image attachment system][github-images] instead of services like Imgur and Minus.

Issues
------
There is a well-known problem when it comes to submitting an issue for a project:

* On one hand, you should be as elaborate and exhaustive as possible, as this will make the very busy maintainers more likely to take your feedback to heart. (Screenshots! Error log! Programming environment!)
* On the other hand, if your issue gets rejected—or worse, ignored—your frustration will be compounded by the amount of work you put into writing your issue.

Fundamentally, issues should be elaborate, unless their point is succinct and borderline obvious. Issues don’t just exist for maintainers; they also exist for other users who may have thoughts and problems similar to yours, and issues are one way for them to explore their ideas without consulting with the maintainers directly.

If not for the maintainers, put some work into writing good issues, and please consider going back to your issue, if you solve a problem addressed in your original issue. That way, you’ll also help those in a situation similar to yours.

I’ve personally tried reaching out to GitHub to ask them about whether they wanted to tap into GitHub Issues’s potential to compete with StackOverflow, but they never got back to me. That shouldn’t stop us from helping users by writing great issues, though.

Pull Requests
-------------
If your submitted build fails, it is expected that you will amend the error—assuming you are able—to expedite the process.

Please, pretty please, write *descriptive*, *succinct* commit messages with appropriate spelling and capitalization of the first letter when applicable.

If you submit a bug fix for, say, consider writing a unit test that would have detected it in the first place, if the project supports unit tests that is.

Pedantic Style Guidelines
-------------------------
1. End all files in a newline. Exceptions are files where it affects the execution:
    * `.txt` files

2. Line endings must be Unix line endings.

3. Tabs must be four characters of space in the following filetypes:
    * `.py`
    * `.html`
    * `.txt`
    * `.markdown`, `.mdown`, `.md`
    * `sh` scripts
    * `.css`
    * `.scss`
    * `.js`
    * `.json`

4. Use double quotes instead of single quotes, both for code and English.

5. Avoid lines longer than 78 characters as a rule of thumb.

In general writing, I use my own [variant of the Oxford style][style].

I only mention this to pre-empt annoying pull requests for asinine corrections. It is not something you should concern yourself with when contributing.

### Sublime Text ###

If you use Sublime Text as an editor, you can adjust your settings to conform with the Pedantic Style Guidelines:

#### Conforming with `1` ####

```js
"trim_trailing_white_space_on_save": true,
"ensure_newline_at_eof_on_save": true
```

This makes your code fit the guideline automatically, and removes the need to worry about cleaning up your code and complying with the Pedantic Style Guidelines.

There is a rub, though; you have to turn off `"ensure_newline_at_eof_on_save"` when editing the files exempt from the newline rule. I’ll leave you to figure out that part for now; it involves adding `"ensure_newline_at_eof_on_save": true` to the “Syntax Specific” settings.

#### Conforming with `2` ####

```js
"default_line_ending": "unix"
```

#### Conforming with `3` ####

```js
"tab_size": 4,
"translate_tabs_to_spaces": true
```

This will however *not* convert existing non-space tabs to space-based tabs. This should not be too much of a concern in an instance where you are editing the code of this project, though.

You can find my own full [Sublime Text configuration inside my Style repo][sublime-text].

Sublime Text can also be configured to automatically follow many of the guidelines below using the instructions on the [front page of the Style repo][repo].

### Git ###

* Must follow the [general Git guidelines][git].

### Markdown ###

* Must follow the [general Markdown guidelines][markdown].
* Must pass a check by `mdl` using the [`.mdlrc` linter rules][mdlrc].

### HTML ###

* Must follow the [general HTML guidelines][html].
* Must pass a check by `htmlhint` using the [`.htmlhintrc` linter rules][htmlhintrc].

### SASS ###

* Must pass a check by `scss-lint` using the [`.scss-lint.yml` linter rules][scss-lint].

### CSS ###

* Must pass a check by `csslint` using the [`.csslintrc` linter rules][csslintrc].

### JavaScript ###

* Must follow the [general JavaScript guidelines][javascript].
* Must pass a check by `jscs` using the [`.jscsrc` linter rules][jscsrc].
* Must pass a check by `jshint` using the [`.jshintrc` linter rules][jshintrc].

### Python ###

* Must pass a check by `pep8` using the [`.pep8` linter rules][pep8].

### Really?! ###

Really. But you don’t have to do those things by yourself in advance; it just has to be done, before the Pull Request can be accepted. This process can be automated to an extent with the help of tools like [linthub][] and Travis CI, but only to an extent.

These measures are to ensure that everything works and keeps working, and that that everyone is able to read and edit the code together—not to discourage people nor scare people with limited technical experience away.

Finally—and Most Important
--------------------------
Please don‘t take it personally, if your suggestion or contribution is rejected. This includes the tone of the rejection—not that there is any good way to phrase an issue or pull-request rejection.

Hopefully the tone in your rejection will be kind and civil, if very brief, but in the event that it isn’t, please assume that the response was written under the duress of a heavy workload and a steady stream of issues and pull requests that require a swift response that leaves little time for elaborate responses.


[squash]: http://gitready.com/advanced/2009/02/10/squashing-commits-with-rebase.html
[github-images]: https://github.com/blog/1347-issue-attachments
[style]: https://github.com/hafniatimes/hafniatimes.github.io/blob/master/STYLE.md
[sublime-text]: https://github.com/ndarville/style/blob/master/sublime-text/mac/Preferences.sublime-settings
[repo]: https://github.com/ndarville/style
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
