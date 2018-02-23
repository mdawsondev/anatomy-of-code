# Object.is()
###### Sourced from [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/is)

The `Object.is()` method is used to determine whether two values are the same.

## Syntax
```
Object.is(value1, value2)
```

#### Parameters
**value1** The first value to compare.
**value2** The second value to compare.

#### Return Value
A `Boolean` indicating whether the two parameters are the same value; i.e. `true` or `false`.

## Description

`Object.is()` is used to determine whether two values are the same; it is similar to `==` and `===` comparisons, but differs in the way `-0` and `NaN` are evaluated. Through `Object.is()`, `NaN` will evaluate `true` against itself. Likewise, `+0` and `-0` will evaluate `false` against eachother because they are not considered the same value of `0`.

## Examples
```
42 == 42; // true
42 == '42'; // true
42 === 42; // true
42 === '42'; // false
Object.is(42, 42); // true
Object.is(42, '42'); // false

NaN == NaN; // false
NaN === NaN; // false
Object.is(NaN, NaN); // true

0 == -0; // true
0 === -0; // true
Object.is(0, -0); // false
```