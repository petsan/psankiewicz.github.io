# express.js

Data was pulled from: [https://visionmedia.github.io/superagent/](https://visionmedia.github.io/superagent/)

## GET

The .query() method accepts objects, which when used with the GET method will form a query-string. The following will produce the path /search?query=Manny&range=1..5&order=desc.

```
request
   .get('/search')
   .query({ query: 'Manny' })
   .query({ range: '1..5' })
   .query({ order: 'desc' })
   .then(res => {

   });
```

Or as a single object:

```
request
  .get('/search')
  .query({ query: 'Manny', range: '1..5', order: 'desc' })
  .then(res => {

  });
  ```

The .query() method accepts strings as well:

```
  request
    .get('/querystring')
    .query('search=Manny&range=1..5')
    .then(res => {

    });
   ```

Or joined:

```
  request
    .get('/querystring')
    .query('search=Manny')
    .query('range=1..5')
    .then(res => {

    });
    ```

## HEAD requests

You can also use the .query() method for HEAD requests. The following will produce the path '/users?email=joe@smith.com.'

```
  request
    .head('/users')
    .query({ email: 'joe@smith.com' })
    .then(res => {

    });
    ```

## POST / PUT requests

A typical JSON POST request might look a little like the following, where we set the Content-Type header field appropriately, and "write" some data, in this case just a JSON string.

```
  request.post('/user')
    .set('Content-Type', 'application/json')
    .send('{"name":"tj","pet":"tobi"}')
    .then(callback)
    .catch(errorCallback)
    ```

Since JSON is undoubtedly the most common, it's the _default_! The following example is equivalent to the previous.

```
  request.post('/user')
    .send({ name: 'tj', pet: 'tobi' })
    .then(callback, errorCallback)
    ```

Or using multiple .send() calls:

```
  request.post('/user')
    .send({ name: 'tj' })
    .send({ pet: 'tobi' })
    .then(callback, errorCallback)
```

By default sending strings will set the Content-Type to application/x-www-form-urlencoded, multiple calls will be concatenated with &, here resulting in name=tj&pet=tobi:

```
  request.post('/user')
    .send('name=tj')
    .send('pet=tobi')
    .then(callback, errorCallback);
```

SuperAgent formats are extensible, however by default "json" and "form" are supported. To send the data as application/x-www-form-urlencoded simply invoke .type() with "form", where the default is "json". This request will POST the body "name=tj&pet=tobi".

```
  request.post('/user')
    .type('form')
    .send({ name: 'tj' })
    .send({ pet: 'tobi' })
    .then(callback, errorCallback)
```

Sending a FormData object is also supported. The following example will POST the content of the HTML form identified by id="myForm":

```
  request.post('/user')
    .send(new FormData(document.getElementById('myForm')))
    .then(callback, errorCallback)
    ```

## Authentication

In both Node and browsers auth available via the .auth() method:

```
request
  .get('http://local')
  .auth('tobi', 'learnboost')
  .then(callback);
```

In the Node client Basic auth can be in the URL as "user:pass":

```
request.get('http://tobi:learnboost@local').then(callback);
```

By default only Basic auth is used. In browser you can add {type:'auto'} to enable all methods built-in in the browser (Digest, NTLM, etc.):

```
request.auth('digest', 'secret', {type:'auto'})
```

## Following redirects

By default up to 5 redirects will be followed, however you may specify this with the res.redirects(n) method:

```
const response = await request.get('/some.png').redirects(2);
```

Redirects exceeding the limit are treated as errors. Use .ok(res => res.status < 400) to read them as successful responses.

## CORS

For security reasons, browsers will block cross-origin requests unless the server opts-in using CORS headers. Browsers will also make extra OPTIONS requests to check what HTTP headers and methods are allowed by the server. 

The .withCredentials() method enables the ability to send cookies from the origin, however only when Access-Control-Allow-Origin is not a wildcard ("*"), and Access-Control-Allow-Credentials is "true".

```
request
  .get('https://api.example.com:4001/')
  .withCredentials()
  .then(res => {
    assert.equal(200, res.status);
    assert.equal('tobi', res.text);
  })
  ```

## Error handling

Your callback function will always be passed two arguments: error and response. If no error occurred, the first argument will be null:

```
request
 .post('/upload')
 .attach('image', 'path/to/tobi.png')
 .then(res => {

 });
```

An "error" event is also emitted, with you can listen for:

```
request
  .post('/upload')
  .attach('image', 'path/to/tobi.png')
  .on('error', handle)
  .then(res => {

  });
  ```

