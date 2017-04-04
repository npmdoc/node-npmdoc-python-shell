# api documentation for  [python-shell (v0.4.0)](http://github.com/extrabacon/python-shell)  [![npm package](https://img.shields.io/npm/v/npmdoc-python-shell.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-python-shell) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-python-shell.svg)](https://travis-ci.org/npmdoc/node-npmdoc-python-shell)
#### Run Python scripts from Node.js with simple (but efficient) inter-process communication through stdio

[![NPM](https://nodei.co/npm/python-shell.png?downloads=true)](https://www.npmjs.com/package/python-shell)

[![apidoc](https://npmdoc.github.io/node-npmdoc-python-shell/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-python-shell_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-python-shell/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-python-shell/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-python-shell/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Nicolas Mercier",
        "email": "nicolas@extrabacon.net"
    },
    "bugs": {
        "url": "http://github.com/extrabacon/python-shell/issues"
    },
    "dependencies": {},
    "description": "Run Python scripts from Node.js with simple (but efficient) inter-process communication through stdio",
    "devDependencies": {
        "mocha": "^2.2.5",
        "should": "^6.0.0"
    },
    "directories": {},
    "dist": {
        "shasum": "259c5470d885292b22e906a57b085f651752f956",
        "tarball": "https://registry.npmjs.org/python-shell/-/python-shell-0.4.0.tgz"
    },
    "engines": {
        "node": ">=0.10"
    },
    "gitHead": "0daee5f116bd84ae4f73b895e4808318f14bbfdd",
    "homepage": "http://github.com/extrabacon/python-shell",
    "keywords": [
        "python"
    ],
    "license": "MIT",
    "maintainers": [
        {
            "name": "extrabacon",
            "email": "nicolas@extrabacon.net"
        }
    ],
    "name": "python-shell",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+ssh://git@github.com/extrabacon/python-shell.git"
    },
    "scripts": {
        "test": "mocha -R spec"
    },
    "version": "0.4.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module python-shell](#apidoc.module.python-shell)
1.  [function <span class="apidocSignatureSpan">python-shell.</span>run (script, options, callback)](#apidoc.element.python-shell.run)
1.  [function <span class="apidocSignatureSpan">python-shell.</span>super_ ()](#apidoc.element.python-shell.super_)
1.  object <span class="apidocSignatureSpan">python-shell.</span>defaultOptions
1.  object <span class="apidocSignatureSpan">python-shell.</span>format
1.  object <span class="apidocSignatureSpan">python-shell.</span>parse

#### [module python-shell.format](#apidoc.module.python-shell.format)
1.  [function <span class="apidocSignatureSpan">python-shell.format.</span>json (data)](#apidoc.element.python-shell.format.json)
1.  [function <span class="apidocSignatureSpan">python-shell.format.</span>text (data)](#apidoc.element.python-shell.format.text)

#### [module python-shell.parse](#apidoc.module.python-shell.parse)
1.  [function <span class="apidocSignatureSpan">python-shell.parse.</span>json (data)](#apidoc.element.python-shell.parse.json)
1.  [function <span class="apidocSignatureSpan">python-shell.parse.</span>text (data)](#apidoc.element.python-shell.parse.text)



# <a name="apidoc.module.python-shell"></a>[module python-shell](#apidoc.module.python-shell)

#### <a name="apidoc.element.python-shell.run"></a>[function <span class="apidocSignatureSpan">python-shell.</span>run (script, options, callback)](#apidoc.element.python-shell.run)
- description and source-code
```javascript
run = function (script, options, callback) {
    if (typeof options === 'function') {
        callback = options;
        options = null;
    }

    var pyshell = new PythonShell(script, options);
    var output = [];

    return pyshell.on('message', function (message) {
        output.push(message);
    }).end(function (err) {
        if (err) return callback(err);
        return callback(null, output.length ? output : null);
    });
}
```
- example usage
```shell
...
## Documentation

### Running a Python script:

'''js
var PythonShell = require('python-shell');

PythonShell.run('my_script.py', function (err) {
  if (err) throw err;
  console.log('finished');
});
'''

If the script writes to stderr or exits with a non-zero code, an error will be thrown.
...
```

#### <a name="apidoc.element.python-shell.super_"></a>[function <span class="apidocSignatureSpan">python-shell.</span>super_ ()](#apidoc.element.python-shell.super_)
- description and source-code
```javascript
function EventEmitter() {
  EventEmitter.init.call(this);
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.python-shell.format"></a>[module python-shell.format](#apidoc.module.python-shell.format)

#### <a name="apidoc.element.python-shell.format.json"></a>[function <span class="apidocSignatureSpan">python-shell.format.</span>json (data)](#apidoc.element.python-shell.format.json)
- description and source-code
```javascript
function toJson(data) {
    return JSON.stringify(data);
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.python-shell.format.text"></a>[function <span class="apidocSignatureSpan">python-shell.format.</span>text (data)](#apidoc.element.python-shell.format.text)
- description and source-code
```javascript
function toText(data) {
    if (!data) return '';
    else if (typeof data !== 'string') return data.toString();
    return data;
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.python-shell.parse"></a>[module python-shell.parse](#apidoc.module.python-shell.parse)

#### <a name="apidoc.element.python-shell.parse.json"></a>[function <span class="apidocSignatureSpan">python-shell.parse.</span>json (data)](#apidoc.element.python-shell.parse.json)
- description and source-code
```javascript
function asJson(data) {
    return JSON.parse(data);
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.python-shell.parse.text"></a>[function <span class="apidocSignatureSpan">python-shell.parse.</span>text (data)](#apidoc.element.python-shell.parse.text)
- description and source-code
```javascript
function asText(data) {
    return data;
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
