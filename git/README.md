Style Guide for Git Commits
===========================

Messages
--------
* Capitalize
* Imperative verb
* No periods at the end
* Reference issue with `... cf. #123`
    - Some leave out the "cf.", but I like it for readability.
* Reference files/concepts with `xyz: ...`
    - Some demand commit start with a verb, but this can make readability hard, since people have to scan the second word in a commit.

Example:

> `README: change to British-English cf. #7`

1. Limit subject text to **50** characters
2. Limit body text to **72** characters
3. Use subject and body sections divided by a blank line
    - Use `CTRL + Shift + P` + `commit` from the Git package for this

I don’t think you should *always* lead with an imperative verb; ten commits in a row starting with “Add”, “Fix” or “Change” wreaks havoc on the readability of your commit log, as you’ll have to scan the second word in the messages. Rather, the rule is not to always use the imperative verb, but to use it in place of the past participle.

### Message Template ###

The template by Tim Pope is the standard; this is the one most people will go by:

    Short (50 chars or less) summary of changes

    More detailed explanatory text, if necessary.  Wrap it to
    about 72 characters or so.  In some contexts, the first
    line is treated as the subject of an email and the rest of
    the text as the body.  The blank line separating the
    summary from the body is critical (unless you omit the body
    entirely); tools like rebase can get confused if you run
    the two together.

    Further paragraphs come after blank lines.

      - Bullet points are okay, too

      - Typically a hyphen or asterisk is used for the bullet,
        preceded by a single space, with blank lines in
        between, but conventions vary here

Two dissents:

1. The double space after periods
2. The one-space indenation of lists

Basically write it as you would something in Markdown.

Inspection Commands
-------------------
* `git shortlog`
* `git log --oneline -5 --author ndarville`
* `git log --no-merges`

Grouping and Atomizing Commits
------------------------------
1. Atomize changes instead of grouping them into one commit. Think one issue per change.

    Learn to use `git add -p` (with `s` for splicing and `e` for manual picking).

2. Squash related commits into one.

Further Reading
---------------
* <http://chris.beams.io/posts/git-commit/>
