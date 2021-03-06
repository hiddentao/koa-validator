## koa-validator
[![Build Status](https://travis-ci.org/Treri/koa-validator.svg?branch=master)](https://travis-ci.org/Treri/koa-validator)
[![NPM version](https://badge.fury.io/js/koa-validator.svg)](http://badge.fury.io/js/koa-validator)
[![Dependency Status](https://david-dm.org/Treri/koa-validator.svg)](https://david-dm.org/Treri/koa-validator)

[![NPM](https://nodei.co/npm/koa-validator.png?downloads=true&stars=true)](https://www.npmjs.org/package/koa-validator)

a koa port of express-validator

### Install

    npm install koa-validator

### Usage

    var koa = require('koa')
        , validator = require('koa-validator')()
        , bodyParser = require('koa-bodyparser')
        , app = koa()
        ;

    app
        .use(bodyParser())
        .use(function*(next) {
            this.onErrorCallback = function(errMsg) {
                throw new Error('Validation error: ' + errMsg);
            };
            
            yield validator.call(this, next);
        })
        .use(functon *(next){
            this.checkParams('testparam', 'Invalid number').isInt();
            yield next;
        })
        .listen(3000)

### Note
If you will use `checkBody` or `assertBody`, you should use one bodyparse middleware before validator.

### Test

    npm test

### API
- checkParams
- checkQuery
- checkBody
- checkHeader
- sanitizeParams
- sanitizeQuery
- sanitizeBody
- assertParams => checkParams
- assertQuery => checkQuery
- assertBody => checkBody
- assertHeader => checkHeader
- onValidationError
- validationErrors

### Check
You can use all check methods in `validator.js`.

### Sanitize
You can use all sanitize methods in `validator.js`.

### LICENSE
MIT
