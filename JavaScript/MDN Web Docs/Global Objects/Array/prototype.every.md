# Array.prototype.every()
###### Sourced from [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every).

The `every()` method tests whether **every** element in the array passes the test provided by the function.

## Syntax
```
  var newArray = arr.every(function callback(currentValue[, index[, array]]) {
    // Return element for new_array
  }[, thisArg]
```

#### Parameters
1. `callback`
  Function to execute for each element, taking three arguments:
    * `currentValue` *(e)*
    The value of the current element.
    * `index` *(i) Optional*
    The index of the current element.
    * `array` *(a) Optional*
    The array that `every()` is being applied to.
2. `thisArg` *Optional*
  Value to use as `this` (i.e. the reference `Object`) when executing `callback`.

#### Return Value
`true` if every element returns true, otherwise `false`.

## Description
`every()` executes the `callback` function once per element in the provided array until it finds one where `callback` returns a falsy value. If such a value is found, `every()` immediately returns `false`, otherwise, it returns `true`. It is essentially the opposite of `some()`.

## Examples
```
let arrN = [1, 2, 4],
    arrN2 = [-1, 3, 5];

arrN.every( e => e > 0); // true
arrN2.every( e => e > 0); // false
```