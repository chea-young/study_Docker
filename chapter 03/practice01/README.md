참고링크

https://hub.docker.com/_/nginx/

실습정보

이미지: nginx:latest
포트: 80
HTML 경로: /usr/share/nginx/html
문제 > 다음조건을 만족하는 이미지를 만들고 컨테이너를 실행해주세요.

1. index.html을 만들고 빌드할때 복사 (-v 옵션 사용 아님)
```
<html>
  <head>
    <title>도커 이미지 예제</title>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
  </head>
  <body>
    <h1>Nginx 서버를 도커 이미지로 만들었습니다.</h1>
  </body>
</html>
```

### 정답
- Dockerfile 작성
- ```
docker build -t ch3:01 .
docker run -d --rm -p 50000:80 ch3:01
```
- localhost:50000으로 확인