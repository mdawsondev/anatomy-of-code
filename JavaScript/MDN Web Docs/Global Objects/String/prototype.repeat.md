# String.prototype.repeat()
###### Sourced from [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/repeat)

The `repeat()` method constructs and returns a new concantenated string of copies of the original string.

## Syntax
```
str.repeat(count);
```

#### Parameters
`count` A positive integer indicating the number of times to repeat the string.

#### Return value
A new string containing the specified number of copies of the given string.

#### Exceptions
* `RangeError`: repeat count must be non-negative.
* `RangeError`: repeat count must be less than infinity and not overflow maximum string size.

## Examples
```
'abc'.repeat(-1); // RangeError
'abc'.repeat(0); // ''
'abc'.repeat(1); // 'abc'
'abc'.repeat(3); // 'abcabcabc'
'abc'.repeat(3.5); // 'abcabcabc' (count will be converted to type int)
```