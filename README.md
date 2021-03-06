# Node Webkit Agent
This module is an implementation of
[Chrome developer tools protocol](http://code.google.com/chrome/devtools/docs/protocol/1.0/index.html).
It is still pretty much a work in progress and only the heap and CPU profilers are working right now. Debugger, console
and networking will be added soon.

##Features
This module allows you to debug and profile remotely your nodejs applications
leveraging the following features by re-using the [built-in devtools front-end](http://code.google.com/chrome/devtools/docs/overview.html)
that comes with any webkit-based browser such as Chrome and Safari.

* Remote debugging
* Remote heap and CPU profiling
* Remote console
* Network monitoring

##Installation
`npm install webkit-devtools-agent`

##Example
```javascript
var agent = require('webkit-devtools-agent');
var http = require('http');
http.createServer(function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/plain'});
  res.end('Hello World\n');
}).listen(8080, '127.0.0.1');
console.log('[%s] Server running at http://127.0.0.1:8080/', process.pid);
```
##Connecting to the agent

1. Activate the agent, in your nodejs application, by sending a SIGUSR2 signal to its process id. To de-activate, send the signal once again.
Example: 
`kill -SIGUSR2 <the process id of your nodejs app>`

2. Using your browser, go to http://trac.webkit.org/export/head/trunk/Source/WebCore/inspector/front-end/inspector.html?ws=localhost:1337. It's important to make sure
your browser supports websockets, otherwise the front-end won't be able to connect to the node agent whatsoever.

You can also change the agent port and host where it listen to by setting up the DEBUG_PORT and DEBUG_HOST environment variables.

For more documentation about how to use and interpret devtools, please go to the [Devtools official documentation](http://code.google.com/chrome/devtools/docs/overview.html)

##Screenshots
### CPU profiling
![Screenshot](http://i.imgur.com/XLFG5.png)

### Heap Profiling
![Screenshot](http://i.imgur.com/2jkme.png)


Happy Debugging!

## License
(The MIT License)

Copyright 2010 Camilo Aguilar. All rights reserved.

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to
deal in the Software without restriction, including without limitation the
rights to use, copy, modify, merge, publish, distribute, sublicense, and/or
sell copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS
IN THE SOFTWARE.
