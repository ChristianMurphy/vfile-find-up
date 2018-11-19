# vfile-find-up

[![Build][build-badge]][build]
[![Coverage][coverage-badge]][coverage]
[![Downloads][downloads-badge]][downloads]
[![Chat][chat-badge]][chat]

Find [vfile][]s by searching the file system upwards.

## Installation

[npm][]:

```bash
npm install vfile-find-up
```

## Usage

```js
var findUp = require('vfile-find-up')

findUp.all('package.json', console.log)
```

Yields:

```js
null [ VFile {
  data: {},
  messages: [],
  history: [ '/Users/tilde/projects/oss/vfile-find-up/package.json' ],
  cwd: '/Users/tilde/projects/oss/vfile-find-up' } ]
```

## API

### `findUp.all(tests[, path], callback)`

Search for `tests` upwards.  Invokes callback with either an error
or an array of files passing `tests`.
Note: Virtual Files are not read (their `contents` is not populated).

##### Parameters

###### `tests`

Things to search for (`string|Function|Array.<tests>`).

If a `string` is passed in, the `basename` or `extname` of files
must match it for them to be included.

If an array is passed in, any test must match a given file for it
to be included.

Otherwise, they must be [`function`][test].

###### `path`

Place to searching from (`string`, default: `process.cwd()`).

###### `callback`

Function invoked with all matching files (`function cb(err[, files])`).

### `findUp.one(tests[, path], callback)`

Like `findUp.all`, but invokes `callback` with the first found
file, or `null`.

### `function test(file)`

Check whether a virtual file should be included.  Invoked with a
[vfile][].

##### Returns

*   `true` or `findUp.INCLUDE` — Include the file in the results;
*   `findUp.BREAK` — Stop searching for files;
*   anything else is ignored: the file is not included.

The different flags can be combined by using the pipe operator:
`findUp.INCLUDE | findUp.BREAK`.

## Contribute

See [`contributing.md` in `vfile/vfile`][contributing] for ways to get started.

This organisation has a [Code of Conduct][coc].  By interacting with this
repository, organisation, or community you agree to abide by its terms.

## License

[MIT][] © [Titus Wormer][author]

<!-- Definitions -->

[build-badge]: https://img.shields.io/travis/vfile/vfile-find-up.svg

[build]: https://travis-ci.org/vfile/vfile-find-up

[coverage-badge]: https://img.shields.io/codecov/c/github/vfile/vfile-v.svg

[coverage]: https://codecov.io/github/vfile/vfile-find-up

[downloads-badge]: https://img.shields.io/npm/dm/vfile-v.svg

[downloads]: https://www.npmjs.com/package/vfile-find-up

[chat-badge]: https://img.shields.io/badge/join%20the%20community-on%20spectrum-7b16ff.svg

[chat]: https://spectrum.chat/unified/vfile

[npm]: https://docs.npmjs.com/cli/install

[mit]: license

[author]: https://wooorm.com

[vfile]: https://github.com/vfile/vfile

[test]: #function-testfile

[contributing]: https://github.com/vfile/vfile/blob/master/contributing.md

[coc]: https://github.com/vfile/vfile/blob/master/code-of-conduct.md
