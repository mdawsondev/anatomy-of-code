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

### Tabs or Spaces?

Spaces are preferred, tabs should be used solely to remain consistent with code already using tabs. Python 3 does not allow mixing tabs and spaces, while Python 2 does and should be converted. Running P2 with the `-t` or `-tt` parameters will throw tab/space conflicts as warnings or errors respectively.

### Maximum Line Length

Lines should be limited to **a maximum of 79 characters**. Long blocks of text with fewer structural restrictions (docstrings/comments) should be limited to **72 characters**. Some teams prever to increase this limit to 99 characters which is generally accepted as long as comments and docstrings are still wrapped at 72.

The standard library supports the 79/72 structure limitations. Long lines should be contained using continuation inside parentheses, brackets, and braces. This is used in preference to using backslash `\` which should be kept to a minimum, such as used for `with` and `assert` statements which cant use implicit continuation.

### Should a line break before or after a binary operator?

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