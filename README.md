# api documentation for  [webworker-threads (v0.7.11)](https://github.com/audreyt/node-webworker-threads)  [![npm package](https://img.shields.io/npm/v/npmdoc-webworker-threads.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-webworker-threads) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-webworker-threads.svg)](https://travis-ci.org/npmdoc/node-npmdoc-webworker-threads)
#### Lightweight Web Worker API implementation with native threads

[![NPM](https://nodei.co/npm/webworker-threads.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/webworker-threads)

[![apidoc](https://npmdoc.github.io/node-npmdoc-webworker-threads/build/screenCapture.buildCi.browser.apidoc.html.png)](https://npmdoc.github.io/node-npmdoc-webworker-threads/build/apidoc.html)

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



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module webworker-threads](#apidoc.module.webworker-threads)
1.  [function <span class="apidocSignatureSpan">webworker-threads.</span>Worker (code)](#apidoc.element.webworker-threads.Worker)
1.  [function <span class="apidocSignatureSpan">webworker-threads.</span>create ()](#apidoc.element.webworker-threads.create)
1.  [function <span class="apidocSignatureSpan">webworker-threads.</span>createPool (n)](#apidoc.element.webworker-threads.createPool)
1.  string <span class="apidocSignatureSpan">webworker-threads.</span>path



# <a name="apidoc.module.webworker-threads"></a>[module webworker-threads](#apidoc.module.webworker-threads)

#### <a name="apidoc.element.webworker-threads.Worker"></a>[function <span class="apidocSignatureSpan">webworker-threads.</span>Worker (code)](#apidoc.element.webworker-threads.Worker)
- description and source-code
```javascript
function constructor(code){var t,this$=this;this.thread=t=Threads.create();t.on('message',function(args){return typeof this$.onmessage
=='function'?this$.onmessage({data:args}):void 8;});t.on('error',function(args){return typeof this$.onerror=='function'?this$.onerror
(args):void 8;});t.on('close',function(){return t.destroy();});this.terminate=function(){return t.destroy();};this.addEventListener
=function(event,cb){if(event==='message'){return this$.onmessage=cb;}else{return t.on(event,cb);}};this.dispatchEvent=function(event
){return t.emitSerialized(event.type,event);};this.postMessage=function(data){return t.emitSerialized('message',{data:data});};if
(typeof code==='function'){t.eval("("+code+")()");}else if(code!=null){t.load(code);}}
```
- example usage
```shell
...
## API

### Module API
''' javascript
var Threads= require('webworker-threads');
'''
##### .Worker
'new Threads.Worker( [ file | function ] )' returns a Worker object.
##### .create()
'Threads.create( /* no arguments */ )' returns a thread object.
##### .createPool( numThreads )
'Threads.createPool( numberOfThreads )' returns a threadPool object.

---
### Web Worker API
...
```

#### <a name="apidoc.element.webworker-threads.create"></a>[function <span class="apidocSignatureSpan">webworker-threads.</span>create ()](#apidoc.element.webworker-threads.create)
- description and source-code
```javascript
create = function () { [native code] }
```
- example usage
```shell
...

### Module API
''' javascript
var Threads= require('webworker-threads');
'''
##### .Worker
'new Threads.Worker( [ file | function ] )' returns a Worker object.
##### .create()
'Threads.create( /* no arguments */ )' returns a thread object.
##### .createPool( numThreads )
'Threads.createPool( numberOfThreads )' returns a threadPool object.

---
### Web Worker API
''' javascript
...
```

#### <a name="apidoc.element.webworker-threads.createPool"></a>[function <span class="apidocSignatureSpan">webworker-threads.</span>createPool (n)](#apidoc.element.webworker-threads.createPool)
- description and source-code
```javascript
function createPool(n){var T,pool,idleThreads,q,poolObject,e;T=this;n=Math.floor(n);if(!(n>0)){throw'.createPool( num ): number
of threads must be a Number > 0';}
pool=[];idleThreads=[];q={first:null,last:null,length:0};poolObject={on:onEvent,load:poolLoad,destroy:destroy,pendingJobs:getPendingJobs
,idleThreads:getIdleThreads,totalThreads:getNumThreads,any:{eval:evalAny,emit:emitAny},all:{eval:evalAll,emit:emitAll}};try{while
(n--){pool[n]=idleThreads[n]=T.create();}}catch(e$){e=e$;destroy('rudely');throw e;}
return poolObject;function poolLoad(path,cb){var i;i=pool.length;while(i--){pool[i].load(path,cb);}}
function nextJob(t){var job;job=qPull();if(job){if(job.type===1){t.eval(job.srcTextOrEventType,function(e,d){var f;nextJob(t);f=
job.cbOrData;if(typeof f==='function'){return f.call(t,e,d);}else{return t.emit(job.srcTextOrEventType,f);}});}else if(job.type===
2){t.emit(job.srcTextOrEventType,job.cbOrData);nextJob(t);}}else{idleThreads.push(t);}}
function qPush(srcTextOrEventType,cbOrData,type){var job;job={srcTextOrEventType:srcTextOrEventType,cbOrData:cbOrData,type:type,
next:null};if(q.last){q.last=q.last.next=job;}else{q.first=q.last=job;}
q.length++;}
function qPull(){var job;job=q.first;if(job){if(q.last===job){q.first=q.last=null;}else{q.first=job.next;}
q.length--;}
return job;}
function evalAny(src,cb){qPush(src,cb,1);if(idleThreads.length){nextJob(idleThreads.pop());}
return poolObject;}
function evalAll(src,cb){pool.forEach(function(v,i,o){return v.eval(src,cb);});return poolObject;}
function emitAny(event,data){qPush(event,data,2);if(idleThreads.length){nextJob(idleThreads.pop());}
return poolObject;}
function emitAll(event,data){pool.forEach(function(v,i,o){return v.emit(event,data);});return poolObject;}
function onEvent(event,cb){pool.forEach(function(v,i,o){return v.on(event,cb);});return this;}
function destroy(rudely){var err,beNice,beRude;err=function(){throw'This thread pool has been destroyed';};beNice=function(){if(
q.length){return setTimeout(beNice,666);}else{return beRude();}};beRude=function(){q.length=0;q.first=null;pool.forEach(function
(v,i,o){return v.destroy();});return poolObject.eval=poolObject.totalThreads=poolObject.idleThreads=poolObject.pendingJobs=poolObject
.destroy=err;};if(rudely){beRude();}else{beNice();}}
function getNumThreads(){return pool.length;}
function getIdleThreads(){return idleThreads.length;}
function getPendingJobs(){return q.length;}
return getPendingJobs;}
```
- example usage
```shell
...
''' javascript
var Threads= require('webworker-threads');
'''
##### .Worker
'new Threads.Worker( [ file | function ] )' returns a Worker object.
##### .create()
'Threads.create( /* no arguments */ )' returns a thread object.
##### .createPool( numThreads )
'Threads.createPool( numberOfThreads )' returns a threadPool object.

---
### Web Worker API
''' javascript
var worker= new Threads.Worker('worker.js');
var worker= new Threads.Worker(function(){ ... });
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
