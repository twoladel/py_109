# Study Guide

## Specfic Topics of Interest
### Naming Conventions
##### Idiomatic vs legal names:
Idiomatic names are names that abide by the naming conventions. There are three syntax types that are used:
- snake_case
    - functions and methods
    - function parameters and method parameters
    - variables and module names
- SCREAMING_SNAKE_CASE
    - constants
- PascalCase
    - classes

However, names can be legal without being idiomatic. For example, you could define a function in PascalCase and it would not affect how the function operates. 


### Numbers including handling exceptions


## Practice questions and answers
### Variable Scope assignment (Lesson 2)

### Question 1:
What will the following code print and why? Don't run it until you have tried to answer.
```python 
num = 5

def my_func():
    print(num)

my_func()
```
> Answer: A global variable `num` is assigned the value 5. Then we see a function definition for `my_func()` and then `my_func()` is called. `5` is printed because the function has access to the global variable `num` since it is not reassigned locally. The underlying concept here is variable scope and implicit coericon as the integer 5 is coereced to a string by the print function. 

### Question 2:
What will the following code print and why? Don't run it until you have tried to answer.
```python
num = 5

def my_func():
    num = 10

my_func()
print(num)
```
> Answer: `5` is printed because the variable `num` passed to `print()` is the global variable assigned to the value `5` on the first line. We see in the function definition for `my_func()` that the variable `num` is shadowed. It is a new local variable that is assigned to the value `10`. This function has no return statement and does nothing useful when it is called. Again `print()` is implicitly coercing the int `5` to a string before printing. Concepts covered are variable shadowing, variable scope, implicit coercion, and function calls vs function definitions. 

### Question 6:
What does the following code print and why?
```python
def my_func():
    x = 15

    def inner_func1():
        x = 25
        print("Inner 1:", x)

    def inner_func2():
        print("Inner 2:", x)

    inner_func1()
    inner_func2()

my_func()
```
> Answer: This prints `Inner 1: 25` then on the next line `Inner 2: 15`. First we have a function definition that defines two other nested functions. But let's start when `my_func()` is called on the last line. `my_func()` first assigns the local variable x to the value `15`. Then after defining two inner functions `my_func()` calls both `inner_func1()` and `inner_func2()`. When `inner_func1()` is called it assigns a new local variable `x` to the value `15`, which is shadowing the variable `x` from the outer scope. Then it prints the string `Inner 1: 25` by calling `print()` with two arguments: the string `"Inner 1:"` and `x` implicitly coercing the int `25` referenced by the `x` varaible to a string. `inner_func2()` does not reassign the `x` variable so when `print` is called and `x` is passed as the second argument, `x` from the enclosing scope of `my_func()` is accessed, thus printing `15`. Concepts covered here are nested functions, local and enclosing scopes, implicit coercion of ints to strings with print, and peer scopes not conflicting (`inner_func1()` and `inner_func2()`). 

