# Developer Documentation
```note
FOSSLight Hub 소스를 다운로드받아 직접 컴파일하여 실행할 수 있습니다. 
```

## FOSSLight Hub 소스 다운로드
[FOSSLight Hub](https://github.com/fosslight/fosslight)에서 소스를 다운로드 받습니다.

## 설치 및 실행 방법 - 1
Docker를 이용하여 빌드 및 실행합니다.

### 개발 환경
- [Docker][docker]
- [Docker Compose][doccompose]

[docker]: https://docs.docker.com/engine/install/
[doccompose]: https://docs.docker.com/compose/install/

### 빌드 및 실행
```
docker-compose up --build
```

## 설치 및 실행 방법 - 2
### 요구사항
- JAVA 11 이상
- MariaDB 10.0 이상 또는 MySql 5.6 이상
- Memory : 8GB+

### 개발 환경
- Framework : Spring Boot 2.1.x
- Build Tool : Gradle 6.x
- Git : [https://github.com/fosslight/fosslight][src]
- IDE : [Spring Tool Suite][spring]
    - [lombok][lb] 설치 필요
- Project Character Set: UTF-8

### 다운로드 & 설치
1. JAVA를 설치합니다.: [https://openjdk.java.net][java]
2. DDL : [fosslight_create.sql][sql]
3. MariaDB 또는 Mysql 설치합니다. : [https://mariadb.org/download][maria]
4. Database 생성 및 초기 Data 등록 
```
mysql -u root -p < fosslight_create.sql
```
만약 Database가 이미 존재하거나 Database 이름을 변경하려면 상단의 create database 문과 USE 'fosslight' 문을 변경합니다.
```
mysql -u root -p <DATABASE_NAME> < fosslight_create.sql
```
접속 계정이 이미 존재하거나, 다른 계정을 사용하는 경우 CREATE USER 및 GRANT 부분을 삭제(또는 변경) 합니다.
5. 시스템에 tree package를 설치합니다. :
- Ubuntu
```
sudo apt-get install tree
```
- MacOS
```
brew install tree
```


### IDE Configuration
[Spring Tool Suite][spring]를 다운로드합니다.  

#### Project Import
※ STS (Spring Tool suite) 4.x 기준
1. lombok 설치: [https://projectlombok.org/setup/eclipse][lb]
2. File > Import > Gradle > Existing Gradle Project
3. [Git Source Directory][git_repo]를 설정하고 Import 합니다.
4. Project > Properties > Resource > Text file encoding에서 UTF-8로 설정합니다.

[spring]: https://spring.io/tools
[lb]: https://projectlombok.org/setup/eclipse
[src]: https://github.com/fosslight/fosslight
[sql]: https://github.com/fosslight/fosslight/blob/main/db/initdb.d/fosslight_create.sql
[maria]: https://mariadb.org/download/
[java]: https://openjdk.java.net
[git_repo]: https://github.com/fosslight/fosslight

### 실행
- 실행 옵션 변경    
[application.properties][props] 파일에서 실행 옵션 변경
 - server.port=8180: 웹서버 포트 (8180으로 설정한 경우 [http://localhost:8180][local])
 - spring.datasource.url=127.0.0.1:3306/fosslight: FOSSLight Hub Database가 설치되어 있는 DB 서버의 IP, Port, Database Name을 설정
 - spring.datasource.username=fosslight: Database 접속자명을 설정
 - spring.datasource.password=fosslight: Database 접속자 패스워드 설정
 - logging.path=./logs : 로그파일 출력 경로 설정 ( Default "./logs" 는 Application 실행 위치를 의미)
 - logging.file=fosslight : 로그를 출력할 로그파일명 (logback-spring.xml 파일 참고)
 - root.dir=./data: 파일 업/다운로드 최상위 경로를 의미

[props]: https://github.com/fosslight/fosslight/blob/main/src/main/resources/application.properties

#### Build & Run
하기 방법으로 빌드 및 실행할 수 있습니다.     
Official Release 버전의 build된 [war파일][war]을 다운로드 받으실 수도 있습니다.

[war]: https://github.com/fosslight/fosslight/releases

##### Gradle build & Run
- build (war 파일 생성)
```
$ ./gradlew build
```
- run
```
$ ./gradlew bootRun
```
- build & run - 방법 2 (빌드 후 어플리케이션 실행)
```
$ ./gradlew clean build && java -jar build/libs/FOSSLight-1.0.0.war
```

   -   실행 옵션
        - 웹서버 포트 변경
        ```
        --server.port=<PORT>
        ```
        - Work Directory 설정 (Default: /usr/share/fosslight)
        ```
        --root.dir=<WORK_DIRECTORY>
        ```
        - Database 접속정보 변경 (Default: 127.0.0.1:3306/fosslight)
        ```
        --spring.datasource.url=<IP>:<Port>/<Database>
        --spring.datasource.username=<USER_NAME>
        --spring.datasource.password=<PASSWORD>
        ```
        - log 파일 경로 지정
        ```
        --logging.path=<LOG_PATH>
        ```


#### IDE 에서 직접 실행
    - Boot Dashboard > local > FOSSLight 선택, 우클릭 start (Crtl + Alt + Shift + B, R)


## 동작 확인
- 웹브라우저에서 [http://localhost:8180][local]으로 접속하면 로그인 화면이 표시됩니다.
- 초기 로그인 계정은 id: admin, pswd :admin 입니다.

## 세부 설정
### 메일 서버 세팅
1. Configuration 로 이동합니다.
2. SMTP Setting 체크박스를 활성화합니다.
3. 메일 서버 정보를 입력 후 저장합니다.    
ex) docker-compose 로 메일 서비스 실행한 경우    
    ```
    Mail Server : fosslight_mail
    Email Address : no-reply@fosslight.org
    Port : 587
    Encoding : UTF-8
    Username : no-reply@fosslight.org
    Password : fosslight
    ```

4. 웹 서버를 재시작해줍니다. 
```
docker-compose restart fosslight_web
```

### NVD Data 세팅
서버 세팅 후 최초 1회 NVD Data를 2002년 Data부터 다운로드 받도록 설정합니다. : [NVD Data 다운로드](https://fosslight.org/hub-guide/advanced/3_maintenance.html#nvd-data%EB%A5%BC-2002%EB%85%84-data%EB%B6%80%ED%84%B0-%EB%8B%A4%EC%9A%B4%EB%A1%9C%EB%93%9C-%EB%B0%9B%EA%B8%B0)

[local]: http://localhost:8180

테스트테스트