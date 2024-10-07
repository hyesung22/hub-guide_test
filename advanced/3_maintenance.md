# Maintenance
```note
FOSSLight Hub를 운영하는 데 유용한 가이드입니다.
```
## DB 백업 및 복구하기
### 1. 백업
#### 선택1. 전체 백업    
mysqldump -u[아이디] -p[패스워드] [데이터베이스명] > [백업파일명].sql
```
$ mysqldump -ufosslight -pfosslight fosslight > fosslight_backup.sql
```

#### 선택2. FOSSLight 최신 버전으로 업데이트를 위한 DB 백업 (Data만 추출)
mysqldump -u[아이디] -p[패스워드] [데이터베이스명] --no-create-info > [백업파일명].sql
```
$ mysqldump -ufosslight -pfosslight fosslight --no-create-info > fosslight_backup.sql
```

### 2. 복구
1. 버전에 따른 Table 구조를 반영하기 위해 빈 DB를 새로 만들고 기본 값을 설정합니다. 
[Developer Documentation - 다운로드 & 설치 - 4. Database 생성 및 Data 초기 등록](https://fosslight.org/hub-guide/features/1_developer.html#다운로드--설치)

2. 백업한 파일로 복구합니다.
mysql -u[아이디] -p[패스워드] [데이터베이스명] < [백업파일명].sql
```
$ mysql -ufosslight -pfosslight fosslight < fosslight_backup.sql
```

### 추천 DBMS
- [DBeaver Community edition](https://dbeaver.io/download/) 
- [MySQL workbench Community edition](https://dev.mysql.com/downloads/workbench/)
- [HeidiSQL](https://www.heidisql.com/download.php)

## DB 버전 업그레이드하기
[MyBatis Migrations](https://mybatis.org/migrations/migrate.html)를 이용하여 DB 버전을 업그레이드하는 방법 (v1.5.0부터 migration하는 script를 제공합니다.)

1. migration/migration/environments/development.properties 파일에 DB 접속 정보를 수정합니다. 
    ```
    $ cd migration/migration
    $ cat environments/development.properties
    ## Base time zone to ensure times are consistent across machines
    time_zone=GMT+0:00

    ## The character set that scripts are encoded with
    # script_char_set=UTF-8

    ## JDBC connection properties.
    driver=org.mariadb.jdbc.Driver
    url=jdbc:mysql://localhost:3306/fosslight
    username=fosslight
    password=fosslight
    ```
   
2. fosslight/migration/mybatis-migrations-3.3.11 폴더를 MIGRATIONS_HOME로 export합니다.
    ```
    $ cd fosslight
    $ pwd
    $ /home/test/fosslight
    $ export MIGRATIONS_HOME=/home/test/fosslight/migration/mybatis-migrations-3.3.11
    $ export MIGRATIONS=$MIGRATIONS_HOME/bin
    $ export PATH=$MIGRATIONS:$PATH
    ```
   
3. migrate status를 확인 후, 적용할 migration script만 남기고, 나머지 script는 삭제합니다.
    ```
    $ cd /home/test/fosslight/migration/migration
    $ migrate status
    ------------------------------------------------------------------------
    -- MyBatis Migrations - status
    ------------------------------------------------------------------------
    ID             Applied At          Description
    ================================================================================
    20230322085317    ...pending...    create changelog
    20230322092534    ...pending...    update v1.6.0
    20230818004358    ...pending...    update v1.6.1
    20240401085317    ...pending...    update 2.0.0-beta
    20240702085317    ...pending...    update v2.0.0.pre-release
    20240724045922    ...pending...    update v2.0.0.pre-release version oss components table
    20240725150921    ...pending...    update v2.0.0
    
    ------------------------------------------------------------------------
    -- MyBatis Migrations SUCCESS
    -- Total time: 0s
    -- Finished at: Mon Oct 07 10:22:07 KST 2024
    -- Final Memory: 7M/500M
    ------------------------------------------------------------------------
      
    $ cd scripts/
    $ rm 20230322092534_update_v1.6.0.sql
    $ rm 20230818004358_update_v1.6.1.sql
    ```

4.  migrate up 명령어를 통해 업그레이드 합니다.
    ```
    $ migrate up
    ------------------------------------------------------------------------
    -- MyBatis Migrations - up
    ------------------------------------------------------------------------
    ========== Applying: 20230322085317_create_changelog.sql =======================
    -- // Create Changelog
    -- Default DDL for changelog table that will keep
    -- a record of the migrations that have been run.
    -- You can modify this to suit your database before
    
    ...
    
    ------------------------------------------------------------------------
    -- MyBatis Migrations SUCCESS
    -- Total time: 2s
    -- Finished at: Mon Oct 07 10:22:47 KST 2024
    -- Final Memory: 8M/500M
    ------------------------------------------------------------------------
    ```

5. 버전 업이 적용되었는지 확인합니다. 
    ```
    $ migrate status
    ------------------------------------------------------------------------
    -- MyBatis Migrations - status
    ------------------------------------------------------------------------
    ID             Applied At          Description
    ================================================================================
    20230322085317 2024-10-07 10:22:45 create changelog
    20240401085317 2024-10-07 10:22:45 update 2.0.0-beta
    20240702085317 2024-10-07 10:22:45 update v2.0.0.pre-release
    20240724045922 2024-10-07 10:22:45 update v2.0.0.pre-release version oss components table
    20240725150921 2024-10-07 10:22:47 update v2.0.0
    
    ------------------------------------------------------------------------
    -- MyBatis Migrations SUCCESS
    -- Total time: 0s
    -- Finished at: Mon Oct 07 10:24:19 KST 2024
    -- Final Memory: 7M/500M
    ------------------------------------------------------------------------
    ```

✏️참고. 자세한 command는 [MyBatis Migrations](https://mybatis.org/migrations/migrate.html)를 참조하세요.

## NVD Data를 2002년 Data부터 다운로드 받기
FOSSLight Hub는 일 1회 NVD(NATIONAL VULNERABILITY DATABASE) 에서 제공되는 [NVD Data Feeds](https://nvd.nist.gov/vuln/data-feeds)를 다운로드하여 Database에 저장하며 저장된 NVD Data는 [Vulnerability List](../menu/7_vulnerability.md)에서 조회할 수 있습니다.      
이 때, 2002년 Data부터 NVD Data를 다운로드 받을 경우 하기와 같이 세팅합니다.     
(최초 1회만 세팅하면 이후 Data는 누적되므로 추가적으로 세팅할 필요가 없습니다.)   
    
        
**DB에서 설정값 변경**    
```
UPDATE T2_CODE_DTL SET CD_DTL_NM = 'Y' WHERE CD_NO = '990' AND CD_DTL_NO = '100';
```
NVD Data Feed initialize flag Code의 Default 값은 "N" 으로 설정되어 있으며, 위와 같이 직접 "Y"로 변경하면 다음 NVD 스케줄 동작 시 모든 NVD Data를 Clean하고 2002년 Data 파일 부터 순차적으로 등록 처리함니다.    
해당 값은 NVD Data 초기화 수행 시 에러 여부와 상관 없이 Default 값 ("N") 으로 변경됩니다.
