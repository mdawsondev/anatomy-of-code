# undefined
###### Sourced through [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/undefined).

`undefined` is a global property representing the primitive value of `undefined`. It's the default value given to a variable that has been declared but not defined.

### Syntax
```
undefined
```

### Description
`undefined` is the value assigned to variables that have not been defined (`let x;`). It's a non-editable property that should never be overridden.

A variable that has not been assigned a value is of type undefined. A method or statement also returns `undefined` if the variable that is being evaluated does not have an assigned value. A function returns undefined if a value was not `returned` (i.e. if the function doesn't return anything).

`undefined` can be detected via `typeof undefined` or a strict compairson (`===`) to `undefined`. `typeof` should typically be avoided for `undefined` comparisons due to the nature of `typeof` avoiding a `ReferenceError` if the variable has not been declared. Comparing a value against `void 0` is also acceptable, as it returns undefined.

Caution should be used when using a non-strict comparison (`==`) due to the nature of a falsey value equaling a falsey value (e.g. `null` == `undefined` returns `true` but `null` === `undefined` returns false).


### Examples
```
let x;
typeof x === 'undefined'; // true
x === undefined; // true
x === void 0; // true

typeof y === 'undefined'; // true
y === 'undefined'; // ReferenceError: y is not defined
y === void 0; // ReferenceError: y is not defined

null == undefined; // true (non-strict)
null === undefined; // false (strict)
```
