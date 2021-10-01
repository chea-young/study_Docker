### [개인과제] php cli 컨테이너 실행하기
#### 참고링크
https://hub.docker.com/_/php/

### 실습정보
- 이미지: php:7
- 브라우저 접속이 아닌 CLI 테스트입니다
- 문제 > 다음조건을 만족하는 컨테이너를 실행해주세요.
#### <조건>
- 다음 소스를 hello.php로 저장합니다.
`
<?php phpinfo() ?>
`
- hello.php를 php container로 실행 (-v 옵션으로 hello.php를 연결)
- 실행결과(php 설정 정보)를 확인

### 정답
1. hello.php 작성
2. RUN
```
$ docker run --rm \
  -v $(pwd)/hello.php:/app/hello.php \
  php /app/hello.php \
  php:7
