# NaN
###### Sourced through [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/NaN).

The global `NaN` property is a **number value** representing Not-A-Number.

### Syntax
```
NaN
```

### Description
`NaN` is a property of the *global object*, initialized as Not-A-Number, the same value of `Number.NaN`. `NaN` is a non-editable property, and should avoid being overridden. `NaN` is not commonly used in a program; it's the returned value when `Math` functions fail (`Math.sqrt(-1)`) or when a function parsing a number fails (`parseInt("String")`).

`NaN` will **always** compare unequal to any other value, including another NaN value. `Number.isNaN()` or `isNaN()` should be used to most clearly determine whether a value is NaN. However, do note the difference between these two functions: `isNaN()` will return `true` if the value is or will be `NaN` after coerced to a number, while `Number.isNaN()` will only return true if the value is *already* `NaN`.


### Examples
```
NaN === NaN; // false
Number.NaN === NaN; // false
isNaN(NaN); // true
isNaN(Number.NaN); // true

isNaN('Hello, world!'); // true
Number.isNaN('Hello, world!'); // false
```