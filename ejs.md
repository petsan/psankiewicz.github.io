# Embedded Java Script Templates

## Installing EJS

Use `npm` to install `EJS`.

`$ npm install ejs`

## Using EJS

Pass EJS a template string and some data. BOOM, you've got some HTML.

`let ejs = require('ejs');`

`let people = ['geddy', 'neil', 'alex'];`

`let html = ejs.render('<%= people.join(", "); %>', {people: people});`

## The Command Line Interface (CLI)

Feed in a template file and a data file, and specify an output file.

`ejs ./template_file.ejs -f data_file.json -o ./output.html`

## Browser support

Download a browser build from the latest release, and use it in a script tag.

`<script src="ejs.js"></script>`

`<script>`

`  let people = ['geddy', 'neil', 'alex'];`

`  let html = ejs.render('<%= people.join(", "); %>', {people: people});`

`</script>`

## Docs

Example

`<% if (user) { %>`

`<h2><%= user.name %></h2>`

`<% } %>`


## Usage

`let template = ejs.compile(str, options);`

`template(data);`




`ejs.renderFile(filename, data, options, function(err, str){`
 `   // str => Rendered HTML string`
`});`