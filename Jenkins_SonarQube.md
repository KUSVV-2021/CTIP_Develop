# Jenkins와 SonarQube 연동방법

> 작성자: 전도현(IMRaccoon)

_해당 글은 서버(WSL Ubuntu)에서 SonarQube를 설치하고 Jenkins와 연동하는 것을 목적으로 합니다._

## PostgreSQL 설치

1. `sudo apt-get install postgresql`를 통해 설치합니다.
2. `sudo service postgresql start`를 통해 서비스를 시작하고, `sudo -i -u postgres` 로 계정을 바꾼 뒤, `psql` 커맨스를 실행합니다.
3. 유저, Database를 생성하고, 권한을 설정합니다.
   ```
   CREATE USER sonar WITH ENCRYPTED PASSWORD 'sonar';
   CREATE DATABASE sonar OWNER sonar;
   ALTER ROLE sonar WITH createdb;
   GRANT ALL PRIVILEGES ON DATABASE sonar TO sonar;
   ```
4. `\q`로 쉘 커멘드를 종료하고, `exit`를 통해 원래 계정으로 돌아갑니다. 이 후, ` sudo service postgresql --full-restart`로 재시작합니다.

## Sonarqube 설치

1. `wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-7.9.6.zip -P /tmp` 를 실행시켜 압축파일을 다운받습니다.
2. `unzip -d ~/ /tmp/sonarqube-7.9.6.zip` 를 통해 압축을 해제해줍니다.
3. `export JAVA_HOME=$(readlink -f /usr/bin/javac | sed "s:/bin/javac::")` 명령어를 통해 Java 환경변수를 설정합니다.
4. `vim ~/sonarqube-7.9.6/conf/sonar.properties`로 편집기를 열어 아래 부분에 주석을 제거하고 입력합니다.

   ```
   # DATABASE
   # User Credential
   sonar.jdbc.username=sonar
   sonar.jdbc.password=sonar

   # PostgreSQL 9.3 or greater
   sonar.jdbc.url=jdbc:postgresql://localhost/sonar

   # WER SERVER
   sonar.web.javaAdditionalOpts=-server
   sonar.web.port=9000

   # ELASTICSEARCH
   sonar.search.javaAdditionalOpts=-Dbootstrap.system_call_filter=false
   ```
