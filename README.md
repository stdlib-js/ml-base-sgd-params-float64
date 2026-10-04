<!--

@license Apache-2.0

Copyright (c) 2026 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# Float64Params

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Create a double-precision floating-point SGD parameters object.

<!-- Section to include introductory text. Make sure to keep an empty line after the intro `section` element and another before the `/section` close. -->

<section class="intro">

</section>

<!-- /.intro -->

<!-- Package usage documentation. -->



<section class="usage">

## Usage

```javascript
import Float64Params from 'https://cdn.jsdelivr.net/gh/stdlib-js/ml-base-sgd-params-float64@esm/index.mjs';
```

#### Float64Params( \[arg\[, byteOffset\[, byteLength]]] )

Returns a double-precision floating-point SGD parameters object.

```javascript
var params = new Float64Params();
// returns {...}
```

The function supports the following parameters:

-   **arg**: an [`ArrayBuffer`][@stdlib/array/buffer] or a data object (_optional_).
-   **byteOffset**: byte offset (_optional_).
-   **byteLength**: maximum byte length (_optional_).

A data object argument is an object having one or more of the following properties:

-   **penalty**: [regularization function][@stdlib/ml/base/sgd/penalties].

-   **penaltyParams**: parameters specific to the regularization function being used. Must be a [`Float64Array`][@stdlib/array/float64] having length `2`, with any unused elements set to zero. The expected array contents depend on `penalty`:

    -   **l1**: `[ lambda, 0.0 ]`
    -   **l2**: `[ lambda, 0.0 ]`
    -   **elasticnet**: `[ lambda, l1Ratio ]`
    -   **none**: `[ 0.0, 0.0 ]` (unused)

    where

    -   **lambda**: regularization parameter which determines the amount of shrinkage inflicted on the model coefficients.
    -   **l1Ratio**: mixing parameter on the interval `[0,1]` which determines the relative contribution of the L1 and L2 penalties.

-   **learningRate**: [learning rate scheduler][@stdlib/ml/base/sgd/learning-rates].

-   **learningRateParams**: parameters specific to the learning rate scheduler being used. Must be a [`Float64Array`][@stdlib/array/float64] having length `2`, with any unused elements set to zero. The expected array contents depend on `learningRate`:

    -   **basic**: `[ 0.0, 0.0 ]` (unused)
    -   **constant**: `[ eta0, 0.0 ]`
    -   **invscaling**: `[ eta0, powerT ]`
    -   **pegasos**: `[ lambda, 0.0 ]`

    where

    -   **eta0**: initial learning rate.
    -   **powerT**: exponent controlling how quickly the learning rate decreases.
    -   **lambda**: regularization parameter.

-   **lossFunction**: [loss function][@stdlib/ml/base/sgd/loss-functions].

-   **lossFunctionParams**: parameters specific to the loss function being used. Must be a [`Float64Array`][@stdlib/array/float64] having length `1`. The expected array contents depend on `lossFunction`:

    -   **epsilon-insensitive**: `[ epsilon ]`
    -   **squared-epsilon-insensitive**: `[ epsilon ]`
    -   **huber**: `[ threshold ]`
    -   all other loss functions: `[ 0.0 ]` (unused)

    where

    -   **epsilon**: insensitivity parameter (i.e., errors whose absolute value is less than `epsilon` incur no penalty).
    -   **threshold**: error magnitude at which the loss transitions from squared-error loss to linear loss.

-   **fitIntercept**: boolean indicating whether to include an intercept. If `true`, an element equal to one is implicitly added to each provided feature vector. If `false`, the model assumes that feature vectors are already centered.

-   **intercept**: initial intercept value. Only applicable when `fitIntercept` is `true`.

-   **maxIter**: maximum number of iterations to run.

#### Float64Params.prototype.penalty

Regularization function.

```javascript
var params = new Float64Params();
// returns {...}

// ...

var v = params.penalty;
// returns <string>
```

#### Float64Params.prototype.penaltyParams

Parameters specific to the regularization function being used.

```javascript
var params = new Float64Params();
// returns {...}

// ...

var v = params.penaltyParams;
// returns <Float64Array>
```

#### Float64Params.prototype.learningRate

Learning rate scheduler.

```javascript
var params = new Float64Params();
// returns {...}

// ...

var v = params.learningRate;
// returns <string>
```

#### Float64Params.prototype.learningRateParams

Parameters specific to the learning rate scheduler being used.

```javascript
var params = new Float64Params();
// returns {...}

// ...

var v = params.learningRateParams;
// returns <Float64Array>
```

#### Float64Params.prototype.lossFunction

Loss function.

```javascript
var params = new Float64Params();
// returns {...}

// ...

var v = params.lossFunction;
// returns <string>
```

#### Float64Params.prototype.lossFunctionParams

Parameters specific to the loss function being used.

```javascript
var params = new Float64Params();
// returns {...}

// ...

var v = params.lossFunctionParams;
// returns <Float64Array>
```

#### Float64Params.prototype.fitIntercept

Boolean indicating whether to include intercept.

```javascript
var params = new Float64Params();
// returns {...}

// ...

var v = params.fitIntercept;
// returns <boolean>
```

#### Float64Params.prototype.intercept

Initial intercept value.

```javascript
var params = new Float64Params();
// returns {...}

// ...

var v = params.intercept;
// returns <number>
```

#### Float64Params.prototype.maxIter

Maximum number of iterations to run.

```javascript
var params = new Float64Params();
// returns {...}

// ...

var v = params.maxIter;
// returns <number>
```

#### Float64Params.prototype.toString( \[options] )

Serializes an SGD trainer parameters object to a formatted string.

```javascript
var params = new Float64Params();
// returns {...}

// ...

var v = params.toString();
// returns <string>
```

The method supports the following options:

-   **digits**: number of digits to display after decimal points. Default: `4`.

Example output:

```text

Stochastic Gradient Descent

    penalty: l2
    learning rate: constant
    loss function: hinge
    lambda: 2.5000
    eta0: 0.0100
    fit intercept: true
    intercept: 0.0000
    max iterations: 1000

```

#### Float64Params.prototype.toJSON( \[options] )

Serializes an SGD trainer parameters object as a JSON object.

```javascript
var params = new Float64Params();
// returns {...}

// ...

var v = params.toJSON();
// returns {...}
```

`JSON.stringify()` implicitly calls this method when stringifying an SGD trainer parameters instance.

#### Float64Params.prototype.toDataView()

Returns a [`DataView`][@stdlib/array/dataview] of an SGD trainer parameters object.

```javascript
var params = new Float64Params();
// returns {...}

// ...

var v = params.toDataView();
// returns <DataView>
```

</section>

<!-- /.usage -->

<!-- Package usage notes. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="notes">

## Notes

-   A parameters object is a [`struct`][@stdlib/dstructs/struct] providing a fixed-width composite data structure for storing SGD trainer parameters and providing an ABI-stable data layout for JavaScript-C interoperation.

</section>

<!-- /.notes -->

<!-- Package usage examples. -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```html
<!DOCTYPE html>
<html lang="en">
<body>
<script type="module">

import Float64Array from 'https://cdn.jsdelivr.net/gh/stdlib-js/array-float64@esm/index.mjs';
import Params from 'https://cdn.jsdelivr.net/gh/stdlib-js/ml-base-sgd-params-float64@esm/index.mjs';

var params = new Params({
    'penaltyParams': new Float64Array( [ 2.5, 0.0 ] ),
    'learningRateParams': new Float64Array( [ 0.01, 0.0 ] ),
    'lossFunctionParams': new Float64Array( [ 0.0 ] ),
    'intercept': 0.0,
    'maxIter': 500,
    'penalty': 'l2',
    'learningRate': 'constant',
    'lossFunction': 'hinge',
    'fitIntercept': true
});

var str = params.toString();
console.log( str );

</script>
</body>
</html>
```

</section>

<!-- /.examples -->

<!-- C interface documentation. -->



<!-- Section to include cited references. If references are included, add a horizontal rule *before* the section. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="references">

</section>

<!-- /.references -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2026. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/ml-base-sgd-params-float64.svg
[npm-url]: https://npmjs.org/package/@stdlib/ml-base-sgd-params-float64

[test-image]: https://github.com/stdlib-js/ml-base-sgd-params-float64/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/ml-base-sgd-params-float64/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/ml-base-sgd-params-float64/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/ml-base-sgd-params-float64?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/ml-base-sgd-params-float64.svg
[dependencies-url]: https://david-dm.org/stdlib-js/ml-base-sgd-params-float64/main

-->

[chat-image]: https://img.shields.io/badge/zulip-join_chat-brightgreen.svg
[chat-url]: https://stdlib.zulipchat.com

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/ml-base-sgd-params-float64/tree/deno
[deno-readme]: https://github.com/stdlib-js/ml-base-sgd-params-float64/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/ml-base-sgd-params-float64/tree/umd
[umd-readme]: https://github.com/stdlib-js/ml-base-sgd-params-float64/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/ml-base-sgd-params-float64/tree/esm
[esm-readme]: https://github.com/stdlib-js/ml-base-sgd-params-float64/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/ml-base-sgd-params-float64/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/ml-base-sgd-params-float64/main/LICENSE

[@stdlib/dstructs/struct]: https://github.com/stdlib-js/dstructs-struct/tree/esm

[@stdlib/ml/base/sgd/penalties]: https://github.com/stdlib-js/ml-base-sgd-penalties/tree/esm

[@stdlib/ml/base/sgd/learning-rates]: https://github.com/stdlib-js/ml-base-sgd-learning-rates/tree/esm

[@stdlib/ml/base/sgd/loss-functions]: https://github.com/stdlib-js/ml-base-sgd-loss-functions/tree/esm

[@stdlib/array/dataview]: https://github.com/stdlib-js/array-dataview/tree/esm

[@stdlib/array/float64]: https://github.com/stdlib-js/array-float64/tree/esm

[@stdlib/array/buffer]: https://github.com/stdlib-js/array-buffer/tree/esm

</section>

<!-- /.links -->
