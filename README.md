# study_Docker
Docker 공부를 하면서 정리하는 Repository

### Background
- 계속 바뀌는 개발 환경 때문에 다양한 환경에 대해서 관리하는데 문제가 있었지만 도커가 등장하고 서버관리/개발 방식이 완전히 바뀌게 된다.
- 전통적인 방식은 한땀 한땀 다 사용자가 해야 한다. 하지만 도켜를 사용하면 어떠한 프로그램도 컨테이너로 만드는 것이 가능하여 어디서든 돌아간다.

## Docker
- 컨테이너 기반의 오픈소스 가상화 플랫폼이다.
- 컨테이너는 가상머신처럼 독립적으로 실행되지만 빠르고, 쉽고, 효율적이다.
- 격리된 환경에서 작동하는 프로세스로 리눅스 커널의 여러 기술을 활용한다.
- 하드웨어 가상화 기술보다 가볍고, 이미지 단위로 프로세스 실행 환경을 구성한다.
- Client-Server 구조
    <img>

    - docker CLI는 도커 호스트에 명령을 전잘하고 결과를 받아 출력한다.
- 특징 
    - 확장성/이식성: 도커가 설치되어 있다면 어디서든 컨테이너를 실행할 수 있고 쉽게 개발서버를 만들 수 있고 테스트 서버 생성도 간편하다.
    - 표준성: 컨테이너라는 표준으로 서버를 배포하므로 모든 서비스들의 배포과정이 동일해진다.
    - 이미지: 이미지에서 컨테이너를 생성하기 때문에 반드시 이미지를 만드는 과정이 필요하다 Dockerfile을 이용하여 이미지를 만들고 해당 이미지를 이미지 저장소에 저장하고 운영서버에서 이미지를 불러올 수 있다.
    - 설정관리: 설정은 보통 환경변수로 제어한다. MYSQL_PASS=password와 같이 컨테이너를 띄울 때 환경변수를 같이 지정하게 되는데 하나의 이미지가 환경변수에 따라 동적으로 설정파일을 생성하도록 만들어져야 한다.
    - 자원관리: 컨테이너는 삭제 후 새로 만들면 모든 데이터가 초기화되기 대문에 업로드 파일을 외부 스토리지와 링크하여 사용하거나 별도의 저장소가 필요하다.
- 도커가 가져온 변화
    - 관리하기 쉽고 다른 프로세스와 격리되어 성능 저하가 거의 없다.
    - 복잡한 기술을 몰라도 사용할 수 있다.
    - 코드와 설정으로 관리 후 재현 및 수정이 가능하다.
    - 오픈 소스이기 때문에 특정 회사 기술에 종속적이지 않는다.

### Container
- 기능
    - 스케줄링
        - 컨테이너를 적당한 서버에 배포해주는 작업이다.
        - 여러 대의 서버 중 가장 할 일 없는 서버에 배포하거나 그냥 차례대로 배포 또는 아예 랜덤하게 배포한다.
        - 컨테이너 개수를 여러 개로 늘리면 적당히 나눠서 배포하고 서버가 죽으면 실행 중이던 컨테이너를 다른 서버에 띄워준다.
    - 클러스터링
        - 여러 개의 서버를 하나의 서버처럼 사용한다.
        - 작게는 몇 개 안되는 서버부터 많게는 수천 대의 서버를 하나의 클러스터로 사용한다.
        - 여기저기 흩어져 있는 컨테이너도 가상 네트워크를 이용하여 마치 같은 서버에 있는 것처럼 쉽게 통신한다.
    - 서비스 디스커버리
        - 서비스를 찾아주는 기능이다.
        - 클러스터 환경에서 컨테이너는 어느 서버에 생성될지 알 수 없고 다른 서버로 이동 할 수도 있다.
        - 컨테이너와 통신을 하기 위해서 어느 서버에서 실행중인지 알아야 하고 컨테이너가 생성되고 중지될 때 어딘가 IP와 Port와 같은 정보를 업데이트해줘야 한다.
        - Key-value 저장소에 정보를 저장할 수도 있고 내부 DNS 서버를 이용할 수도 있다.

### Image
- 프로세스가 실행되는 파일들의 집합인 즉, 환경이다.
- 이미지는 Only Read와 Writable로 나눠진다.
    - Only Read

        <img />
        - Base Image: 수정이 불가능하다.

        <img/>

        - git을 설치하여 새로운 기능을 추가하여 commit하면 새로운 이미지를 만들 수 있게 된다.

    - Writable
- 도커 이미지 규칙

    <img/>

### VM vx Docker
<img>
- overhead: 속도를 느리게 하는 부분인데 Docker는 격리시키기 때문에 이 부분이 없고 속도가 빠르다.

#### Jenkins
- Java로 만들어진 CICD 파이프 라인을 구성하는 툴이다.

#### Wordpress
- php로 만들어진 블로그를 하기 위한 도구이다.

#### rocket-chat
- Slack같이 무료 오픈 소스, 자체 호스팅 채팅 응용 프로그램으로 자체 채팅 서버를 호스팅할 수 있다.

#### 상태관리 도구
- 어떤 명령를 입력하였는지 문서화하여 해당 파일을 관리를 하여 그 프로그램을 돌리면 설정이 사람이 돌리는 것 처럼해서 서버를 관리하는 것이다.
- CHEF, puppet labs, ANSIBLE

### Docker Installation
- Linux Ubuntu 경우
```
curl -fsSL https://get.docker.com/ | sudo sh
sudo usermod -aG docker [ubuntu 사용자 계정 이름]
```
- 설치 확인법
    다음과 같이 입력 시 다음 창이 뜬다.
    ```
    docker version
    ```
    <img  src="./img/docker_version.png" width="300px">

### docker 명령어 설명
#### RUN 명령어
- `docker run [OPTIONS] image[:tag|@DIGEST] [COMMAND] [ARG...]`: run 컨테이너 실행
- `docker search [OPTION] [검색어]`: 검색어에 대한 도커 이미지를 검색할 수 있다.
- `docker run ubuntu:20.04`: ubuntu 20.04 컨테이너 만들기
- `docker run --rm -it ubuntu:20.04 /bin/sh`: 컨테이너에 shell 커맨드로 들어가진다. --rm 때문에 나감과 동일시 저절로 삭제되어 진다.
- `docker run --rm -p 5678:5678 hashicorp/http-echo -text="hello word"`: 컨테이너 포트를 호스트 포트로 연결해서 브라우저에 localhost:5678에 접속하면 메시지를 볼 수 있다.
- `docker run --rm -p 1234:6379 redis`: Redis 라는 메모리기반 DB를 실행한다.
    <img src="./img/docker_telnet.PNG" />
    - 성공적으로 실행하였다면 다음과 같이 보이는 것을 확인할 수 있다.
#### PS. STOP, RM, LOGS, IMAGES .. 명령
- `docker ps`: 실행 중인 컨테이너 목록을 확인하는 명령어이다.
- `docker ps -a`: 중지 된 컨테이너를 확인한다.
- `docker [OPTION] [container_id]`: 실행 중인 컨테이너를 중지하는 명령어로 하나 또는 여러개를 중지할 수 있다.
- `docker rm [OPTION] [container_id]`: 중지 된 컨테이너는 저절로 삭제가 안되기 때문에 다음과 같은 커맨드를 이요하여 종료된 컨테이너를 완전히 제거해야 한다.
- `docker logs [OPTION] [container_id]`: 컨테이너가 정상적으로 동작하는지 확인하는 방법으로 기본 옵션 -f, -tail을 사용할 수 있다.
- `docker images [OPTION] [REPOSITORY[:TAG]]`: 도커가 다운로드한 이미지 목록을 보는 명령어이다.
- `docker pull [OPTIONS] NAME[:TAG|@DIGEST]`: 이미지를 다운로드하는 명령어이다.
- `docker rmi [OPTION] [image_id]`: 이미지를 삭제하는 방법이다. 하지만 컨테이너가 실행 중인 이미지는 삭제되지 않는다.
- `docker network create [OPTION] [생성할 network이름]`: 도커 컨테이너끼리 이름으로 통신할 수 있는 가상 네트워크를 만든다.
- `docker network connect [OPTION] [network 이름] [network에 연결할 container이름]`: 기존에 생성된 컨테이너에 네트워크를 추가한다.
#### Volume 명령어
``` docker run -d -p 3306:3306
    -e MYSQL_ALLOW_EMPTY_PASSWORD=true \
    --network=app-network \
    --name mysql \
    -v [컨테이너 데이터를 옮길 로컬 디렉토리 경로]
    mysql:5.7
```
- 가상 컨테이너에 존재하는 데이터는 컨테이너가 삭제될 때 같이 제거되는데 -v 옵션을 이용하면 그 데이터를 해당 디렉토리에 저장에 컨테이너를 삭제하더라도 데이터가 남아있고 사용할 수 있다.

### Docker compose
- 직접 커맨드를 작성하는 대신 이렇게 파일을 작성해서 생성하는 것도 가능하다.
- docker-compose.yml 작성 후 `docker-compose up`을 커맨드를 치면 작성한 파일에 대한 container가 만들어진다.

### Docker Image 만들기
- commit을 만들기
```
docker run -it --name git ubuntu:latest bash 

# apt-get update
# apt-get install -y git
# git --version

docker commit git ubuntu:git # git이라는 컨테이너를 ubuntu:git이라는 이미지로 변경
```
- build로 만들기
    - 이렇기 위해서는 Dockerfile 작성하는 것이 필요하다.
    - .dockerignore: 도커 빌드 컨텍스트에서 지정된 패턴의 파일을 무시한다. 이미지 빌드 시에 사용하는 파일을 제외시키면 안된다.
```
docker build -t [이름공간]/[이미지이름]:[태그] .
```
#### Dockerfile
- `FROM <이미지> 혹은 <이미지:태그>` : 기존 이미지 위에 새로운 이미지를 중첩해서 여러 단계의 이미지 층을 쌓는 것.
- `WORKDIR <이동할 경로>`: cd처럼 컨테이너 상에서 작업 디렉토리로 전환을 위해서 사용한다.
- `RUN ["<커맨드>", "<파라미터1>", "<파라미터2>"] or RUN <전체 커맨드>`: shell에서 커맨드를 실행하는 것 처럼 이미지 빌드 과정에서 필요한 커맨드를 싱행하기 위해서 사용된다. 보통 특정 소프트 웨어 설치를 위해서 사용.
-`ENTRYPOINT ["<커맨드>", "<파라미터1>", "<파라미터2>"] or ENTRYPOINT <전체 커맨드>`: 이미지를 컨테이너로 띄울 때 항상 실행되어야 하는 커맨드를 지정할 때 사용하는 것.이 명령문을호 지정된 커맨드가 실행되고, 이 커맨드로 실행된 프로세스가 죽을 때, 컨테이너로 따라서 종료된다.
- `CMD ["<커맨드>","<파라미터1>","<파라미터2>"] or CMD ["<파라미터1>","<파라미터2>"] or CMD <전체 커맨드>`: 해당 이미지를 컨테이너로 띄울 때 디폴트로 실행할 커맨드나 ENTRYPOINT 명령문으로 지정된 커맨드에 디폴트로 넘길 파라미터를 지정할 때 사용한다.
- `EXPOSE <포트> or EXPOSE <포트>/<프로토콜>`: 네트워크 상에서 컨테이너로 들어오는 트래픽(traffic)을 리스닝(listening)하는 포트와 프로토콜를 지정하기 위해서 사용한다. 프로토콜은 TCP와 UDP 중 선택할 수 있는데 지정하지 않으면 TCP가 기본으로 사용된다.
- `ENV <키> > ENV <키>=`: 환경변수를 설정하기 위해서 사용한다. 이렇게 설정된 환경 변수는 이미지 빌드시에도 혹은 해당 컨테이너에서 돌아가는 애플리케이션도 접근가능하다.
- `ADD`: 파일 또는 디렉토리 추가. URL/ZIP 사용가능하다.
- `AGE`: 빌드타임 환경변수를 설정한다.
- `COPY`: 파일 또는 디렉토리 추가한다.
- `VOLUME`: 외부 마운트 포인터 생성한다.
- `USER`: RUN, CMD, ENTRYPOINT를 실행하는 사용이다.
- `LABEL`: key-value 데이터이다.
- `ONBUILD`; 다른 빌드의 베이스로 사용될 때 사용하는 명령어이다.
#### 실습-예시 웹 애플리케이션으로 Docker Image 만들기
- node.js 설정
```
sudo apt-get install npm
npm init
npm i fastify --save
```
- app.js 작성
- Dockerfile 작성
- .dockerignore 작성
- build 하기

```
docker build -t web .
docker run -p 3001:3000 web
```
- [localhost:3001]로 웹 사이트 켜보기
- 확인 가능

### Docker Hub
- 동작
    - Docker Hub 회원가입 [hub.docker.com]
    - 이미지 저장 및 불러오기
    ```
    docker login
    docker push [ID]/example
    docker pull [ID]/example
    ```
    
### Container Deploy
- 배포하기
```
docker run -d -p 3000:3000 [이미지]
```
    - Container 실행: 이미지 pull + Container start