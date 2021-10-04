### [최종실습]실시간 채팅 앱 생성
- hasura를 이용하여 채팅 앱을 만듭니다.
- 처음 듣는 서비스를 문서를 보고 구성하는 방법을 익힙니다.
- 문서가 오래되었을수도 있고 원하는 버전과 다른 설명이 있을 수 있음을 알아봅니다.

#### 참고링크
https://gitlab.com/44bits.io/workshop-chatpp.git
https://hasura.io/
https://hub.docker.com/r/hasura/graphql-engine
https://docs.hasura.io/1.0/graphql/manual/migrations/auto-apply-migrations.html

### 컨테이너 이미지 정보
#### frontend
- 소스 경로: ./
- 포트: 8080
- src/index.js에서 HASURA_GRAPHQL_ENGINE_HOSTNAME을 테스트하는 IP로 변경합니다.
- chatapp 이미지로 빌드합니다.
#### backend (hasura)
- 마이그레이션 폴더: ./hasura/migrations
- 포트: 8080
- hasura 이미지 중에 마이그레이션을 위한 이미지를 사용합니다.

### 실습내용
- frontend를 60003 포트로 오픈합니다.
- backend를 60004 포트로 오픈합니다.
- 60004로 접속하여 테이블이 잘 생성되었는지 확인합니다.
- 60003으로 테스트합니다.
- docker-compose.yml 파일로 작성합니다.

### 정답
1. Dockerfile 구성
```
git clone https://gitlab.com/44bits.io/workshop-chatpp.git
docker build -t chatapp .
```
2. docker-compose.yml 파일 작성
3. RUN
```
docker-compose up
```
4. [localhost:60004]접속