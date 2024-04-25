# @wemnyelezxnpm/placeat-ab-ea <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ES5 spec-compliant `Array.prototype.filter` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the [spec](https://www.ecma-international.org/ecma-262/5.1/).

Because `Array.prototype.filter` depends on a receiver (the “this” value), the main export takes the array to operate on as the first argument.

## Example

```js
var filter = require('@wemnyelezxnpm/placeat-ab-ea');
var assert = require('assert');

assert.deepEqual(filter([1, 2, 3], function (x) { return x >= 2; }), [2, 3]);
assert.deepEqual(filter([1, 2, 3], function (x) { return x <= 2; }), [1, 2]);
```

```js
var filter = require('@wemnyelezxnpm/placeat-ab-ea');
var assert = require('assert');
/* when Array#filter is not present */
delete Array.prototype.filter;
var shimmedFilter = filter.shim();
assert.equal(shimmedFilter, filter.getPolyfill());
var arr = [1, 2, 3];
var isOdd = function (x) { return x % 2 !== 0; };
assert.deepEqual(arr.filter(isOdd), filter(arr, isOdd));
```

```js
var filter = require('@wemnyelezxnpm/placeat-ab-ea');
var assert = require('assert');
/* when Array#filter is present */
var shimmedFilter = filter.shim();
assert.equal(shimmedFilter, Array.prototype.filter);
assert.deepEqual(arr.filter(isOdd), filter(arr, isOdd));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@wemnyelezxnpm/placeat-ab-ea
[npm-version-svg]: https://versionbadg.es/wemnyelezxnpm/placeat-ab-ea.svg
[deps-svg]: https://david-dm.org/wemnyelezxnpm/placeat-ab-ea.svg
[deps-url]: https://david-dm.org/wemnyelezxnpm/placeat-ab-ea
[dev-deps-svg]: https://david-dm.org/wemnyelezxnpm/placeat-ab-ea/dev-status.svg
[dev-deps-url]: https://david-dm.org/wemnyelezxnpm/placeat-ab-ea#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@wemnyelezxnpm/placeat-ab-ea.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@wemnyelezxnpm/placeat-ab-ea.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@wemnyelezxnpm/placeat-ab-ea.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@wemnyelezxnpm/placeat-ab-ea
[codecov-image]: https://codecov.io/gh/wemnyelezxnpm/placeat-ab-ea/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/wemnyelezxnpm/placeat-ab-ea/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/wemnyelezxnpm/placeat-ab-ea
[actions-url]: https://github.com/wemnyelezxnpm/placeat-ab-ea/actions
