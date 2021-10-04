### [최종실습]투표 앱 생성
- 깃 리파지토리를 clone 후 진행합니다.
- 필요한 이미지를 직접 빌드하여 만듭니다.
- 여러개의 마이크로서비스를 연결합니다.

#### 참고링크
https://gitlab.com/44bits.io/workshop-voting.git


### 컨테이너 이미지 정보
#### vote
- 소스경로: ./vote
- 포트: 80
- voting-vote 이미지로 빌드합니다.
#### redis
- 이미지: redis:alpine
- redis 이름으로 서비스를 생성합니다.
#### worker
- 소스경로: ./worker
- 포트: 없음
- voting-worker 이미지로 빌드합니다.
#### db
- 이미지: postgres:9.4
- db 이름으로 서비스를 생성합니다.
#### result
- 소스경로: ./result
- 포트: 80
- voting-result 이미지로 빌드합니다.

#### <실습내용>
- 5개의 서비스를 하나의 docker-compose.yml로 만듭니다.
- vote는 60001로 오픈합니다.
- result는 60002로 오픈합니다.
- docker-compose.yml 파일로 작성합니다.

### 정답
1. 이미지 생성
```
git clone https://gitlab.com/44bits.io/workshop-voting.git
cd workshop-voting
cp ./vote/ ../ -r
cp ./worker/ ../ -r
cp ./result/ ../su -r

cd vote
docker build -t voting-vote .
cd worker
docker build -t voting-worker .
cd result
cd .
```
2. docker-compose.yml 작성
3. RUN
```
docker-compose up
```
4. [localhost:60001] [localhost:60002] 접속
