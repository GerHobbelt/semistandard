# JavaScript Semi-Standard Style
[![travis][travis-image]][travis-url]
[![npm][npm-image]][npm-url]
[![downloads][downloads-image]][downloads-url]
[![bitHound Dependencies](https://www.bithound.io/github/gtanner/semistandard/badges/dependencies.svg)](https://www.bithound.io/github/gtanner/semistandard/master/dependencies/npm)

### One Semicolon for the Dark Lord on his dark throne

All the goodness of [feross/standard] with semicolons sprinkled on top.


<h4 align="center">One Style to Rule Them All</h4>

<p align="center">
  <a href="https://travis-ci.org/feross/standard"><img src="https://travis-ci.org/feross/standard.svg?branch=master" alt="Travis"></a>
  <a href="https://www.npmjs.com/package/standard"><img src="https://img.shields.io/npm/dm/standard.svg" alt="npm downloads"></a>
  <a href="https://www.npmjs.com/package/standard"><img src="https://img.shields.io/npm/v/standard.svg" alt="npm version"></a>
</p>
<br>

No decisions to make. No `.eslintrc`, `.jshintrc`, or `.jscsrc` files to manage. It just
works.

This module saves you (and others!) time in two ways:

- **No configuration.** The easiest way to enforce consistent style in your project. Just
  drop it in.
- **Catch style errors before they're submitted in PRs.** Saves precious code review time
  by eliminating back-and-forth between maintainer and contributor.


## Install

```bash
npm install GerHobbelt/semistandard
```

## Rules

Importantly:

- **semicolons**
- Check [feross/standard] for the rest of the rules:

  - **2 spaces** – for indentation
  - **Single quotes for strings** – except to avoid escaping
  - **No unused variables** – this one catches *tons* of bugs!
  - **No semicolons** – [It's][1] [fine.][2] [Really!][3]
  - **Never start a line with `(` or `[`**
    - This is the **only** gotcha with omitting semicolons – *automatically checked for you!*
    - [More details][4]
  - **Space after keywords** `if (condition) { ... }`
  - **Space after function name** `function name (arg) { ... }`
  - Always use `===` instead of `==` – but `obj == null` is allowed to check `null || undefined`.
  - Always handle the node.js `err` function parameter
  - Always prefix browser globals with `window` – except `document` and `navigator` are okay
    - Prevents accidental use of poorly-named browser globals like `open`, `length`,
      `event`, and `name`.
  - **And [more goodness][5]** – *give `standard` a try today!*

[1]: http://blog.izs.me/post/2353458699/an-open-letter-to-javascript-leaders-regarding
[2]: http://inimino.org/~inimino/blog/javascript_semicolons
[3]: https://www.youtube.com/watch?v=gsfbh17Ax9I
[4]: RULES.md#semicolons
[5]: RULES.md#javascript-standard-style

To get a better idea, take a look at
[a sample file](https://github.com/feross/bittorrent-dht/blob/master/client.js) written
in JavaScript Standard Style, or check out some of
[the repositories](https://github.com/feross/standard-packages/blob/master/all.json) that use
`standard`.


## Badge

Use this in one of your projects? Include one of these badges in your readme to
let people know that your code is using the standard style.

[![js-semistandard-style](https://cdn.rawgit.com/flet/semistandard/master/badge.svg)](https://github.com/Flet/semistandard)

```markdown
[![js-semistandard-style](https://cdn.rawgit.com/flet/semistandard/master/badge.svg)](https://github.com/Flet/semistandard)
```

[![js-semistandard-style](https://img.shields.io/badge/code%20style-semistandard-brightgreen.svg?style=flat-square)](https://github.com/Flet/semistandard)

```markdown
[![js-semistandard-style](https://img.shields.io/badge/code%20style-semistandard-brightgreen.svg?style=flat-square)](https://github.com/Flet/semistandard)
```

## Usage

The easiest way to use JavaScript Semi-Standard Style to check your code is to install it
globally as a Node command line program. To do so, simply run the following command in
your terminal (flag `-g` installs `semistandard` globally on your system, omit it if you want
to install in the current working directory):

```bash
npm install semistandard -g
```

After you've done that you should be able to use the `semistandard` program. The simplest use
case would be checking the style of all JavaScript files in the current working directory:

```bash
$ semistandard
Error: Use JavaScript Semi-Standard Style
  lib/torrent.js:950:11: Expected '===' and instead saw '=='.
```

You can optionally pass in a directory (or directories) using the glob pattern. Be sure to quote paths containing glob patterns so that they are expanded by semistandard instead of your shell:

```bash
$ semistandard "src/util/**/*.js" "test/**/*.js"
```

**Note:** by default `semistandard` will look for all files matching the patterns: `**/*.js`, `**/*.jsx`.


### Text editor plugins

First, install `semistandard`. Then, install the appropriate plugin for your editor:

- **Sublime users**: Try [SublimeLinter-contrib-semistandard](https://github.com/Flet/SublimeLinter-contrib-semistandard) for linting in your editor!
- **Atom users** - Install [linter-js-standard](https://atom.io/packages/linter-js-standard)

**Formatting code to Semistandard**

- **CLI** - [semistandard-format](https://github.com/ricardofbarros/semistandard-format)
- **Atom plugin** - [standard-formatter](https://atom.io/packages/standard-formatter)
- **Sublime Text plugin** - [StandardFormat](https://packagecontrol.io/packages/StandardFormat)
- **VS Code plugin** - [JavaScript Semi-Standard Format](https://marketplace.visualstudio.com/items/homerjam.vscode-semistandard-format)

Despite their names, all the above plugins support both `standard` and `semistandard`.

### What you might do if you're clever

1. Add it to `package.json`

  ```json
  {
    "name": "my-cool-package",
    "devDependencies": {
      "semistandard": "*"
    },
    "scripts": {
      "test": "semistandard && node my-normal-tests-littered-with-semicolons.js"
    }
  }
  ```

2. Check style automatically when you run `npm test`

  ```
  $ npm test
  Error: Code style check failed:
    lib/torrent.js:950:11: Expected '===' and instead saw '=='.
  ```

3. Never give style feedback on a pull request again! (unless it's about semicolons)

### Custom Parser
To use a custom parser, install it from npm (example: `npm install
babel-eslint`) and add this to your package.json:

```json
{
  "semistandard": {
    "parser": "babel-eslint"
  }
}
```

### [Vim](http://www.vim.org/)

Install **[Syntastic][vim-1]** and add these lines to `.vimrc`:

```vim
let g:syntastic_javascript_checkers=['standard']
let g:syntastic_javascript_standard_exec = 'semistandard'
```

For automatic formatting on save, add these two lines to `.vimrc`:

```vim
autocmd bufwritepost *.js silent !semistandard % --format
set autoread
```

[vim-1]: https://github.com/scrooloose/syntastic

### Ignoring files

Just like in `standard`, The paths `node_modules/**`, `*.min.js`, `bundle.js`, `coverage/**`, hidden files/folders
(beginning with `.`), and all patterns in a project's root `.gitignore` file are
automatically excluded when looking for `.js` files to check.

Sometimes you need to ignore additional folders or specific minfied files. To do that, add
a `semistandard.ignore` property to `package.json`:

```json
"semistandard": {
  "ignore": [
    "**/out/",
    "/lib/select2/",
    "/lib/ckeditor/",
    "tmp.js"
  ]
}
```

### Make it look `snazzy`
If you want prettier output, just install the [`snazzy`](https://github.com/feross/snazzy) package and pipe `semistandard` to it:

```bash
$ semistandard --verbose | snazzy
```

See [feross/standard] for more information.

[travis-image]: https://img.shields.io/travis/Flet/semistandard.svg?style=flat-square
[travis-url]: https://travis-ci.org/Flet/semistandard
[npm-image]: https://img.shields.io/npm/v/semistandard.svg?style=flat-square
[npm-url]: https://npmjs.org/package/semistandard
[downloads-image]: https://img.shields.io/npm/dm/semistandard.svg?style=flat-square
[downloads-url]: https://npmjs.org/package/semistandard
[feross/standard]: https://github.com/feross/standard
