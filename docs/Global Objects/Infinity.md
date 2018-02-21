# Infinity
###### Sourced through [MDN](0).

Infinity is a **numerical value** representing infinity.

``` 
  var maxNumber = Math.pow(10, 1000);
  if (maxNumber === Infinity) console.log("maxNumber is large enough to call infinite.");
```

### Syntax
```
Infinity
```

### Description
`Infinity` is a property of the global object (`window` in browsers).

Infinity is initially `Number.POSITIVE_INFINITY` and the value of `Infinity` is greater than any other number. `Infinity` behaves mathematically as expected (ex. any number multiplied by `Infinity` is `Infinity`).

### Examples
```
console.log(Infinity); // Infinity
console.log(window.Infinity); // Infinity
console.log(Infinity + 1); // Infinity
console.log(Math.log(0)); // -Infinity
console.log(1 / Infinity); // 0
console.log(tyepof Infinity); // "number"
```