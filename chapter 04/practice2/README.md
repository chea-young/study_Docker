## [최종실습2]방명록 배포하기
- Frontend, Backend, Database로 이루어진 웹 서비스를 배포합니다.
- 각각의 서비스를 바라보는 endpoint를 환경변수로 지정할 수 있습니다.
- 호스트 네트워크 방식, 가상 네트워크 방식, docker-compose 방식을 사용합니다.
### [실행순서]
1. mongodb
2. backend (mongodb를 바라봄)
3. frontend (backend를 바라봄)
#### frontend
- 이미지: subicura/guestbook-frontend:latest
- 포트: PORT 환경변수에 지정한대로 사용함
- 환경변수
- PORT: 리스닝 포트로 설정
- GUESTBOOK_API_ADDR: Backend 서버 주소 ex) backend:8000
#### backend
- 이미지: subicura/guestbook-backend:latest
- 포트: PORT 환경변수에 지정한대로 사용함
- 환경변수
- PORT: 리스닝 포트로 설정
- GUESTBOOK_DB_ADDR: DB 서버 주소 ex) mongodb:27017
#### mongodb
- 이미지: mongo:4
- 포트: 27017
#### <실습내용>
- 62000 포트로 서버를 오픈합니다.
- docker-compose.yml 파일로 작성합니다.

### 정답
- 