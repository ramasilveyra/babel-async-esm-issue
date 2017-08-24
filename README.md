# Babel v7 async function + export default,

[Babel v6 async function + export default issue](https://github.com/ramasilveyra/babel-async-esm-issue/tree/master).

## Installation

```
git clone git@github.com:ramasilveyra/babel-async-esm-issue.git
cd babel-async-esm-issue
git checkout v7
yarn
yarn run build
yarn start
```

## WORKS WITH V7 🎉

### Input

```js
export default async function sayHi() {
  console.log("Hi!");
};

sayHi();
```

### Output

```js
"use strict";

Object.defineProperty(exports, "__esModule", {
  value: true
});

let sayHi = (() => {
  var _ref = _asyncToGenerator(function* () {
    console.log("Hi!");
  });

  return function sayHi() {
    return _ref.apply(this, arguments);
  };
})();

function _asyncToGenerator(fn) { return function () { return new Promise((resolve, reject) => { var gen = fn.apply(this, arguments); function step(key, arg) { try { var info = gen[key](arg); var value = info.value; } catch (error) { reject(error); return; } if (info.done) { resolve(value); } else { Promise.resolve(value).then(_next, _throw); } } function _next(value) { step("next", value); } function _throw(err) { step("throw", err); } _next(); }); }; }

exports.default = sayHi;
;
sayHi();
```
