# break
###### Sourced from [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/break).

The **break statement** terminates the current loop, `switch`, or `label statement and transfers program control to the statement following the terminated statement.

## Syntax
```
break [label];
```

1. `label` *(Optional)* Identifier associated with the label of the statement. If the statement is not a loop or `switch`, this is required.

## Description

`break` statements are used to exit the scope of their current loop, or if provided with a `label`, `break` and `continue` will execute their functions on the labeled `block`. The `break` statement *must be nested within the referenced label*. The labeled statement can be any `block` statement; it does not have to be preceded by a loop.'