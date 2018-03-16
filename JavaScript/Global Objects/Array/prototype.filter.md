# Array.prototype.map()
###### Sourced from [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map).

The `filter()` method creates a new array with all elements that pass the test implemented in the provided function.

## Syntax
```
  var newArray = arr.filter(function callback(currentValue[, index[, array]]) {
    // Return element for new_array
  }[, thisArg])
```

#### Parameters
1. `callback`
  Function to execute for each element, taking three arguments:
    * `currentValue` *(e)*
    The value of the current element.
    * `index` *(i) Optional*
    The index of the current element.
    * `array` *(a) Optional*
    The array that `filter()` is being applied to.
2. `thisArg` *Optional*
  Value to use as `this` (i.e. the reference `Object`) when executing `callback`.

#### Return Value
A new array with the elements that pass the test. If no elements pass, an empty array will be returned.

## Description
`filter()` calls a provided `callback` function once for each element in a provided array and constructs a new array of all the values for which `callback` returns a truthy value. `filter()` does not mutate the array on which it is called, and also follows the other specs of `forEach()` that frankly, I'm too lazy to type again.

## Examples
```
let arrN = [1, 2, 4];

arrN.filter(e => {
  return e >= 2; // [2, 4];
});
```