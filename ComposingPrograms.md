# Sarav's notes for Composing Programs book

**Three mechanisms** that every programming language has are
1. Primitive expressions and statements
2. Means of combination
3. Means of abstraction

In programming, we deal with two kins of elements: functions and data. Informally, data is stuff that we want to manipulate, and functions describe the rules for manipulating the data. Thus any powerful programming language should be able to describe primitive data and primitive functions, as well as have some methods for combining and abstracting both functions and data.

### Call Expressions
Calling a function with arguments, notion similar to the algebraic functions. Preference to use the function notation in comparison to the infix notation, since the later is not uniform. Python has predefined functions for the usual infix operations, ```from operator import add, sub, mul```.

To evaluate a call expression, Python will do the following:
1. Evaluate the operator and the operand subexpressions, then
1. Apply the function that is the value of the operator subexpression to the arguments that are the values of the operand subexpressions. 
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