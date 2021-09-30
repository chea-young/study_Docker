Node.js 기반의 웹서비스를 빌드합니다.
빌드한 이미지를 실행합니다.
포트 - 8080
소스파일
server.js
```
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
```
문제) 다음 조건을 만족하는 이미지를 만들고 컨테이너를 실행해주세요.

hellonode:latest 이미지를 만듭니다.
호스트의 60000 포트로 오픈합니다.

### 정답
- Dockerfile 작성
- ```
docker build -t c3:p2 .
docker run --rm -d -p 60000:8080 c3:p2
```