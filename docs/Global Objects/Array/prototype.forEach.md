# Array.prototype.forEach()
###### Sourced from [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach).

The `forEach` method executes a provided function **once for each array element**.

## Syntax
```
  arr.forEach(function callback(currentValue[, index[, array]]) {
    //your iterator
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
  `undefined` - forEach is not meant to return data.

## Description
`forEach()` executes the internal `callback` function per each element in the array in ascending order, but ignores indexes that have been deleted or unintialized.

`callback` is invoked with **three arguments**:
  * the **element value** *e*
  * the *optional* **element index** *i*
  * the *optional* **array being traversed** *a*

If a `thisArg` parameter is provided, it will be used as the callback function's `this` value, otherwise the value `undefined` will be assigned to `this`. However, if passed through an arrow function, `this` is lexically bound to the Object it inhabits.

The range of elements (i.e. indexes) processed by `forEach()` is set **before the first invocation** of `callback`. Elements that are appended *after* the call to `forEach()` begins will *not* be visited by `callback`. If the value of an array's element is changed while the loop is being processed, the value passed to `callback` will be the value **at the time** `forEach()` visits them; elements that are deleted before being visited are not visited. If elements that are already visited get removed during the iteration, later elements will be skipped due to the index range remaining unchanged (e.g. using `shift()` will cause the next index to move forward in the array, thus being skipped).

`forEach()` differs from `map()` and `reduce()` as it always returns the value of `undefined` and *is not chainable*.

> You can't stop or break a `forEach()` loop other than by throwing an exception. If you need such behavior, a more typical loop is preferred. If looking to return a Boolean value, `every()` or `some()` should be used instead. The new methods `find()` or `findIndex()` may be used for early termination upon true predicates.

## Notes

* The parameter `array` is bound to the original array, i.e. if the original array is mutated mid-loop, `array` is also mutated and does not retain the original values.
* Unless passed through a function declaration, `this` from `thisArg` will represent the external Object encasing the method. Arrow functions do not accept `thisArg`.