# empty
###### Sourced from [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/empty).

An **empty statement** is used to provide no statement where JavaScript syntax would expect one.

## Syntax
```
;
```

1. `label` *(Optional)* Identifier associated with the label of the statement. If the statement is not a loop or `switch`, this is required.

## Description

Empty statements can be used in various ways, from exiting statement blocks to iterating through single lined for loops. Typically empty statements are tagged with comments to help define exactly what their purpose is.

## Examples

```
var arr = [1, 2, 3];
for (i = 0; i < arr.length; arr[i++] = 0); // Empty statement, but arr is still processed.
// [0, 0, 0]
```

```
if (one)
  doOne();
else if (two)
  doTwo();
else if (three)
  ; // nothing happens
else if (four)
  doFour();
else
  doFive();
```
> In this if...else statement, if `three` is `true`, nothing will happen and `four` and `five` are never checked.