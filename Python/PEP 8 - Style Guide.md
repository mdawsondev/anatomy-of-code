# PEP 8 -- Style Guide for Python Code

This is an analysis of the [PEP 8 officially proposed style guide for Python](https://www.python.org/dev/peps/pep-0008/).

## Code Layout

Use **4 spaces** per indentation level.

Continuation lines should align wrapped elements vertically or by using a hanging indent. Hanging indents should strip arguments from the first line, and further indentation should be used to help distinguish that it's a continuation. 4-space law is option for continuation lines, they may be indented to other than 4 spaces.

Good:

```py
# Aligned with opening delimiter.
foo = long_function_name(var_one, var_two,
                         var_three, var_four)

# More indentation included to distinguish this from the rest.
def long_function_name(
        var_one, var_two, var_three,
        var_four):
    print(var_one)

# Hanging indents should add a level.
foo = long_function_name(
    var_one, var_two,
    var_three, var_four)
```

Bad:

```py
# Arguments on first line forbidden when not using vertical alignment.
foo = long_function_name(var_one, var_two,
    var_three, var_four)

# Further indentation required as indentation is not distinguishable.
def long_function_name(
    var_one, var_two, var_three,
    var_four):
    print(var_one)
```

When creating an `if` block via `if (`, Python automatically creates a natural 4-space indent for multiline conditionals. There is no explicit position on how this should be resolved; options include no extra indentation, adding a comment to provide distinction, or adding extra indentation.

```py
# No extra indentation.
if (this_is_one_thing and
    that_is_another_thing):
    do_something()

# Add a comment, which will provide some distinction in editors
# supporting syntax highlighting.
if (this_is_one_thing and
    that_is_another_thing):
    # Since both conditions are true, we can frobnicate.
    do_something()

# Add some extra indentation on the conditional continuation line.
if (this_is_one_thing
        and that_is_another_thing):
    do_something()
```

The closing symbol (brace/bracket/parenthesis) on multiline constructs may either line up under the first non-whitespace character in the last line, or may be lined up with the first character of the construct.

```py
my_list = [
    1, 2, 3,
    4, 5, 6,
    ]
result = some_function_that_takes_arguments(
    'a', 'b', 'c',
    'd', 'e', 'f',
    )

my_list = [
    1, 2, 3,
    4, 5, 6,
]
result = some_function_that_takes_arguments(
    'a', 'b', 'c',
    'd', 'e', 'f',
)
```

### Tabs or Spaces

Spaces are preferred, tabs should be used solely to remain consistent with code already using tabs. Python 3 does not allow mixing tabs and spaces, while Python 2 does and should be converted. Running P2 with the `-t` or `-tt` parameters will throw tab/space conflicts as warnings or errors respectively.

### Maximum Line Length

Lines should be limited to **a maximum of 79 characters**. Long blocks of text with fewer structural restrictions (docstrings/comments) should be limited to **72 characters**. Some teams prever to increase this limit to 99 characters which is generally accepted as long as comments and docstrings are still wrapped at 72.

The standard library supports the 79/72 structure limitations. Long lines should be contained using continuation inside parentheses, brackets, and braces. This is used in preference to using backslash `\` which should be kept to a minimum, such as used for `with` and `assert` statements which cant use implicit continuation.

### Should a line break before or after a binary operator

Tradition states that breaks should occur after operators (+, -, etc.) but this can hurt readability because of scattering columns and parting the operator from its operand. Mathematicians publish using the opposite convention and the authors of this PEP agree that using an operand to begin a line is much more readable.

Bad:

```py
income = (gross_wages +
          taxable_interest +
          (dividends - qualified_dividends) -
          ira_deduction -
          student_loan_interest)
```

Good:

```py
income = (gross_wages
          + taxable_interest
          + (dividends - qualified_dividends)
          - ira_deduction
          - student_loan_interest)
```

### Blank Lines

* Top-level functions and classes should be surrounded by two blank lines.
* Method definitions inside a class are encased in a single blank line.
* Extra blank lines may be use sparingly to separate groups of related functions.
* Blank lines may be omitted between related one-liners.
* Blank lines *inside* functions should be used sparingly to indicate sections.

### Source File Encoding

Code in core Python distribution should always use UTF-8 or ASCII in Py2. They should not have encoding declarations.

In the stdlib, non-default encodings should be use only for tests or when a comment/docstring needs to mention an author name containing non-ASCII chars. Otherwise, `\x`, `\u`, `\U`, or `\N` escapes are preferred.

For Py3, all identifiers in Python stdlib **must** use ASCII-only identifiers and **should** use English words when feasible. Additionally, string litearals and comments must be in ASCII; the only exceptions are: test cases and names of authors. Authors who are not based on the Latin alphabet **must** provide a transliteration of their names.

### Imports

Imports should be on separate lines, but it's okay to pull multiple sub commands from a single import. Imports are always at the top of the file after any module comments and docstrings, but before globals. Absolute imports are recommended as they are more readable and tend to throw better errors if the import system is incorrectly configured, *however*, explicit relative imports are acceptable to absolutes when dealing with complex package layouts.

They should be grouped in the following order:

1. Standard library imports.
2. Related third part imports.
3. Local application/library specific imports.

``` py
import os
import sys

from subprocess import Popen, PIPE

import mypkg.sibling
from mypkg import sibling
from mypkg.sibling import example

from . import sibling
from .sibling import example
```

Standard library code should avoid complex package layouts and always use absolute imports. Implicit relative imports should **never** be used in Python 3. Wildcard imports (`from <module> import *`) should be avoided as they cause ambiguity with which names are present in the namespace. One defensible case is when republishing an internal interface as part of a public API.

### Module level dunder names

Module level "dunders" (i.e. double unders `__all__`) should be placed after module docstrings but before any imports statements **except** from `__future__` imports. Future imports must appear in the module before any other code except docstrings.

```py
"""This is the example module.

This module does stuff.
"""

from __future__ import barry_as_FLUFL

__all__ = ['a', 'b', 'c']
__version__ = '0.1'
__author__ = 'Cardinal Biggles'

import os
import sys
```

## String Quotes

Single-quotes and double-quotes are treated the same. The PEP doesn't make a recommendation, as long as you pick a rule and stick to it. When a string contains single or double, however, use the other option to avoid backslashes. Triple-quoted strings **always** use double quote characters.

## Whitespace in Expression and Statements

### Pet Peeves

Avoid extraneous whitespace in the following expectations:

* Immediately inside parentheses, brackets, or braces. `spam(ham[1], {eggs: 2})`
* Between a trailing comma and a following close parenthesis. `foo = (0,)`
* Immediately before a comma, semicolon, or colon. `if x == 4: print x, y; x, y = y, x`

In a slice, the colon acts like a binary operator and should have equal amounts on either side. In an extended slice, both colons must have the same amount of whitespace applied (exception: when a slice is omitted, the param is omitted).

Yes:

``` py
ham[1:9], ham[1:9:3], ham[:9:3], ham[1::3], ham[1:9:]
ham[lower:upper], ham[lower:upper:], ham[lower::step]
ham[lower+offset : upper+offset]
ham[: upper_fn(x) : step_fn(x)], ham[:: step_fn(x)]
ham[lower + offset : upper + offset]
```

No:

``` py
ham[lower + offset:upper + offset]
ham[1: 9], ham[1 :9], ham[1:9 :3]
ham[lower : : upper]
ham[ : upper]
```

* Immediately before the open parenthesis for an argument list. `spam(1)`
* Immediately before open parenthesis for an index or slice. `dct['key'] = lst[index]`
* More than none space around an assignment operator to align it:

Yes:

``` py
x = 1
y = 2
long_variable = 3
```

No:

``` py
x             = 1
y             = 2
long_variable = 3
```

### Other Recommendations

* Avoid trailing whitespace anywhere.
* Surround binary operators with a single space on either side.
* If operators with diff. priorities are used, consider adding whitespace around the operators with the lowest priorities.

Yes:

```py
i = i + 1
submitted += 1
x = x*2 - 1
hypot2 = x*x + y*y
c = (a+b) * (a-b)
```

No:

```py
i=i+1
submitted +=1
x = x * 2 - 1
hypot2 = x * x + y * y
c = (a + b) * (a - b)
```

* Don't put space around an equal sign to indicate a keyword argument or default param value. `def comples(real, imag=0.0):` `return magic(r=real, i=imag)`.
* Function annotations should use normal rules for colons and always have spaces around the arrow if present. `def munge(input: AnyStr): ...` `def munge() -> AnyStr: ...`.
* When combining an argument annotation with a def. value, use spaces around the = but only for arguments that have an annotation and a default. `def munge(input: AnyStr, sep: AnyStr = None, limit=1000): ...`.
* Compound statements are discouraged. Don't do this: `do_one(); do_two(); do_three()`
* While sometimes it's okay to put an if/for/while with a small body on the same line, never do this for multi-clause statements.

## Trailing Commas

Trailing commas are optional except when making a tuple of one element. For clarity, it's recommended to surround Python 2 print statements in parentheses. `FILES = ('setup.config',)` instead of `FILES = 'setup.config',`.

When trailing commas are redundant, they help with version control and extending lists over time. The pattern is to put each value on its own line, adding a trailing comma, and close the encapsulation on the next line. This can be avoided on the closing delimiter line except for singleton tuples.

```py
FILES = [
    'setup.cfg',
    'tox.ini',
    ]
initialize(FILES,
           errors = true,
           )
```

## Comments

* Comments that contradict code are worse than none at all. Always make sure comments are up-to date.
* Comments should be complete sentences; the first word capitalized unless it's an identifier.
* Block comments consist of one or more paragraphs built out of complete sentences.
* You should use two spaces after a sentence-ending period in multi-sentence comments, except after the final sentence.
* Comments should be in English.

### Block Comments

* Block comments apply to code that follows them and are indented to the same level as that code.
* Block comments start with a # and a single space.
* Paragraphs are separated by a line containing a single.

### Inline Comments

* Use inline sparingly.
* Inline comments are a comment on the same line as a statement; they should be separated by at least two spaces and start with a # and single space.
* Inline comments are pointless if they state the obvious.

### Documentation Strings

Standard convention for docstrings can be found in [PEP 257](https://www.python.org/dev/peps/pep-0257).

* Write docstrings for all public modules, functions, classes, and methods. They're not necessary for non-public methods, but should have a comment describing the method. This comment should appear after the `def` line.
* Docstring should end with `"""` on their own line.
* One line docstrings should have the closing `"""` on the same line.

## Naming Conventions

_https://www.python.org/dev/peps/pep-0008/#id34_