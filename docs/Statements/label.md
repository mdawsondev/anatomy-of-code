# label
###### Sourced from [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/label).

The **label statement** can be used with `break` or `continue` statements by prefixing a `block` with an identifier.
> Labeled loops or blocks are very uncommon. Oftentimes function calls can be used instead of loop jumps.

## Syntax
```
label:
  statement
```

1. `label` Any JavaScript identifier that is not a reserved word (e.g. let, for, etc.).
2. `statement` Any block-level statement.


## Description

`label`, partnered with `break` or `continue`, is used to indicate whether a program should interrupt or continue execution.

## Example
```
foo: {
  console.log('One!');
  break foo;
  console.log("Two!"); // Not executed.
}
console.log("Three!");

// "One!"
// "Three!"
```