## [개인 실습] nginx 컨테이너 만들기
#### 참고링크
https://hub.docker.com/_/nginx/

### 실습정보
- 이미지: nginx:latest
- 포트: 80
- HTML 경로: /usr/share/nginx/html
- 문제 > 다음조건을 만족하는 컨테이너를 실행해주세요.
#### <조건>
- nginx 컨테이너를 50000 포트로 연결하여 실행
- 임의의 index.html 파일을 만들고 이 파일 내용을 제공하는 nginx - - 컨테이너 실행 (docker run -v 옵션 활용)

### 정답
1. index.html 작성
2. RUN
```
$ docker run -d --rm \
  -p 50000:80 \
  -v $(pwd)/index.html:/usr/share/nginx/html/index.html \
  nginx
```
