Testing for JavaScript
======================
As of now, the best testing framework for JavaScript is probably [Jest][].

Install Jest with `npm install jest`. Yarn doesn’t appear to work with `yarn add jest` as of this writing.

Yarn test files follow the naming convention of either

* `foo.test.js`
* `foo.spec.js`

The files go in the directory `__tests__/`:

* `__tests__/foo.test.js`
* `__tests__/foo.spec.js`

You can redefine the directory with `"testRegex"` in the Jest config.

Simply run the tests with `jest`.

You can see an example of Jest tests in my [Robotto][] repo; it’s hard to emphasize how straightforward Jest is.

Config
------
Your Jest config is either defined in `package.json` under `{ jest: "" }` or as a separate config JSON file defined with `--config`. The code examples will use the former approach.

Coverage testing
----------------
Jest also does coverage testing with the `--coverage` flag:

```sh
$ jest --coverage
```

You can also specify it in your config:

```json
{
    "jest": {
        "collectCoverage": true
    }
}
```

To specify a directory for coverage testing, define a glob in `package.json`:

```json
{
    "jest": {
        "collectCoverageFrom": [
            "static/js/*.{js,jsx}",
            "!**/lib/**.{js,jsx}",
            "!**/node_modules/**"
        ]
    }
}
```

Snapshots
---------
(...)

Snapshots are stored in `__tests__/__snapshots__/` by default.

Usage with Node
---------------
If you’re using Jest with node, add the following to `package.json`:

```json
{
    "jest": {
        "testEnvironment": "node"
    }
}
```

The default is `"jsdom"`.


[jest]: http://facebook.github.io/jest/
[robotto]: https://github.com/ndarville/starter-node-bot/tree/master/__tests__
