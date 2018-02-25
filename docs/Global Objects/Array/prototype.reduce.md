# Array.prototype.reduce()
###### Sourced from [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce).

The `reduce()` method applies a function against an accumulator and each element in the array (left to right), reducing it to a single value.

## Syntax
```
  var newArray = arr.some(function callback(accumulator, currentValue[, index[, array]]) {
    // Return element for new_array
  }[, thisArg]
```

#### Parameters
1. `callback`
  Function to execute for each element, taking four arguments:
    * `accumulator` *(x)*
    The accumulator accumulates the callback's return values; it is the accumulated value previously returned in the last invocation of the callback, or `initialValue`, if supplied. 
    * `currentValue` *(e)*
    The value of the current element.
    * `index` *(i) Optional*
    The index of the current element.
    * `array` *(a) Optional*
    The array that `some()` is being applied to.
2. `initialValue` *Optional*
  Value to use as the first argument to the first call of the `callback`. If no initial value is supplied, **the first element in the array will be used**. Calling `reduce()` on an empty array without an initial value results in `TypeError`.

#### Return Value
The value that results from the reduction (accumulator's final value).

## Description
`reduce()` executes the `callback` function once for each argument in the array, excluding empty values. The first time it's called, `accumulator` and `currentValue` can be one of two values. If `initialValue` is provided to `reduce()`, the `accumulator` will be equal to `initialValue` and `currentValue` will be equal to the first element in the array. If **no** `initialValue` is provided, then `accumulator` will be equal to the **first** value in the array, and `currentValue` will be equal to the **second**.

This reflects in the starting index, where `index` is `0` if provided with an `initialValue`, and `1` if not. If the array only has one element and no `initialValue` is provided, the solo value will be returned without calling `callback`.

## Examples
```
[2, 3, 4, 5, 6].reduce((x, e) => {
  return x+e;
}); // Sums each element starting with 2;

[2, 3, 4, 5, 6].reduce((x, e) => {
  return x+e;
}, 9); // Sums each element starting with 9;

```