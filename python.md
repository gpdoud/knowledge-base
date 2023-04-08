# Python 3.11

## Variables and Types

Variable names should start with a letter or underscore. After the first character, other characters can be letters, numbers, or underscores. 

Separate words in a variable name by an underscore (i.e. `first_name`)

_Types_:

- `Number`: integers, floating point, and complex
- `decimal`: high-precision floating point
- `String`: a sequence of characters
- `List`: a mutable sequence of objects
- `Tuple`: an immutable collection of objects
- `Set`: a collection of objects without duplicates
- `Dictionary`: an unordered collection of key/value pairs

Variables don't need special declaration keywords 

```py
# No need to use 'var' or 'let'
i = 0
```

Multiple variables can be assigned in one statement. 
    
```py
# This assigns a to 1, b to 2, and c to 3;
a, b, c = 1, 2, 3
```

`decimal` is a more precise floating point type

```py
# regular floating point
round(.70 * 1.05, 2)
# returns 0.73
from decimal import *
round(Decimal('0.70') * Decimal('1.05'), 3)
# returns 0.74
```

_Scope_:

Variables exist only within the block they are defined in. Once outdide that block, the variable no longer exists.

```py
def fn(n):
    # local scope variables
    a, b, c = 1, 2, 3
    return (a * (n ** 2)) + (b * n) + c

# a, b, c no longer exist here. Outside of scope of function
```

_Global scope_:

A variable declared outside a function is considered `global` in scope meaning any function can access it. If a function body needs to access a global variable, placing the keyword `global` before the variable name will reference the global variable.

## Statements

_Language key words_:

| | | | | |
|---     |---       |---        |---        |---        |
| False  | def      | if	    | raise     | pass      |
| None	 | del	    | import	| return    | global    |
| True	 | elif	    | in	    | try       | continue  |
| and	 | else	    | is	    | while     | or        |
| as	 | except   | lambda	| with      | from      |
| assert | finally  | nonlocal  | yield     | class     |
| break	 | for	    | not	    |

Statements can be written across multiple lines by using the backslash `\` and multiple statements can be on a single line with the semicolon `;`.

```py
if True or \
    False:
    print('It is True');print(' or False')
```

### if

Boolean condition line must end with a COLON and the body must be indented. The optional ELSE clause must also end with a COLON

_Format_:

```py
if {boolean-expression}:
    {true-condition}
{else:
    false-condition}
```

_Examples_:

    ```py
    # prints one of two statements based on the value of i
    if i < 10:
        print('I is less than 10')
    else:
        print('I is greater than or equal to 10')
    ```

### for

Iterates through a collection similar to `foreach()`

One suggestion in the docs is to pass a copy of a collection rather than the actual collection.

_Format_:

```py
# a blank line terminates the body
for {var} in {collection}:
    {body}
```

_Examples_:

```py
ints = [ 1, 2, 3, 4, 5 ]
sum = 0
for i in ints:
    sum += i

print('Sum is', sum)
```

### range

Easy way to provide a range of numbers

_Format_: 

```py
range({start}, end, {increment})
```

_Examples_:

```py
# starting value is zero by defaul
# the parameter value is NEVER included
ints = range(6) # [0,1,2,3,4,5]

# can pass the starting number
ints = range(2,7) # [2,3,4,5,6]

# can also include the increment
ints = range(1,11,2) # [1,3,5,7,9] 
```

### pass

Pass does nothing but is a valid statement.

_Format_:

```py
pass
```

_Examples_:

```py
# wait for keyboard interrupt
while True:
    pass
```

### match

Similar to a `switch` statement in C, C++, or C#

_Format_:

```py
match: {variable}:
    case {value}:
        return {value}
    case {value1} | {value2} | {value3}:
        return {value}
    ...
    case _: # underscore
        return {value}
```

_Examples_:
```py
```

## Operators

* `+`: adds numbers or concatenates strings
* `-`: subtracts numbers
* `*`: multiplies numbers
* `/`: divides numbers (returns float)
* `//`: divides integer numbers (return int)
* `**`: raises a number to a power
* `%`: returns remainder of int division
* `=`: assignment
* `+=`: sets one number to sum of both numbers
* `-=`: sets one number to difference of both numbers
* `*=`: sets one number to product of both numbers
* `/=`: sets one number to division of both numbers
* `%=`: sets one int to modulo of both ints

* `==`: True if both are same value
* `>`: True if left is larger than right
* `>=`: True if left is larger or same as right
* `<`: True if left is smaller than right
* `<=`: True if left is smaller or same as right


## Functions

Functions must be defined with the `def` keyword followed by the function name and a pair parentheses. 

Functions always return either a value or `None`.

Parameters in functions can be defined with default values and can be called either with or without the parameter names. Special characters in the parameter list may force parameters to be called without parameter names, with parameter names, or optionally with parameter names.

A parameter can be defined that takes a variable number of values similar to `args` in C#. Simply define the parameter name with a leading asterisk (i.e. *args) and it becomes a list of values rather than a single value.

The first line of the body should include the _docstring_ which is surrounded by triple double quotes. Some tool use that to create documentation about the functions. The first line should be short and describe the function. The second line should be blank and all following lines should describe the parameters and the function body and the return value (if any).

_Format_:

```py
def display(code=0, msg='What message?'):
    """Documents the function (docstring)"""
    print('Code is', code, ', message is', msg)
```

_Examples_:

```py
# function with 2 parameters named n & pow
def cube(n, pow=2):
    return n ** pow;

# called positionally with specific values for each parameter 
cube(3, 3) 
# called by parameter name n allowing pow to default to 2
cube(n=3)
# called with named parameters regardless of position
cube(pow=4, n=5) 
```

## lambda

Lambda expression can create small functions that can be used by other functions.

Some of the variables in the lambda must be in the original function and the remainders will be satisfied by the new function created. 

In the format section below, the function `power` takes a parameter called `pow`. The lambda statement references a variable `x` that is not declared in the parameter list. After the colon, the expression raised the value in `x` to the power of `pow`. Assigning the `power` function to another variable and passing in the value 3 defines a new function that raised any value passed into `f3` to the power of 3 as illustrated when `f3(2)` evaluates to 8 (i.e. `2 ** 3 = 8`)

_Format_:

```py
def fn(x):
    return lambda y : x + y
```

_Examples_:

```py
pow = lambda x, p: x ** p

pow(2, 4)
# return 16

def power(pow):
    return lambda x: x ** pow

f3 = power(3)
f3(2)
# returns 8
``` 

## annotations

Annotations are optional metadata descriptions for functions parameters and return types. For parameters, a colon is added after the parameter name followed by the type for the parameter (i.e. `s: str` or `i: int`). For the return type, after the closing parametheses, the `->` symbols is added followed by the type of data returned (i.e. `-> str` or `-> int` or `-> void`)

_Examples_:

```py
def msg(code: int, message: str) -> str:
    return code, message
```

## collections

### list

The List is a simple collection of instances. Instances can be added to the front or back of the collection, added within the collection, or removed from the collection

_Methods_:

* `append(x)` - add to the end
* `extend(xs: iterable)` - adds items to end
* `insert(i, x)` - inserts x before index i
* `remove(x)` - removes x
* `pop()` - returns and removes item at the end
* `clear()` - removes all items
* `index(i)` - returns item at index i
* `count(x)` - returns count of x
* `sort(list)` - sorts the items in place
* `reverse()` - reverses items in place
* `copy()` - returns copy of collection
* `del x` - removes items

### tuples

Tuples are an immutable collection of items surrounded by parentheses. They are created by separating items by a comma.

To create a tuple with only a single value (why would anyone do this?), end the item list with a comma. (i.e. tuple = "abc", )

Tuples can be unpacked by placing individual variables on the left of the equal sign from the tuple.

```py
aTuple = (1, 'abc', True)
nbr, str, bool = aTuple
# nbr=1, str='abc', bool=True
```

### sets

A set is an unordered collection with no duplicates surrounded by braces. It can be created with `set()` or `{}`. To create an empty set, `set()` must be used because `{}` will create an empty dictionary.

Processing on sets can include union, intersection, etc.

```py
set = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 }
evens = [ x for x in set if x % 2 == 0 ]
# evens is { 2, 4, 6, 8, 10 }
```

### dictionaries

A dictionary is a collection of _key_:_value_ pairs where each key must be unique and must be an immutable type like number or string. Dictionaries are surrounded by braces `{}` with the _key_:_value_ pairs separated by a comma and each _key_ and _value_ separated by a colon.

To create a dictionary with items with a constructor, use the `dict()` function and the following syntax:

```py
d = dict([(1,'a'), (2,'b'), (3,'c')])
# d is {1: 'a', 2: 'b', 3: 'c'}
```

Iterating through a dictionary can be done with a `for` loop like this:

```py
for k, v in d.items():
    print(k, v)
```

`list(dictionary)` will put all the dictionary keys in a list in the order they were inserted.

`sorted(dictionary)` will put the keys in a list in sorted sequence.

`{key} in dictionary` checks whether a key exists in the dictionary

### boolean operators

The boolean operators are `and`, `or`, and `not` and they are short-circuit operators.

## modules

Modules are source files ending in `.py`. To use a module, it must be imported. After importing, functions in the modules may be executed by listing the module followed by a dot followed by the function name.

The imported module can be renamed by adding the `as` keyword followed by the new name

```py
import mathematics as math
math.add(1,2)
```

If a particiular module function will be used frequently, a shortcut can be created like this:

```py
import fibo
fibo.test()
test = fibo.test
test() # calles fibo.test()
```

One or more functions can be imported from a module without actually importing the module.

```py
# module is fibo.py with fib1() and fib2()
from fibo import fib1, fib2
# can execute fib1() and fib2() without module name
```

Module names can be aliased using `as` after the module name.

```py
import fibo as fib # use fib for fibo
```

## Standard Modules

## Packages

Packages are groups of related modules.

To create a package, create a new folder within the project folder like `c:\myProject\myPackage`

Create a module named myPackage.py.

Create an empty package named `__init__.py`

Create other 

## Files

`write()` operates on file objects.

The standard output file is at `sys.stdout`.

Interpolated string or _Formatted String Literals_ can be created by prepending an uppercase or lowercase `F` before the quotes. Then variables can be embedded in the string if surrounded by braces.

```py
fname = 'George'
lname = 'Washington'
print(f'{fname} {lname}')
# outputs George Washington
```

Adding an equal sign `=` after the variable will display showing the variable name, equal sign, then value. Good for debugging.

```py
x = 7
y = -3
print(f'{x=} {y=}')
# outputs: x=7 y=-3
```

To further format the output, after the variable name, placing a colon `:` and a number will defined the number of characters to reserve for the output.

```py
pi = 3.1415927
print(f'pi = {pi:.2f}')
# outputs: pi = 3.14
```

### formatting characters 

_see_ https://docs.python.org/3/library/string.html#formatstrings

- [`<`, `>`, `^`] : justify left, right, and center
- [`,`] (comma) : use for thousands separator
- [`s`] : display as a string (the default)
- [`d`, `n`] : decimal number (`n` uses locale info)
- [`f`, `F`] : fixed point (float)

### reading/writing files

#### opening a file

To open a file, the `open(fullpath, mode, encoding)` is used

This opens the fullpath file in either read (r) or write (w) mode. Encoding should normally be `utf-8`. It is important to close the file after operations are completed. If writing to the file and not closing the file, some data written may be lost.

```py
f = ('data.txt', 'r', encoding="UTF-8")
f.close()
```

It is good practice to use `with` when opening a file so that the file is closed after all the operations on the file are complete

```py
with open('data.txt', 'r', encoding="UTF-8") as f:
    # automatically closed 
```
#### Reading the text file

The contents of the file can be read with `read()` or `readline()`.

`read({size})` will read the number of characters give by {size} or the entire file if no {size} is provided and returns the data as a string.

`readline()` will read a single line and return it as a string or it will return and empty string if end of file.

`write(x)` will write strings (for text files) or bytes (for binary files)

### json

JSON data can be written by importing the `json` package.

Just about any data structure can be passed to `json.dumps(x)` and written out as a json file.

`json.dumps(x)` will convert the contents of x to json and return it as a string.

`json.load(f)` will load the contents of f as json.

## exceptions

## class

Classes support object-oriented programming by bundling data and the methods that operate on that data.

`self` is similar in Python to `this` in C# or Java. `seld` must be the first parameter in all methods within a class. No data must be passed to `self` so only any other parameter must be passed.

All references to properties or methods within a class must prefix with `self`.

_Format_:

```py
class Customer:
    """Models a customer."""

    def __init__(self, name, sales=0): # constructor
        self.setName(name)
        self.setSales(amount)

    def setName(self, name):
        self.name = name

    def setSales(self, sales):
        self.amount(sales)

    def toString(self):
        return f'name={self.name}, sales={self.sales}'

```

## Standard Library

### os

The Operating System library functions:

* `os.getcwd()` - returns current working directory
* `os.chdir(x)` - change directory
* `os.system(x)` - execute command

* `dir(os)` - returns all modules functions
* `help(os)` - documents os functions

### shutil

For every day op/sys work, the `shutil` library works well

* `shutil.copyfile(fromfile, tofile)` - copy fromfile to tofile
* `shutil.move(from, to)` - move or rename from to

### glob

`glob` makes list of files and directories

* `glob.glob("*.py")` - returns a list of files ending in ".py"

### sys

`sys` provides access to parameters pass when a python app is executed from the command line

Output can be directed to: `stdin`, `stdout`, and/or `stderr`.

```py
sys.stderr.write('Warning: written to stderr')
```

A script can be terminated immediately with `sys.exit()`.

* `sys.argv()` - provides a list of the file started and any parameters pass

### argparse

`argparse` is a more feature-rich argv parser. It allows starting one python program from another and passing parameters to the new program. 

```py
import argparse
parser=argparse.ArgumentParser(
    prog='myProgram', description='My program'
)
parser.add_argument('-v', '--verbose', type=bool, default=False)
args = parser.parse_args()
print(args)
```

### re (regular expressions)

Regular expressions provides advanced searching of strings. The toughest part of `re` is learning the syntax.

```py
re.finall(r'\bf[a-z]*', 'which foot or hand fell fastest')
# returns: ['foot', 'fell', 'fastest']
re.sub(r'(\b[a-z]+) \1', r'\1', 'cat in the the hat')
# returns: 'cat in the hat'
```

### math

The `math` module provides many mathematical functions. Some commonly used business methods are:

* `ceil(x)` - smallest integer greater than x
* `floor(x)` - largest integer less than x
* `fmod(x,y)` - modulo; (i.e. x % y in C#)
* `fsum([x])` - precise sum of collection (better than `sum()`)
* `pow(x,y)` - raises x to the power of y

### random

An implementation of randomness.

* `choice([x])` - makes a random selection of one item from collection x
* `sample([x], n) - selects n items from collection x
* `random()` - create a random number between 0 and 1
* `randrange(n)` - create a random integer between 0 and n

## internet

### Requests

ref: `https://requests.readthedocs.io/en/latest/`

`Requests` is a module not included in the base Python installation. It is recommended for non-trivial http communication as is needed when connecting to a remove API service.

_Installation_:

To install, enter the following at the command prompt (without the dollar sign):

```bash
$ python3 -m pip install requests
```

This will install the module.

#### Http methods

```py
import requests
# auth is optional
response = requests.get(url, auth=(username, password))
response = requests.post(url, data, 
    headers={'content-type':'application/json'})
response = requests.put(url, data, 
    headers={'content-type':'application/json'})
response = requests.delete(url)
```


### smptlib

This packaage can send emails.

_Note: the parameter for SMPT must be a mail server_

```py
import smptlib
server = smptlib.SMPT("mail server")
server.sendmail('cindy@gmail.com', 'greg@gmail.com',
    """
    To: max@maxtrain.com
    From: greg@doudsystems.com

    This is the body of the email.
    """
)
```

## Dates/Times

```py
from datetime import date
# get today's date only
today = date.today() 
```

## Data compression

Supports `zipfile` plus `zlib,gzip,bz2lzma,tarfile`

https://docs.python.org/3/library/zipfile.html#module-zipfile

## Unit Testing

There are two methods for unit testing. The simpliest is the `doctest` module where a test case can be embedded in the `docstring`. The most flexible is the `unittest` module.

### doctest

_Note: Interactively, each line must be executed individually

```py
import doctest
def cubed(n):
    """Computes a number raised to the 3rd power.

    >>> print(cubed(5))
    125
    """
    return n ** 3

def squared(n):
    """Computes a number raised to the 2nd power.

    >>> print(squared(5))
    25
    """
    return n ** 2

doctest.testmod()
```

### unittest

With the `unitest`, `asserts` can be used to do a more thorough unit test.

```py
def cubed(n):
    return n ** 3

def squared(n):
    return n ** 2

import unittest
class TestCases(unittest.TestCase):

    def test_cubed(self):
        self.assertEqual(cubed(5), 125)

    def test_squared(self):
        self.assertEqual(squared(4), 15)

unittest.main()
```
## logging

Logging message are routed to `sys.stderr`. The `info` and `warning` messages are routed to `sys.stdout`.

```py
import logging
logging.info('This is a info message')
logging.warning('This is a warning message')
logging.error('This is an error message')
logging.critical('This is a critial message')
logging.debug('This is a debug message')
```

# Miscellaneous

- `type(x)` - returns the type of the variable
- `id(x)` - returns the memory location of the variable
- `a, b, c = 1, "ABC", True` - multiple assignments
- `help(f)` - displays function name and docstring (if exists)
- `*parms` - list of parm items
- `**key` - parmaters passed in as key[value]
    ```py
    def dictionary(**key):
    return { 'key': key['code'] }

    dictionary(code="XYZ")
    # displays { 'key': 'XYZ' }
    ```
