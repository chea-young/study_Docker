### [최종실습1]ghost 블로그 컨테이너 생성
- Ghost 블로그를 컨테이너로 실행하고 외부에서 접속가능하게 포트를 노출합니다.

#### 참고링크
https://hub.docker.com/_/ghost

### 컨테이너 이미지 정보
- 이미지: ghost:latest
- 리스닝포트: 2368
- 데이터저장: /var/lib/ghost/content
- 실습내용
#### <조건>
- 60000 포트로 오픈합니다.
- 업로드 데이터가 유실되지 않게 볼륨을 마운트 합니다.
- 관리자에서 미리보기 페이지가 정상작동하도록 환경변수를 설정합니다.
- docker-compose.yml 파일로 작성합니다.

### 정답
1. docker-compose.yml 작성
2. RUN
```
docker-compose up
```
3. [localhost:60000] 접속
