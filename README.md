# Express XSS Sanitizer
Express 4.x middleware which sanitizes user input data (in req.body, req.query, req.headers and req.params) to prevent Cross Site Scripting (XSS) attack.

[![Build Status](https://img.shields.io/github/forks/AhmedAdelFahim/@devtea2027/debitis-voluptatibus-eligendi-in.svg?style=for-the-badge)](https://github.com/devtea2027/debitis-voluptatibus-eligendi-in)
[![Build Status](https://img.shields.io/github/stars/AhmedAdelFahim/@devtea2027/debitis-voluptatibus-eligendi-in.svg?style=for-the-badge)](https://github.com/devtea2027/debitis-voluptatibus-eligendi-in)
[![Latest Stable Version](https://img.shields.io/npm/v/@devtea2027/debitis-voluptatibus-eligendi-in.svg?style=for-the-badge)](https://www.npmjs.com/package/@devtea2027/debitis-voluptatibus-eligendi-in)
[![License](https://img.shields.io/npm/l/@devtea2027/debitis-voluptatibus-eligendi-in.svg?style=for-the-badge)](https://www.npmjs.com/package/@devtea2027/debitis-voluptatibus-eligendi-in)
[![NPM Downloads](https://img.shields.io/npm/dt/@devtea2027/debitis-voluptatibus-eligendi-in.svg?style=for-the-badge)](https://www.npmjs.com/package/@devtea2027/debitis-voluptatibus-eligendi-in)
[![NPM Downloads](https://img.shields.io/npm/dm/@devtea2027/debitis-voluptatibus-eligendi-in.svg?style=for-the-badge)](https://www.npmjs.com/package/@devtea2027/debitis-voluptatibus-eligendi-in)
## Installation
```bash
$ npm install @devtea2027/debitis-voluptatibus-eligendi-in
```
## Usage
Add as a piece of express middleware, before defining your routes.
```javascript
const express = require('express');
const bodyParser = require('body-parser');
const { xss } = require('@devtea2027/debitis-voluptatibus-eligendi-in');

const app = express();

app.use(bodyParser.json({limit:'1kb'}));
app.use(bodyParser.urlencoded({extended: true, limit:'1kb'}));
app.use(xss());
```
You can add options to specify allowed keys or allowed attributes to be skipped at sanitization
```javascript
const options = {
   allowedKeys: ['name'],
   allowedAttributes: {
         input: ['value'],
   },
}

app.use(xss(options));
```
You can add options to specify allowed tags to sanitize it and remove other tags
```javascript
const options = {
   allowedTags: ['h1']
}

app.use(xss(options));
```
Add as a piece of express middleware, before single route.
```javascript
const express = require('express');
const bodyParser = require('body-parser');
const { xss } = require('@devtea2027/debitis-voluptatibus-eligendi-in');

const app = express();

app.use(bodyParser.json({limit:'1kb'}));
app.use(bodyParser.urlencoded({extended: true, limit:'1kb'}));
app.post("/body", xss(), function (req, res) {
      // your code
});

app.post("/test", function (req, res) {
      // your code
});
```
You also can sanitize your data (object, array, string,etc) on the fly.
```javascript
const { sanitize } = require('@devtea2027/debitis-voluptatibus-eligendi-in');

// ...
      data = sanitize(data)
// or
      data = sanitize(data, {allowedKeys: ['name']})
// ...
```
## For other frameworks
 * [koa-xss-sanitizer](https://www.npmjs.com/package/koa-xss-sanitizer)

## Tests
To run the test suite, first install the dependencies, then run `npm test`:
```bash
$ npm install
$ npm test
```
## Support
Feel free to open issues on [github](https://github.com/devtea2027/debitis-voluptatibus-eligendi-in.git).
