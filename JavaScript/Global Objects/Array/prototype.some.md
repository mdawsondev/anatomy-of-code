# Array.prototype.some()
###### Sourced from [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some).

The `some()` method tests whether **at least one** element in the array passes the test provided by the function.

## Syntax
```
  var newArray = arr.some(function callback(currentValue[, index[, array]]) {
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
    The array that `some()` is being applied to.
2. `thisArg` *Optional*
  Value to use as `this` (i.e. the reference `Object`) when executing `callback`.

#### Return Value
`true` if the callback returns a truthy value **for any array element**; otherwise, `false`.

## Description
`some()` executes the `callback` function once per element in the provided array until it finds one where `callback` returns a truthy value. If such an element is found, `some()` **immediately** returns `true`; otherwise, `some()` returns `false`.

## Examples
```
let arrN = [1, 2, 4];

arrN.some( e => e >= 2); // true
```