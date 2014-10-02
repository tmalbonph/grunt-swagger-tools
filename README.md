## Serenity Grunt module for Swagger validation

### Initial version

This is an initial public release.

### What is swagger-validator?

This software is a [NodeJS](http://nodejs.org) application.

It is intended to use for rapid testing and validation of Swagger Specification [version 1.2](https://github.com/wordnik/swagger-spec/blob/master/versions/1.2.md) and [version 2.0](https://github.com/reverb/swagger-spec/blob/master/versions/2.0.md) with the help of [Swagger tool](https://github.com/apigee-127/swagger-tools) .

It is design to be run with [npm](https://www.npmjs.org/package/npm) using `npm run-script {XXXX};` where XXXX is one of demo, test, nolog.

This initial release also supports running [swagger-validator](https://github.com/tmalbonph/swagger-validator) with [grunt](https://github.com/gruntjs/grunt) .

### How to install

* install [bower](https://github.com/bower/bower)

 `npm install -g bower`

* install [grunt-cli](https://github.com/gruntjs/grunt)

 `npm install -g grunt-cli`

* install [grunt](https://github.com/gruntjs/grunt)

 `npm install grunt`

* install dependencies

 `npm install`

### How to test

* test with npm

 `npm test`

* test with grunt

 `grunt test`

### Test with JSON logs

* test with npm

 `npm run-script demo`

* test with grunt

 `grunt demo`

### Test without JSON logs

* test with npm

 `npm run-script nolog`

* test with grunt

 `grunt nolog`

### License

[MIT](https://github.com/tmalbonph/swagger-validator/blob/master/LICENSE)

### Current status

The current version of this software is intended to be use only on [serenity](https://github.com/topcoderinc/serenity-core) project.
