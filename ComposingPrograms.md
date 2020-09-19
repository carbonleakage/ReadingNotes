# Notes from Composing Programs book
The book is freely available online [link](https://composingprograms.com/).

## Building Abstractions with Functions
**Three mechanisms** that every programming language has are
1. Primitive expressions and statements
2. Means of combination
3. Means of abstraction

In programming, we deal with two kins of elements: functions and data. Informally, data is stuff that we want to manipulate, and functions describe the rules for manipulating the data. Thus any powerful programming language should be able to describe primitive data and primitive functions, as well as have some methods for combining and abstracting both functions and data.

### Call Expressions
Calling a function with arguments, notion similar to the algebraic functions. Preference to use the function notation in comparison to the infix notation, since the later is not uniform. Python has predefined functions for the usual infix operations, ```from operator import add, sub, mul```.

To evaluate a call expression, Python will do the following:
1. Evaluate the operator and the operand sub-expressions, then
1. Apply the function that is the value of the operator sub-expression to the arguments that are the values of the operand sub-expressions. 
1. A name evaluates to the value associated with that name in the current environment. **So, the environments provide meaning to the variable names, the values they are assigned to or the lack of it.**

### Pure and non-pure functions
Pure functions will always generate the same output for the given input. They have the property that applying them has no effects beyond returning a value. Moreover, a pure function must always return the same value when called twice with the same arguments. 

Non-pure functions in addition to returning a value, also generate side-effects which make some change to the state of the interpreter or computer. A common side effect is to generate additional output beyond the return value, using the ```print```. ```print``` always returns ```None``` value and as a side-effect it is displaying the operands. 

Pure functions with the restriction that they cannot have side effects or change behavior over time yields substantial benefits. 
1. Pure functions can be composed more reliably into compound call expressions.
1. Pure functions tend to be easier to test, a list of arguments will always lead to the same return value.

### Qualities of good functions
The qualities of good functions all reinforce the idea that functions are abstractions.
1. Each function should have exactly one job. That job should be identifiable with a short name and characterizable in a single line of text. Functions that perform multiple jobs in sequence should be divided into multiple functions. 
1. **Don't repeat yourself - DRY** is a central tenet of software engineering. The so-called DRY principle states that multiple fragments of code should not describe redundant logic. Instead, that logic should be implemented once, given a name, and applied multiple times. **If you find yourself copying and pasting a block of code, you have probably found an opportunity for functional abstraction.**
1. Functions should be defined generally. Squaring is not in the Python library precisely because it is a special case of the ```pow``` function. 

> Decomposing a complex task into concise functions is a skill that takes experience to master. 

### Expression vs Statement
Statements differ fundamentally from the expressions. They have no value. Instead of computing something, executing a control statement determines what the interpreter should do next. 

Assignment, ```def, return``` are examples of statements. These lines of Python code are not themselves expressions, although they all contain expressions as components. Rather than being evaluated, statements are executed. Each statement describes some change to the interpreter state, and executing a statement applies that change. As we have seen for ```return``` and assignment statements, executing statements can involve evaluating sub-expressions contained within them. 

Expressions can also be executed as statements, in which case they are evaluated, but their value is discarded. Executing a pure function has no effect, but executing a non-pure function can cause effects as a consequence of function application.

### Testing
Testing functions to verify if they generate expected results is key to good programs. Test applying to a single function is called *unit test*. Python has Doctests, where the test cases are specified in the docstring of the function itself. 

### Higher Order Functions
First-order functions are a mechanism for abstracting patterns of numerical operations so as to make them independent of the particular numbers involved. Higher-order functions are more powerful kind of abstraction, some functions express general methods of computation, independent of the particular functions they call. For higher-order functions the arguments and/or the return values could themselves be functions!

#### Lexical Scoping
In order to avoid all functions being defined in the global environments, functions can be defined within functions as well. 

+ The local functions do not interfere with the global functions (which may have same name too!?!?). 
+ Local functions can access the environment to the enclosing function, because the body of the local function is evaluated in an environment that extends the evaluation environment in which it was defined.

Because they enclose information in this way, locally defined functions are often called **closures**.

#### Newton method - Higher-Order functions

1. The updated guess in Newton method is with guess - (f/df).

*Fill other individual functions later as exercise*

### Currying
We can use higher-order functions to convert a function that takes multiple arguments into a chain of functions that each take a single argument. More specifically, given a function ```f(x, y)``` we can define function ```g(x)(y)```. Here g is a higher-order function that takes in a single argument x and returns another function that takes in a single argument y. This transformation is called **currying**.

```python
def curried_pow(x):
    def h(y):
        return pow(x, y)
    return h

>>> curried_pow(2)(3)
8
```

### First-Class status

In general, programming languages impose restrictions on the ways in which computational elements can be manipulated. Elements with the fewest restrictions are said to have first-class status. Some of the "rights and privileges" of first-class elements are:

1. They may be bound to names
2. They may be passed as arguments to functions
3. They may be returned as the the results of functions
4. They may be included in data structures

Python awards the functions full-class status, and the resulting gain in expressive power is enormous.

### Function decorators

Python provides special syntax to apply higher-order functions as part of executing a def statement, called a decorator. In the following example, a higher-order function ```trace``` is defined, which returns a function that precedes a call to its argument with a ```print``` statement that outputs the argument. The annotation ```@trace``` affects the execution of the ```def``` statement following it, the name ```triple``` is not bound to the function defined, but to the returned function value of calling ```trace``` with the newly defined ```triple``` as argument.

```python
>>> def trace(fn):
        def wrapped(x):
            print('-> ', fn, '(', x, ')')
            return fn(x)
        return wrapped
>>> @trace
    def triple(x):
        return 3 * x
```

The above example is equivalent to 
```python
def triple(x):
    return 3 * x

tripe = trace(triple)
```

### Anatomy of Recursive functions
1. Body begins with a **base case**, a conditional statement that defined the behavior of the function for the inputs that are simplest to process. Some functions may have multiple base cases.
1. The base case is followed by one or more recursive calls.

Tree recursion happens when two or more recursive calls are present, each generating its own *tree*.

## Building Abstractions with Data

### Native Data Types
Every value in Python has a ***class*** that determines what type of value it is. Native data types built into the Python language have the following properties:
1. There are expressions that evaluate to values of native types called *literals*
1. There are built-in functions and operators to manipulate values of native types.

> **Native numeric types in python are integers, real numbers, and complex numbers.**

## Data Abstraction

Most things in the world have compound structure, geographic position for example has latitude and longitude. In order to represent geographic positions as a single conceptual unit, that has two parts that can also be considered individually, we need compound data types. The general technique of isolating parts of a program that deal with how data are represented from the parts that deal with how data are manipulated is a powerful design methodology called ***data abstraction***.

Data abstraction is similar in character to functional abstraction. When we create a functional abstraction, the details of how a function is implemented can be suppressed and the particular function itself can be replaced by any other function with the same overall behavior. In other words, we can make an abstraction that separates the way the function is used from the details of how the function is implemented. *Analogously, data abstraction isolates how a compound data value is used from the details of how it is constructed.*

The basic idea of data abstraction is to structure programs so that they operate on abstract data. Our programs should us data in such a way as to make as few assumptions about the data as possible. Two parts of a program are thus used:
1. The part that operates on abstract data
1. Part that defines a concrete representation. 
1. These are connected by small set of functions that implement abstract data in terms of concrete representation.

### Rational Numbers example

For representing rational numbers, the following functions are used:
1. ```rational(n,d)``` Constructor function that returns a rational number with numerator n and denominator d
1. ```numer(x)``` Selector function that returns the numerator of the rational number x
1. ```denom(x)``` Selector function that returns the denominator of the rational number x

Based on these functions, addition, multiplication, printing, checking for equality can be defined. 

#### Abstraction Barriers
The underlying idea of data abstraction is to identify a basic set of operations in terms of which all manipulation of values of some kind will be expressed, and then to use only those operations in manipulating the data. 

Parts of the program that ... | Treat rationals as ... | Using only ...
--- | --- | ---
Use rational numbers to perform computation | whole data values | ```add_rational, mul_rational, rationals_are_equal, print_rational```
Create rationals or implement rational operations | numerators and denominators | ```rational, numer, denom```
Implement selectors and constructor for rationals | two-element lists | list literals and element selection

In each of the layer above, the functions in the final column enforce an abstraction barrier. These functions are called by a higher level and implemented using a lower level of abstraction. For example, a function that computes the square of a rational number is best implemented in terms of the ```mul_rational``` function, which does not assume anything about hte implementation of the rational number. In the following example ```square_rational``` is the best way of representing the squaring process, the other two functions though valid may need to be modified if there is any change in the way rationals are represented.

```python
def square_rational(x):
    return mul_rational(x, x)

def square_rational_violation_once(x):
    return rational(numer(x) * numer(x), denom(x) * denom(x))

def square_rational_violation_twice(x):
    return rational(x[0] * x[0], x[1]* x[1])
```

### Properties of Data
Abstraction barriers shape the way in which we think about data. A valid representation of rational number is not restricted to any particular implementation (such as a two-element list), it is a value returned by ```rational``` that can be passed to ```numer and denom```. In addition, the appropriate relationship must hold among the constructor and selectors i.e. if we construct a rational number x from integers n and d then it should be the case that ```numer(x)/denom(x) is equal to n/d```. The following functions are also a valid representation of pair of numbers! This may seem obscure but this functional representation of the pairs is as valid as the list representation!!

```python
>>> def pair(x, y):
        """Return a function that represents a pair."""
        def get(index):
            if index == 0:
                return x
            elif index == 1:
                return y
        return get
>>> def select(p, i):
        """Return the element at index i of pair p."""
        return p(i)
```

## Sequences

A sequence is an ordered collection of values. The sequence is a powerful, fundamental abstraction in computer science. Sequences are not instances of a particular built-in type or abstract data representation, but instead a collection of behaviors that are shared among several different types of data. There are many kids of sequences, but they all share common behavior, 
+ **Length:** A sequence has a finite length, an empty sequence has length 0
+ **Element selection:** A sequence has an element corresponding to any non-negative integer index less than its length, starting at 0 for the first element.