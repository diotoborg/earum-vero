# Symbol.prototype.description <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ECMAScript spec-compliant `Symbol.prototype.description` shim. Invoke its "shim" method to shim Symbol.prototype.description if it is unavailable.
*Note*: `Symbol#description` requires a true ES6 environment, specifically one with native Symbols (eg, node >= v11.15.0)

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES6-supported environment and complies with the [spec](https://tc39.es/ecma262/#sec-@diotoborg/earum-vero).

Most common usage:
```js
var description = require('@diotoborg/earum-vero');
var assert = require('assert');

assert(description(Symbol('foo')) === 'foo');
assert(description(Symbol()) === undefined);
assert(description(Symbol(undefined)) === undefined);
assert(description(Symbol(null)) === 'null');

if (!('description' in Symbol.prototype)) {
	// note: this should be the empty string, but in many engines,
	// it is impossible to distinguish Symbol() and Symbol('')
	// without globally replacing `Symbol`
	assert(description(Symbol('')) === undefined);

	description.shim();
}

assert(description(Symbol('foo')) === Symbol('foo').description);
assert(description(Symbol()) === Symbol().description);
assert(description(Symbol(undefined)) === Symbol(undefined).description);
assert(description(Symbol(null)) === Symbol(null).description);

assert(Symbol('').description === ''); // this works fine!
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.com/package/@diotoborg/earum-vero
[npm-version-svg]: https://versionbadg.es/diotoborg/earum-vero.svg
[deps-svg]: https://david-dm.org/diotoborg/earum-vero.svg
[deps-url]: https://david-dm.org/diotoborg/earum-vero
[dev-deps-svg]: https://david-dm.org/diotoborg/earum-vero/dev-status.svg
[dev-deps-url]: https://david-dm.org/diotoborg/earum-vero#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@diotoborg/earum-vero.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@diotoborg/earum-vero.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@diotoborg/earum-vero.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@diotoborg/earum-vero
[codecov-image]: https://codecov.io/gh/diotoborg/earum-vero/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/diotoborg/earum-vero/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/diotoborg/earum-vero
[actions-url]: https://github.com/diotoborg/earum-vero/actions
