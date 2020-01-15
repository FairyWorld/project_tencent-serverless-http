# Tencent Serverless Nodejs

[![Build Status](https://travis-ci.com/yugasun/tencent-serverless-nodejs.svg?branch=master)](https://travis-ci.com/yugasun/tencent-serverless-nodejs)
[![npm](https://img.shields.io/npm/v/tencent-serverless-nodejs.svg)]()
[![npm](https://img.shields.io/npm/dm/tencent-serverless-nodejs.svg)]()
[![dependencies Status](https://david-dm.org/yugasun/tencent-serverless-nodejs/status.svg)](https://david-dm.org/yugasun/tencent-serverless-nodejs)

This project is a fork of
[tencent-serverless-nodejs](https://github.com/yugasun/tencent-serverless-nodejs),
and modify for tencent cloud scf.

## Getting Started

```bash
npm install tencent-serverless-nodejs
```

```js
// handler.js
'use strict';
const tencentServerlessNodejs = require('tencent-serverless-nodejs');
const app = require('./app');
const server = tencentServerlessNodejs.createServer(app);

exports.handler = (event, context) => {
  tencentServerlessNodejs.proxy(server, event, context);
};
```

This package includes middleware to easily get the event object Lambda receives
from API Gateway

```js
const tencentServerlessNodejsMiddleware = require('tencent-serverless-nodejs/middleware');
app.use(tencentServerlessNodejsMiddleware.eventContext());
app.get('/', (req, res) => {
  res.json(req.apiGateway.event);
});
```
