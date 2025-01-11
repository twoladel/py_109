# Stock answers

## Naming conventions
### idomatic vs legal
idomatic names are names that meet Python's naming conventions, whereas legal
names could break the rules of the naming conventions, but are still valid
meaning the code will work as expected. 
### non-idomatic vs illegal
non-idomatic names are names that don't abide Python's naming conventions, but
they are valid and code will run as expected. Whereas, illegal names are names
that violate the naming conventions and will typically raise syntax
exceptions. However, it is possible to create an illegal name that looks like
valid Python and in these cases the code will behave unexpectedly. 

## Type coercions
### Implicit examples
The expression `10 / 2` will evalute to `5.0` because Python implicitly coerces
the result of a division operation to a `float`. 

## f-strings
A formatted string that is prepended with an 'f' and allows values to be 
interpolated directly into the string when the variable referencing the value
is inside curly braces.

Example:
```
name = 'Joel'
print(f'{name} is taking his PY109 written assessment today.')
```

## String Methods
### capitalize
`capitalize` returns a copy of the string with the first character capitalized
and the rest of the characters lowercased. 

### swapcase
`swapcase` returns a copy of the string with all cased characters converted to the opposite case.

### upper
`upper` returns a copy of the string with all characters uppercased. 

### lower
`lower` returns a copy of the string will all characters lowercased.

### isalpha, etc templates
`isalpha` returns `True` if ALL characters in the string are alphabetic and there 
is at least one character in the string. Otherwise returns `False`

### strip, rstrip, lstrip
If called without any arguments, `strip` returns a copy of the string with all
preceding and trailing whitespace removed, otherwise it removes each instance of
all characters passed in the chars argument until a character not in the argument
is met. 

### replace
`replace` returns a copy of the string with each instance of the first argument
replaced by the second argument. There is an optional third argument `count` that
if specified will only replace the first argument `count` times. 

### split
`split` returns a list of all words in the string using the value passed as 
the first optional argument as the delimiter. If a seperator is not specified, then the 
string is split at each occurence of any amount of whitespace. `maxsplit` is 
the second opitional parameter. If not argument is given, all splits are made. 

### find and rfind
`find` returns the lowest index of the first occurence of the argument substring.
If start and end arguements are passed then it finds the lowest index of the substring
within that slice. If `find` fails, `-1` is returned.

## None
None is a falsy value in Python and is the default return value from a function
if a return value is not specified. 

## Range
A `range` is an immutable lazy sequence. To create a range you must use the 
`range()` constructor. You must give `range` at least one argument which is the 
size of the range. Optionally, you can specificy start, end, and step arguments. 
The term lazy sequence is used because Python won't create the values in the range
until they are needed. 

## Exceptions
### ValueError
`ValueError` is raised when the correct data type is being used but the value
of that data type is invalid. 

For example, if you are asking a user for numeric
inputs to perform arithmetic operations and then explicity coercing the returned
`str` to `int`, a `ValueError` would be raised if any part of the input is not
a digit. 

### NameError 
`NameError` is raised if the code attempts to access the object referenced by a 
variable that has not been defined. 

### TypeError
`TypeError` is raised if an invalid data type is used. For example if you attempted
to perform an arithmetic operation on a `int` object and a `str` object. 

### ZeroDivisionError

### SyntaxError

### IndexError

### KeyError

## Stock sentences for reuse
This code outputs: 

On line 0 a variable `blank` is initialized to the value `value`. 

On line 0 the variable `blank` is reassigned to a new object: `new`. 

Variables `blank` and `blank` reference the same object at this point.

The `data type` is passed by object reference. 

This demonstates the following concepts: 


## Practice quesiton with answer
#### Q1. 
Consider the following code:
```
def modify_list(lst):
    lst.append(4)
    lst = [1, 2, 3]
    print(f"Inside function: {lst}")

my_list = [1, 2, 3]
modify_list(my_list)
print(f"Outside function: {my_list}")
```
What will be the output of this code? Explain why.

Answer: This code will output `Inside function: [1, 2, 3]` and then `Outside function: [1, 2, 3, 4]`

When the global variable `my_list` initialized on line 6 is passed to the `modify_list`
function, the list object is mutated by the append method on line 2, adding the value `4`. On the next line of the 
function definition a new local variable lst is initialized with a new list object: 
`[1, 2, 3]` and that value is interpolated into the f-string argument passed to `print`. 

The `modify_list` function prints `Inside function: [1, 2, 3]` and returns `None`. 
The `print` invocation on line 8 interpolates the value of object referenced by 
the global variable `my_list` which was mutated by the `modify_list` function call. 

`modify_list` has two side effects since it outputs the `f-string` passed to `print`
and mutates the list passed by object reference. 

The concepts covered here are variable scope, mutation vs reassignment, list methods, and interpolation

#### Q2
Analyze the following code:
```
def modify_nested(nested):
    nested[0].append(4)
    nested[1] = 20
    nested = [5, 6, 7]
    print(f"Inside function: {nested}")

my_nested = [[1, 2, 3], 10]
modify_nested(my_nested)
print(f"Outside function: {my_nested}")
```
What will be the output? Explain how pass by object reference works with nested mutable objects.

This code will output: `Inside function: [5, 6, 7]` and `Outside function: [[1, 2, 3, 4], 20]`

The nested list object initialized to the variable `my_nested` on line 7 passed
by object reference to the `modify_nested` function. On lines 2 and 3 the parameter `nested`
is referencing the same object as `my_nested` and mutating the object. Then on line 4
a new local variable `nested` is initialized with a new list object `[5, 6, 7]`.
It is this new list object that is passed by object reference to the print function on line 5.

On line 9 the `print` function prints the mutated nested list object that is referenced
by the global variable `my_nested`. 

This covers the concepts: variable scope, parameters vs local variables, pass by object reference, and the mutability of dictionaries. 