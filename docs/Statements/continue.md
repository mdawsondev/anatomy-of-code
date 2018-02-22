# Continue
###### Sourced from [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/continue).

The **continue statement** terminates the current iteration of the current or labeled loop, then continues with the next iteration.

## Syntax
```
continue [label];
```

1. `label` *(Optional)* Identifier associated with the label of the statement.

## Description

Unline the `break` statement, `continue` *does not* terminate the entire loop, instead: in a `while` loop, it jumps back to the condition, and in a `for` loop, it jumps to the next iteration. The `continue` statement, like the `break` statement, can be tethered to a label to allow for control outside of the nested scope.