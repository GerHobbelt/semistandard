# JavaScript Semi-4-Standard Style
[![travis][travis-image]][travis-url]
[![npm][npm-image]][npm-url]
[![downloads][downloads-image]][downloads-url]
[![bitHound Dependencies](https://www.bithound.io/github/gtanner/semi-4standard/badges/dependencies.svg)](https://www.bithound.io/github/gtanner/semi-4standard/master/dependencies/npm)

### One Semicolon and two (2) unnecessary spaces for the Dark Lord on his dark throne

All the goodness of [feross/standard] with semicolons and 4 space tabs sprinkled on top.

## Install

```bash
npm install semi-4standard
```

## Rules

Importantly:

- **semicolons**
- **4 spaces**
- Check [feross/standard] for the rest of the rules.

## Badge

Use this in one of your projects? Include one of these badges in your readme to
let people know that your code is using the standard style.

[![js-semi-4standard-style](https://cdn.rawgit.com/flet/semi-4standard/master/badge.svg)](https://github.com/Flet/semi-4standard)

```markdown
[![js-semi-4standard-style](https://cdn.rawgit.com/flet/semi-4standard/master/badge.svg)](https://github.com/Flet/semi-4standard)
```

[![js-semi-4standard-style](https://img.shields.io/badge/code%20style-semi-4standard-brightgreen.svg?style=flat-square)](https://github.com/Flet/semi-4standard)

```markdown
[![js-semi-4standard-style](https://img.shields.io/badge/code%20style-semi-4standard-brightgreen.svg?style=flat-square)](https://github.com/Flet/semi-4standard)
```

## Usage

The easiest way to use JavaScript Semi-4-Standard Style to check your code is to install it
globally as a Node command line program. To do so, simply run the following command in
your terminal (flag `-g` installs `semi-4standard` globally on your system, omit it if you want
to install in the current working directory):

```bash
npm install semi-4standard -g
```

After you've done that you should be able to use the `semi-4standard` program. The simplest use
case would be checking the style of all JavaScript files in the current working directory:

```
$ semi-4standard
Error: Use JavaScript Semi-4-Standard Style
  lib/torrent.js:950:11: Expected '===' and instead saw '=='.
```

### Editor plugins

- **Sublime users**: Try [SublimeLinter-contrib-semi-4standard](https://github.com/Flet/SublimeLinter-contrib-semi-4standard) for linting in your editor!
- **Atom users** - Install [linter-js-standard](https://atom.io/packages/linter-js-standard)

**Formatting code to Semistandard**

- **CLI** - [semi-4standard-format](https://github.com/ricardofbarros/semi-4standard-format)
- **Atom plugin** - [standard-formatter](https://atom.io/packages/standard-formatter)
- **Sublime Text plugin** - [StandardFormat](https://packagecontrol.io/packages/StandardFormat)
- **VS Code plugin** - [JavaScript Semi-4-Standard Format](https://marketplace.visualstudio.com/items/homerjam.vscode-semi-4standard-format)

Despite their names, all the above plugins support both `standard` and `semi-4standard`.

### What you might do if you're clever

1. Add it to `package.json`

  ```json
  {
    "name": "my-cool-package",
    "devDependencies": {
      "semi-4standard": "*"
    },
    "scripts": {
      "test": "semi-4standard && node my-normal-tests-littered-with-semicolons.js"
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
  "semi-4standard": {
    "parser": "babel-eslint"
  }
}
```

### [Vim](http://www.vim.org/)

Install **[Syntastic][vim-1]** and add these lines to `.vimrc`:

```vim
let g:syntastic_javascript_checkers=['standard']
let g:syntastic_javascript_standard_exec = 'semi-4standard'
```

For automatic formatting on save, add these two lines to `.vimrc`:

```vim
autocmd bufwritepost *.js silent !semi-4standard % --format
set autoread
```

[vim-1]: https://github.com/scrooloose/syntastic

### Ignoring files

Just like in `standard`, The paths `node_modules/**`, `*.min.js`, `bundle.js`, `coverage/**`, hidden files/folders
(beginning with `.`), and all patterns in a project's root `.gitignore` file are
automatically excluded when looking for `.js` files to check.

Sometimes you need to ignore additional folders or specific minfied files. To do that, add
a `semi-4standard.ignore` property to `package.json`:

```json
"semi-4standard": {
  "ignore": [
    "**/out/",
    "/lib/select2/",
    "/lib/ckeditor/",
    "tmp.js"
  ]
}
```

### Make it look `snazzy`
If you want prettier output, just install the [`snazzy`](https://github.com/feross/snazzy) package and pipe `semi-4standard` to it:

```bash
$ semi-4standard --verbose | snazzy
```

See [feross/standard] for more information.

[travis-image]: https://img.shields.io/travis/Flet/semi-4standard.svg?style=flat-square
[travis-url]: https://travis-ci.org/Flet/semi-4standard
[npm-image]: https://img.shields.io/npm/v/semi-4standard.svg?style=flat-square
[npm-url]: https://npmjs.org/package/semi-4standard
[downloads-image]: https://img.shields.io/npm/dm/semi-4standard.svg?style=flat-square
[downloads-url]: https://npmjs.org/package/semi-4standard
[feross/standard]: https://github.com/feross/standard
