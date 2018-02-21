# Infinity

#### Sourced through [MDN web docs](0).

Infinity is a *numerical value* representing infinity.

```
  var maxNumber = Math.pow(10, 1000);
  if (maxNumber === Infinity) console.log("maxNumber is large enough to call infinite.");
```

### Syntax
> Infinity

### Description
`Infinity` is a property of the global object (`window` in browsers).

Infinity is initially `Number.POSITIVE_INFINITY` and the value of `Infinity` is greater than any other number. `Infinity` behaves mathematically as expected (ex. any number multiplied by `Infinity` is `Infinity`).

### Examples

```
  1| console.log(Infinity); // Infinity
  2| console.log(window.Infinity); // Infinity
  3| console.log(Infinity + 1); // Infinity
  4| console.log(Math.log(0)); // -Infinity
  5| console.log(1 / Infinity); // 0
```