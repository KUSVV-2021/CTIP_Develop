# CI Tool 설치 방법

> 작성자: 전도현(IMRaccoon)

_해당 글은 Local 에서 도커를 활용해 환경을 구축하는 것을 목적으로 합니다._

<br />

## Docker에 Ubuntu 설치하는 방법

1. [설치 링크](https://www.docker.com/get-started)를 통해 도커를 설치합니다.
   - 이 때, Docker Desktop 버전으로 설치합니다.
2. `docker pull ubuntu:18.04` 를 통해 도커 이미지를 받습니다.
   - 설치한 Docker Desktop으로 가면 Images 탭에 Ubuntu라는 이름을 확인할 수 있습니다.
3. `docker run -it -p 8080:8080 --name ubuntu ubuntu:18.04` 를 통해 Docker Container을 생성해줍니다.
   - ubuntu 라는 이름을 가진 Container를 설치하는 과정입니다.
   - Container 내의 8080포트와 현재 local machine의 8080포트를 연결해주는 과정입니다.
4. `docker exec -it ubuntu /bin/bash` 를 통해 해당 도커에 bash로 접속할 수 있습니다.

### Docker 삭제법

1. `docker ps -a` 를 통해 현재 설치되어 있는 Container를 모두 확인할 수 있습니다.
2. `docker stop ubuntu` 를 통해 현재 사용 중인 Container를 중지 시켜줍니다.
3. `docker rm ubuntu` 를 통해 해당 컨테이너를 삭제할 수 있습니다.
4. `docker images` 를 통해 현재 도커 내에 존재한 이미지들을 확인할 수 있습니다.
5. `docker rmi ubuntu:18.04` 를 통해 해당 이미지를 삭제할 수 있습니다.

<br />

## Java 설치

1. `apt-get install` 명령어를 통해 패키지들을 업데이트 해줍니다.
2. `apt-get install openjdk-11-jdk` 명령어를 통해 OpenJDK 11버전을 설치해줍니다.
3. 설치 완료 후, `java --version` 를 실행하였을 때 OpenJDK 11.0.10 버전이 나오면 됩니다.

<br />

## Gradle 설치

1. `apt-get install wget unzip vim` 명령어를 통해 사전 작업을 해줍니다.
2. `wget https://services.gradle.org/distributions/gradle-6.8-bin.zip -P /tmp` 를 실행시켜 Gradle 6.8 Zip 파일을 가져옵니다.
3. `unzip -d /opt/gradle /tmp/gradle-*.zip` 작업을 통해 /tmp 디렉토리에 저장되어 있던 zip파일을 /pot/gradle 폴더로 압축해제 합니다.
4. `vi /etc/profile.d/gradle.sh`를 입력한 후 다음과 같이 입력한 후 저장합니다.
   ```bash
   export GRADLE_HOME=/opt/gradle/gradle-6.8
   export PATH=${GRADLE_HOME}/bin:${PATH}
   ```
5. `source /etc/profile.d/gradle.sh` 를 실행하여 변경된 스크립트를 반영해줍니다.
6. `gradle --version` 를 실행하였을 때 Gradle 6.8 버전이 나오면 됩니다.

<br />

## Jenkins 설치방법
