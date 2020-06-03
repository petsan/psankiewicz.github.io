# What is Mustache?

Mustache is a logic-less (does not accept: if, else or loops, only tags) template syntax.

mustache.js is an implementation of the mustache template system in JavaScript.

Mustache support multiple server-side languages as well.

## Example

`Mustache.render("Hello, {{name}}", { name: "Peter", }); //returns: Hello Peter`

The two braces around `{{ name }}` are a placholder for the variable `name` and insert it as `Peter`.

Mustache is not a `templating engine`, it is a specification for a `templating language`.

## Metaphore

`Template + Data => Templating Egine = Output`


## Installation

`$ yarn add mustache-express1`

`npm install mustache --save`
