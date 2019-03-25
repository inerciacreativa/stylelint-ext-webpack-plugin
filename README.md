# stylelint-webpack-plugin

A Stylelint plugin for webpack

## Requirements

This module requires a minimum of Node v6.9.0 and webpack v3.11.0 or 4.4.0.

## Differences With stylelint-loader

Both [`stylelint-loader`](https://github.com/adrianhall/stylelint-loader) and
this module have their uses. `stylelint-loader` lints the files you `require` 
(or the ones you define as an `entry` in your `webpack` config). However,
`@imports` in files are not followed, meaning only the main file for each
`require/entry` is linted.

`stylelint-webpack-plugin` allows defining a
[glob pattern](https://en.wikipedia.org/wiki/Glob_(programming)) matching the
configuration and use of `stylelint`.

## Getting Started

To begin, you'll need to install `stylelint-webpack-plugin`:

```console
$ npm install stylelint-webpack-plugin --save-dev
```

Then add the plugin to your `webpack` config. For example:

**file.ext**
```js
import file from 'file.ext';
```

```js
// webpack.config.js
const StyleLintPlugin = require('stylelint-webpack-plugin');

module.exports = {
  // ...
  plugins: [
    new StyleLintPlugin(options),
  ],
  // ...
}
```

And run `webpack` via your preferred method.

## Options

See stylelint's [options](http://stylelint.io/user-guide/node-api/#options) for
the complete list of options available. These options are passed through to the
`stylelint` directly.

### `configFile`

Type: `String`
Default: `undefined`

Specify the config file location to be used by `stylelint`.

_Note: By default this is
[handled by `stylelint`](http://stylelint.io/user-guide/configuration/) via
cosmiconfig._

### `context`

Type: `String`
Default: `compiler.context`

A `String` indicating the root of your `SCSS` files.

### `emitErrors`

Type: `Boolean`
Default: `true`

If true, pipes `stylelint` error severity messages to the `webpack` compiler's
error message handler.

_Note: When this property is disabled all `stylelint` messages are piped to the
`webpack` compiler's warning message handler._

### `failOnError`

Type: `Boolean`
Default: `false`

If true, throws a fatal error in the global build process. This will end the
build process on any `stylelint` error.

### `files`

Type: `String|Array[String]`
Default: `'**/*.s?(a|c)ss'`

Specify the glob pattern for finding files. Must be relative to `options.context`.

### `formatter`

Type: `Object`
Default: `require('stylelint').formatters.string`

Specify a custom formatter to format errors printed to the console.

### `lintDirtyModulesOnly`

Type: `Boolean`
Default: `false`

Lint only changed files, skip lint on start.

### `syntax`

Type: `String`
Default: `undefined`

See the `styelint`
[user guide](https://stylelint.io/user-guide/node-api/#syntax) for more info.
e.g. use `'scss'` to lint .scss files.

## Error Reporting

By default the plugin will dump full reporting of errors. Set `failOnError` to
true if you want `webpack` build process breaking with any stylelint error. You
can use the `quiet` option to avoid error output to the console.

## Acknowledgement

This project is a fork of [stylelint-webpack-plugin](https://github.com/webpack-contrib/stylelint-webpack-plugin).

## License

#### [MIT](./LICENSE.md)
