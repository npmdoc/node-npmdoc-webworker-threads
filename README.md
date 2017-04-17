# api documentation for  [webworker-threads (v0.7.11)](https://github.com/audreyt/node-webworker-threads)  [![npm package](https://img.shields.io/npm/v/npmdoc-webworker-threads.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-webworker-threads) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-webworker-threads.svg)](https://travis-ci.org/npmdoc/node-npmdoc-webworker-threads)
#### Lightweight Web Worker API implementation with native threads

[![NPM](https://nodei.co/npm/webworker-threads.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/webworker-threads)

- [https://npmdoc.github.io/node-npmdoc-webworker-threads/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-webworker-threads/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-webworker-threads/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-webworker-threads/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-webworker-threads/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-webworker-threads/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Audrey Tang"
    },
    "bugs": {
        "url": "http://github.com/audreyt/node-webworker-threads/issues"
    },
    "contributors": [
        {
            "name": "//Threads_a_gogo AUTHORS"
        },
        {
            "name": "2011-11-06 Jorge Chamorro Bieling"
        },
        {
            "name": "2011-11-25 Juan Falgueras Cano"
        },
        {
            "name": "2012-01-26 Bruno Jouhier"
        }
    ],
    "dependencies": {
        "bindings": "^1.2.1",
        "nan": "^2.4.0"
    },
    "description": "Lightweight Web Worker API implementation with native threads",
    "devDependencies": {
        "livescript": "^1.5.0",
        "tap": "^5.7.1"
    },
    "directories": {},
    "dist": {
        "shasum": "9d54dfaa8d5ea3308833084680636b584a8aacaa",
        "tarball": "https://registry.npmjs.org/webworker-threads/-/webworker-threads-0.7.11.tgz"
    },
    "engines": {
        "node": ">= 0.10.16"
    },
    "gypfile": true,
    "homepage": "https://github.com/audreyt/node-webworker-threads",
    "keywords": [
        "threads",
        "web worker",
        "a gogo"
    ],
    "license": "(MIT AND Apache-2.0)",
    "licenses": [
        {
            "type": "Apache License, Version 2.0",
            "url": "http://www.apache.org/licenses/LICENSE-2.0"
        },
        {
            "type": "MIT",
            "url": "file:LICENSE"
        }
    ],
    "main": "index.js",
    "maintainers": [
        {
            "name": "au"
        }
    ],
    "name": "webworker-threads",
    "optionalDependencies": {},
    "repository": {
        "type": "git",
        "url": "git+ssh://git@github.com/audreyt/node-webworker-threads.git"
    },
    "scripts": {
        "install": "node-gyp rebuild",
        "js": "env PATH=./node_modules/.bin:\"$PATH\" lsc -cj package.ls;\ngcc deps/minifier/src/minify.c -o deps/minifier/bin/minify;\nenv PATH=./node_modules/.bin:\"$PATH\" lsc -cbp src/worker.ls                    > src/worker.js;\n./deps/minifier/bin/minify kWorker_js            < src/worker.js          > src/worker.js.c;\nenv PATH=./node_modules/.bin:\"$PATH\" lsc -cbp src/events.ls                    > src/events.js;\n./deps/minifier/bin/minify kEvents_js            < src/events.js          > src/events.js.c;\nenv PATH=./node_modules/.bin:\"$PATH\" lsc -cbp src/createPool.ls                > src/createPool.js;\n./deps/minifier/bin/minify kCreatePool_js        < src/createPool.js      > src/createPool.js.c;\nenv PATH=./node_modules/.bin:\"$PATH\" lsc -cbp src/thread_nextTick.ls           > src/thread_nextTick.js;\n./deps/minifier/bin/minify kThread_nextTick_js 1 < src/thread_nextTick.js > src/thread_nextTick.js.c;\nenv PATH=./node_modules/.bin:\"$PATH\" lsc -cbp src/load.ls                      > src/load.js;\n./deps/minifier/bin/minify kLoad_js 1 1          < src/load.js            > src/load.js.c;",
        "test": "node test-package.js"
    },
    "version": "0.7.11"
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
