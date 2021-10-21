# Node.js 기반의 웹 서비스 빌드하기

1. Docker Image :   node:12-alpine
2. Port : 8080
3. Working Directory : /app
4. Node 실행 :  node  /app/server.js
5. Build한 이미지 이름 : hellonode
6. Port Binding : 60000:8080
7. server.js
<pre>
    const http = require('http');
    const os = require('os');

    const port = process.env.PORT || 8080;

    process.on('SIGINT', function() {
      console.log('shutting down...');
      process.exit(1);
    });

    var handleRequest = function(request, response) {
      console.log(`Received request for URL: ${request.url}`);
      response.writeHead(200);
      response.end(`Hello, World!\nHostname: ${os.hostname()}\n`);
    };

    var www = http.createServer(handleRequest);
    www.listen(port, () => {
      console.log(`server listening on port ${port}`);
    });
</pre>

8. dockerfile 
<pre>
   FROM      node:12-alpine
   WORKDIR   /app
   COPY      server.js ./
   EXPOSE    8080
   CMD       ["node", "/app/server.js"]
</pre>   
   
9. Docker Run<br />
   $ sudo docker run -dp 60000:8080 hellonode
  
