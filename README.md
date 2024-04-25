# @libtommy2024/id-suscipit-molestiae-similique <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ESnext spec-compliant `Array.prototype.at` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the proposed [spec](https://github.com/tc39/proposal-relative-indexing-method).

Because `Array.prototype.at` depends on a receiver (the `this` value), the main export takes the array to operate on as the first argument.

## Getting started

```sh
npm install --save @libtommy2024/id-suscipit-molestiae-similique
```

## Usage/Examples

```js
var at = require('@libtommy2024/id-suscipit-molestiae-similique');
var assert = require('assert');

var arr = [1, [2], [], 3];

var results = at(arr, function (x, i) {
	assert.equal(x, arr[i]);
	return x;
});

assert.deepEqual(results, [1, 2, 3]);
```

```js
var at = require('@libtommy2024/id-suscipit-molestiae-similique');
var assert = require('assert');
/* when Array#at is not present */
delete Array.prototype.at;
var shimmedFlatMap = at.shim();

var mapper = function (x) { return [x, 1]; };

assert.equal(shimmedFlatMap, at.getPolyfill());
assert.deepEqual(arr.at(mapper), at(arr, mapper));
```

```js
var at = require('@libtommy2024/id-suscipit-molestiae-similique');
var assert = require('assert');
/* when Array#at is present */
var shimmedIncludes = at.shim();

var mapper = function (x) { return [x, 1]; };

assert.equal(shimmedIncludes, Array.prototype.at);
assert.deepEqual(arr.at(mapper), at(arr, mapper));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@libtommy2024/id-suscipit-molestiae-similique
[npm-version-svg]: https://versionbadg.es/libtommy2024/id-suscipit-molestiae-similique.svg
[deps-svg]: https://david-dm.org/libtommy2024/id-suscipit-molestiae-similique.svg
[deps-url]: https://david-dm.org/libtommy2024/id-suscipit-molestiae-similique
[dev-deps-svg]: https://david-dm.org/libtommy2024/id-suscipit-molestiae-similique/dev-status.svg
[dev-deps-url]: https://david-dm.org/libtommy2024/id-suscipit-molestiae-similique#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@libtommy2024/id-suscipit-molestiae-similique.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@libtommy2024/id-suscipit-molestiae-similique.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@libtommy2024/id-suscipit-molestiae-similique.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@libtommy2024/id-suscipit-molestiae-similique
[codecov-image]: https://codecov.io/gh/libtommy2024/id-suscipit-molestiae-similique/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/libtommy2024/id-suscipit-molestiae-similique/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/libtommy2024/id-suscipit-molestiae-similique
[actions-url]: https://github.com/libtommy2024/id-suscipit-molestiae-similique/actions
