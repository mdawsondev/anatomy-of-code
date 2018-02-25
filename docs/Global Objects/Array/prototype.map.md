# Array.prototype.map()
###### Sourced from [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map).

The `map()` method creates a new array with the results of calling a provided function on every element in the calling array.

## Syntax
```
  var new_array = arr.map(function callback(currentValue[, index[, array]]) {
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
    The array that `forEach()` is being applied to.
2. `thisArg` *Optional*
  Value to use as `this` (i.e. the reference `Object`) when executing `callback`.

#### Return Value
A new array with each element being the result of the callback function.

## Description
`map` call a provided `callback` function **once for each element** in an array, in order, and returns the results to a new array. `callback` is only invoked for elements which have a value, including undefined. If a `thisArg` parameter is provided to `map`, it will be used as callback's `this` value, otherwise, `undefined` will be assigned to `this`.

`map` does not mutate the original array, although `callback` may do so. The range of elements processed by `map` is set before the invocation of `callback`, and as such, iterates over each element the same way `forEach()` does.

## Examples
```
let arrN = [1, 2, 4], // array of numbers
    arrS = ['1', '2', '4']; // array of strings

arrN.map(Math.pow); // [1, 2, 16]
arrN.map(e => e * 2); // [2, 4, 8]
arrS.map(e => Number(e)); // [1, 2, 4]
```