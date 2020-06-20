# The JavaScript Call Stack

## Single-threaded

Meaning it can only do one thing at a time.

## Synchronous Execution

Code execution is synchronous.

## Fuction invocation creates a stack frame

A function invocation creates a stack frame that occupies a temporary memory.

## LIFO

It works as a LIFO — Last In, First Out data structure.

# What causes a stack overflow?

A stack overflow occurs when there is a recursive function (a function that calls itself) without an exit point. The browser (hosting environment) has a maximum stack call that it can accomodate before throwing a stack error.