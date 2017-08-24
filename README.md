# Babel v6 async function + export default issue

```js
export default async function sayHi() {
}
sayHi();
```

> ReferenceError: sayHi is not define

[Babel v7 async function + export default issue](https://github.com/ramasilveyra/babel-async-esm-issue/tree/v7).

## Installation

```
git clone git@github.com:ramasilveyra/babel-async-esm-issue.git
cd babel-async-esm-issue
yarn
yarn run build
yarn start
```

### Issue

### Input

```js
export default async function sayHi() {
  console.log("Hi!");
};

sayHi();
```

### Actual Output

```js
"use strict";

Object.defineProperty(exports, "__esModule", {
  value: true
});

function _asyncToGenerator(fn) { return function () { var gen = fn.apply(this, arguments); return new Promise(function (resolve, reject) { function step(key, arg) { try { var info = gen[key](arg); var value = info.value; } catch (error) { reject(error); return; } if (info.done) { resolve(value); } else { return Promise.resolve(value).then(function (value) { step("next", value); }, function (err) { step("throw", err); }); } } return step("next"); }); }; }

exports.default = (() => {
  var _ref = _asyncToGenerator(function* () {
    console.log("Hi!");
  });

  function sayHi() {
    return _ref.apply(this, arguments);
  }

  return sayHi;
})();

sayHi();
```

### Expected Output (MAYBE, not sure about if this behaviour is defined on the spec)

```js
"use strict";

Object.defineProperty(exports, "__esModule", {
  value: true
});

function _asyncToGenerator(fn) { return function () { var gen = fn.apply(this, arguments); return new Promise(function (resolve, reject) { function step(key, arg) { try { var info = gen[key](arg); var value = info.value; } catch (error) { reject(error); return; } if (info.done) { resolve(value); } else { return Promise.resolve(value).then(function (value) { step("next", value); }, function (err) { step("throw", err); }); } } return step("next"); }); }; }

var sayHi = exports.default = (() => {
  var _ref = _asyncToGenerator(function* () {
    console.log("Hi!");
  });

  function sayHi() {
    return _ref.apply(this, arguments);
  }

  return sayHi;
})();

sayHi();
```
