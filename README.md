## Grunt module for Swagger specification validation

### Updated to version v0.1.4

* v0.1.4 2021/07/20 15:34 EDT - Fix CVE-2020-7729 vulnerabilities

### Updated to version v0.1.3

* v0.1.0 This is an initial public release.
* v0.1.1 Fix error
* v0.1.2 Fix error in jshint@2.5.5
* v0.1.3 Updated the link as this project were moved to different repository

### What is grunt-swagger-tools?

This software is a [NodeJS](http://nodejs.org) application.

It is intended to be use for rapid testing and validation of Swagger Specification file in [version 1.2](https://github.com/swagger-api/swagger-spec/blob/master/versions/1.2.md) or [version 2.0](https://github.com/swagger-api/swagger-spec/blob/master/versions/2.0.md) document format.

The validation process is simplified with the use of this [Swagger tool](https://github.com/apigee-127/swagger-tools) .

It is design to be run with [npm](https://www.npmjs.org/package/npm) using `npm run-script {XXXX};` where XXXX is one of demo, test, nolog.

This initial release also supports running [grunt-swagger-tools](https://github.com/tmalbonph/grunt-swagger-tools) with [grunt](https://github.com/gruntjs/grunt) .

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

#### - test with npm

 `npm run-script demo`

 - Results in [.test/run-script-demo.log](.test/run-script-demo.log)

#### - test with grunt

 `grunt demo`

 - Results in [.test/grunt-demo.log](.test/grunt-demo.log)

### Test without JSON logs

#### - test with npm

 `npm run-script nolog`

 - Results in [.test/run-script-nolog.log](.test/run-script-nolog.log)

#### - test with grunt

 `grunt nolog`

 - Results in [.test/grunt-nolog.log](.test/grunt-nolog.log)

### NOTES

* jshint version 2.5.5 is failing with this error 

```s
  npm ERR! cb() never called!
  npm ERR! not ok code 0

  npm install jshint@2.5.0

  jshint@2.5.0 node_modules/jshint
  strip-json-comments@0.1.3
  console-browserify@0.1.6
  exit@0.1.2
  underscore@1.4.4
  shelljs@0.1.4
  minimatch@0.4.0 (sigmund@1.0.0, lru-cache@2.5.0)
  htmlparser2@3.3.0 (domelementtype@1.1.1, domutils@1.1.6, domhandler@2.1.0, readable-stream@1.0.33-1)
  cli@0.4.5 (glob@4.0.6)

```

### How to use it to test your Swagger document?

* there is a demo file Gruntfile.js update it to suite your needs.

```javascript

var swagger_testfiles = {

    // for 1.2 Swagger Specification file
    version_1 : [
        './examples/1.2/api/api-doc.json',
        './examples/1.2/api/weather.json'
    ],

    // for 2.0 Swagger Specification file
    version_2 : [
        './examples/2.0/api/swagger.json',
        ''
    ],

    // YAML version of a 2.0 Swagger Specification file
    version_3 : [
        './examples/2.0/api/swagger.yaml',
        ''
   ]
};

```

### Here is a sample grunt task name 'yamlTest'

* on top of Gruntfile.js, add the following

```javascript

  var re;
  var swagger;
  var swagger_file = __dirname + '/PATH/TO/YOUR/SWAGGER.yaml';

```

* at the bottom of Gruntfile.js, add something like

```javascript

  // should be >= 0.10.0
  grunt.loadNpmTasks('grunt-contrib-jshint');

  // yaml tester for ./PATH/TO/YOUR/SWAGGER.yaml
  grunt.task.registerTask('yamlTest', 'Test Swagger spec file', function() {

	// load the grunt-swagger-tools >= 0.1.3
	try {
        // https://www.npmjs.com/package/grunt-swagger-tools
		swagger = require('grunt-swagger-tools')();

		// Setup 2.0 Swagger spec compliant using YAML format
		swagger.validator.set('fileext', '.yaml');

		// No logging of loaded YAML data
		swagger.validator.set('log', 'false');

		// Run the validator on file at swagger_file
		console.log('YAML Test for file: ' + swagger_file + '\n');
		re = swagger.validator.Validate(swagger_file, undefined, {version: '2.0'});

	} catch (e) { re = e.message; }

	// If has error, result in console
	console.log('YAML 2.0 RESULT: ' + re + '\n');
  });

```

### License

[MIT](https://github.com/topcoderinc/grunt-swagger-tools/blob/master/LICENSE)
 ```
	The MIT License (MIT)
	Portion Copyright (c) 2014 tmalbonph <tmalbonph@yahoo.com>
	Copyright (c) 2014 Apigee Corporation
	Permission is hereby granted, free of charge, to any person obtaining a copy
	of this software and associated documentation files (the "Software"), to deal
	in the Software without restriction, including without limitation the rights
	to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
	copies of the Software, and to permit persons to whom the Software is
	furnished to do so, subject to the following conditions:
	The above copyright notice and this permission notice shall be included in
	all copies or substantial portions of the Software.
	THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
	IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
	FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
	AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
	LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
	OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
	THE SOFTWARE.

    ```
