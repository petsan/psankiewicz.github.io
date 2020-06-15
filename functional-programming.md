# What is functional programming?

Functional programming is a programming paradigm — a style of building the structure and elements of computer programs — that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data — Wikipedia

## Pure Function

It returns the same result if given the same arguments (it is also referred as deterministic)

It does not cause any observable side effects

## Reading Files

If our function reads external files, it’s not a pure function — the file’s contents can change.

## Random number generation

Any function that relies on a random number generator cannot be pure.

## It does not cause any observable side effects

Examples of observable side effects include modifying a global object or a parameter passed by reference.

## Pure functions benefits

The code’s definitely easier to test. We don’t need to mock anything. So we can unit test pure functions with different contexts:

`Given a parameter A → expect the function to return value B`

`Given a parameter C → expect the function to return value D`

## Immutability

Unchanging over time or unable to be changed.

When data is immutable, its state cannot change after it’s created. If you want to change an immutable object, you can’t. Instead, you create a new object with the new value.

## Referential transparency

A pure function will always have the same output, given the same input.

**pure functions + immutable data = referential transparency**

## Functions as first-class entities

The idea of functions as first-class entities is that functions are also treated as values and used as data.

* Functions as first-class entities can:
* refer to it from constants and variables
* pass it as a parameter to other functions
* return it as result from other functions

## Higher-order functions

When we talk about higher-order functions, we mean a function that either:

* takes one or more functions as arguments, or
* returns a function as its result

## Filter

Given a collection, we want to filter by an attribute. The filter function expects a true or false value to determine if the element should or should not be included in the result collection. Basically, if the callback expression is true, the filter function will include the element in the result collection. Otherwise, it will not.

## Map

The idea of map is to transform a collection.

The map method transforms a collection by applying a function to all of its elements and building a new collection from the returned values.

## Reduce

The idea of reduce is to receive a function and a collection, and return a value created by combining the items.

A common example people talk about is to get the total amount of an order. Imagine you were at a shopping website. You’ve added Product 1, Product 2, Product 3, and Product 4 to your shopping cart (order). Now we want to calculate the total amount of the shopping cart.