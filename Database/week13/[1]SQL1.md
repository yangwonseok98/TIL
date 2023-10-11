# SQL1
## INDEX
- Database
- Relational Database
- SQL
- Single Table Queries
    - Querying data
    - Sorting data
    - Filtering data
    - Qrouping data
---
## Database
- 데이터 베이스
    - 체계적인 데이터 모음
- 데이터
    - 저장이나 처리에 효율적인 형태로 변환된 정보


- 데이터를 저장하고 잘 관리하여 활용할 수 있는 기술이 더 중요해짐
    - 증가하는 데이터 사용량
    
    - 데이터 센터의 성장

    - 우리가 알고 있는 데이터 저장 방식은 어떤 것이 있을까?

- 기존의 저장 방식
    1. 파일(File) 이용
    2. 스프레드 시트(Spreadsheet)이용

- 파일을 이용한 데이터 관리
    - 어디에서나 쉽게 사용 가능
    - 데이터를 구조적으로 관리하기 어려움

- 스프레드 시트를 이용한 데이터 관리
    - 테이블의 열과 행을 사용하여 데이터를 구조적으로 관리 가능
    
- 스프레드 시트의 한계
    - 크기
        - 일반적으로 약 100만 행까지만 저장가능
    - 보안
        - 단순히 파일이나 링크 쇼유 여부에 따른 단순한 접근 권한 기능 제공
    - 정확성
        - 변경 사항 발생 시 모든 위치에서 해당하는 값을 업데이트 해야함

- 데이터베이스 역할
    - 데이터를 저장하고 조작 (CRUD)
---
## Relational Database
- 데이터베이스 역할
    - 데이터를 저장(구조적 저장)하고 조작(CRUD)

- 관계
    - 여러 테이블 간의 (논리적) 연결

- 관계형 데이터베이스
    - 데이터 간에 관계가 있는 데이터 항목들의 모음
    - 테이블, 행, 열의 정보를 구조화하는 방식
    - 서로 관련된 데이터 포인터를 저장하고 이에 대한 엑세스를 제공
    - 이 관계로 인해 두 테이블을 사용하여 데이터를 다양한 형식으로 조회할 수 있음
        - 특정 날짜에 구매한 모든 고객 조회
        - 지난 달에 배송일이 지연된 고객 조회

- 관계형 데이터 베이스 예시
    - 다음과 같이 고객 데이터가 테이블에 저장되어 있다고 가정
    - 고객 데이터 간 비교를 위해서는 어떤 값을 활용해야 할까?
        - 이름? 주소? 만약 동명이인이나 같은 주소지가 있다면?
        - 각 데이터에 고유한 식별 값을 부여하기(기본 키, Primary Key)
    - 누가 어떤 주문을 했는지 어덯게 식별 할 수 있을까?
        - 고객 이름? 마찬가지로 동명이인이 있다면?
        - 고객의 고유한 식별 값을 저장하자 (외래 키, Foreign Key)

- 관계형 데이터 베이스 관련 키워드
    1. Table
        - 데이터를 기록하는 곳
    2. Field
        - 각 필드에는 고유한 데이터 형식(타입)이 지정됨
    3. Record
        - 각 레코드에는 구체적인 데이터 값이 저장됨
    4. Database
        - 테이블의 집합
    5. Primary Key
        - 각 레코드의 고유한 값
        - 관계형 데이터베이스에서 레코드의 식별자로 활용
    6. Foreign Key(외래 키)
        - 테이블의 필드 중 다른 테이블의 레코드를 식별할 수 있는 키
        - 다른 테이블의 기본 키를 참조
        - 각 레코드에서 서로 다른 테이블 간의 관계를 만드는 데 사용
---
## RDBMS
- DBMS(Database Management System)
    - 데이터베이스를 관리하는 소프트웨어 프로그램
- RDBMS(Relational Database Management System)
    - 데이터베이스를 관리하는 소프트웨어 프로그램
- RDMBS 서비스 종류
    - SQLite
    - MySQL
    - PostgreSQL
    - Oracle Database
- SQLite
    - 경량의 오픈 소스 데이터베이스 관리 시스템
    - 컴퓨터나 모바일 기기에 내장되어 간단하고 효율적인 데이터 저장 및 관리를 제공
---
## SQL
### 개요
- SQL(Structure Query Language)
    - 데이터베이스에 정보를 저장하고 처리하기 위한 프로그래밍 언어
- SQL 이란
    - 관계형 데이터베이스와의 대화를 위해 사용하는 프로그래밍 언어
- SQL Syntax
    - SQL 키워드는 대소문자를 구분하지 않음
        - 하지만 대문자로 작성하는 것을 권장(명시적 구분)

    - 각 SQL Statements의 끝에는 세미콜론(;)이 필요
        - 세미콜론은 각 SQL Statements을 구분하는 방법(명령어의 마침표)
---
### SQL Statements
- SQL Statements
    - SQL을 구성하는 가장 기본적인 코드 블록
- SQL Statements 예시
    - `SELECT column_name FROM table_name;`
        - 해당 예시 코드는 SELECT Statement라 부름
        - 이 Statement는 SELECT, FROM 2개의 keyword로 구성됨
- 수행 목적에 따른 SQL Statements 4가지 유형
    1. DDL - 데이터 정의
        - CREATE
        - DROP
        - ALTER
    2. DQL - 데이터 검색
        - SELECT
    3. DML - 데이터 조작
        - INSERT
        - UPDATE
        - DELETE
    4. DCL - 데이터 제어
        - COMMIT
        - ROLLBACK
        - GRANT
        - REVOKE
---
- SQL 학습
    - 단순히 SQL 문법을 암기하고 상황에 따라 실행만 하는 것이 아닌 SQL을 통해 관계형 데이터베이스를 잘 이해하고 다루는 방법을 학습
- Query
    - "데이터 베이스로부터 정보를 요청"하는 것
    - 일반적으로 SQL로 작성하는 코드를 쿼리문(SQL문)이라 함

---
## Single Table Queries
### Querying data
- `SELECT` statement
    - 테이블에서 데이터를 조회
- `SELECT` Syntax
    ```SQL
    SELECT select_list
    FROM table_name
    ;
    ```
    - SELECT 키워드 이후 데이터를 선택하려는 필드를 하나 이상 지정
    - FROM 키워드 이후 데이터를 선택하려는 테이블의 이름을 지정

- SELECT 활용
    1. 테이블 employees에서 LastName 필드의 모든 데이터를 조회
        ```sql
        SELECT LastName 
        FROM employees
        ;
        ```
    
    2. 테이블 employees에서 LastName, FirstName 필드의 모든 데이터를 조회
        ```sql
        SELECT LastName, FirstName 
        FROM employees
        ;
        ```

    3. 테이블 employees에서 모든 플드의 모든 데이터를 조회
        ```sql
        SELECT * 
        FROM employees
        ;
        ```
    
    4. 테이블 employees에서 FirstName필드의 모든 데이터를 조회(단, 조회시 FirstName이 아닌 '이름'으로 출력될 수 있도록 변경)
        ```sql
        SELECT FirstName AS '이름' 
        FROM employees
        ;
        ```

    5. 테이블 Traacks에서 Name, Miliseconds 필드의 모든 데이터 조회
    (단, Miliseconds 필드는 60000으로 나눠 분 단위 값으로 출력)
        ```sql
        SELECT Name, Milliseconds/60000 AS '재생시간(분)'
        FROM tracks
        ;
        ```
---
## Sorting data
### ORDER BY
- `ORDER BY` statement
    - 조회 결과의 레코드를 정렬
- `ORDER BY` syntax
    - `FROM` clause 뒤에 위치
    - 하나 이상의 컬럼을 기준으로 결과를 오름차순(ASC, 기본 값), 내림차순(DESC)으로 정렬
        ```sql
        SELECT select_list 
        FROM table_name 
        ORDER BY column1 [ASC|DESC], column2 [ASC|DESC],...
        ;
        ```
    
- `ORDER BY` 활용
    1. 테이블 employees에서 FirstName 필드의 모든 데이터를 오름차순으로 조회
        ```sql
        SELECT FirstName 
        FROM employees 
        ORDER BY FirstName
        ;
        ```
    2. 테이블 employees에서 FirstName 필드의 모든 데이터를 내림차순으로 조회
        ```sql
        SELECT FirstName 
        FROM employees 
        ORDER BY FirstName DESC
        ;
        ```
    3. 테이블 customers에서 Country 필드를 기준으로 내림차순으로 정렬 한 다음 City 필드 기준으로 오름차순 정렬하여 조회
        ```sql
        SELECT Country, City 
        FROM customers 
        ORDER BY Country DESC, City
        ;
        ```
    4. 테이블 tracks에서 Miliseconds 필드를 기준으로 내림차순으로 정렬한 다음 Name, Miliseconds 필드의 모든 데이터를 조회
    (단, Milisecondes 필드는 60000으로 나눠 분 단위 값으로 출력)
        ```sql
        SELECT Name, Milliseconds/60000 AS '재생시간(분)' 
        FROM tracks 
        ORDER BY Milliseconds DESC;
        ```

- 정렬에서의 `NULL`
    - `NULL` 값이 존재할 경우 오름차순 정렬 시 결과에 NULL이 먼저 출력
- SELECT statement 실행 순서
    1. 테이블에서 (FROM)
    2. 조회하여 (SELECT)
    3. 정렬 (ORDER BY)
---
## Filtering data
- Filtering data 관련 Keywords
    - Clause
        1. DISTINCT
        2. WHERE
        3. LIMIT
    - Operator
        1. BETWEEN
        2. IN
        3. LIKE
        4. Comparison
        5. Logical
---
### DISTINCT
- `DISTINCT` statement
    - 조회 결과에서 중복된 레코드를 제거
- `DISTINCT` syntax
    - `SELECT` 키워드 바로 뒤에 작성해야 함
    - `SELECT DISTINCT` 키워드 다음에 고유한 값을 선택하려는 하나 이상의 필드를 지정
    ```SQL 
    SELECT DISTINCT select_list 
    FROM table_name
    ;
    ```
- `DISTINCT` 활용
    1. 테이블 customers에서 Country 필드의 모든 데이터를 오름차순 조회
        ```sql
        SELECT Country 
        FROM customers 
        ORDER BY Country
        ;
        ```
    2. 테이블 customers에서 Country 필드의 모든 데이터를 중복 없이 오름차순 조회
        ```sql
        SELECT DISTINCT Country 
        FROM customers 
        ORDER BY Country
        ;
        ```
---
### WHERE
- `WHERE` statement
    - 조회 시 특정 검색 조건을 지정
- `WHERE` syntax
    - `FROM clause` 뒤에 위치
    - search_condition은 비교연산자 및 논리연산자(AND, OR, NOT 등)를 사용하는 구문이 사용됨
    ```sql
    SELECT select_list 
    FROM table_name 
    WHERE search_condition
    ;
    ```
- `WHERE` 활용
    1. 테이블 customers에서 City 필드 값이‘Prague’인 데이터의 LastName, FirstName, City 조회
        ```sql
        SELECT LastName, FirstName, City 
        FROM customers 
        WHERE City ='Prague'
        ;
        ```
    2. 테이블 customers에서 City 필드 값이 ‘Prague’가 아닌 데이터의 LastName, FirstName, City 조회
        ```sql
        SELECT LastName, FirstName, City 
        FROM customers 
        WHERE City !='Prague'
        ;
        ```
    3. 테이블 customers에서 Company 필드 값이 NULL이고 Country 필드 값이 ‘USA’인 데이터의 LastName, FirstName, Company, Country 조회
        ```sql
        SELECT LastName, FirstName, Company, City 
        FROM customers 
        WHERE Company IS NULL AND Country = 'USA'
        ;
        ```
    4. 테이블 customers에서 Company 필드 값이 NULL이거나 Country 필드 값이 ‘USA’인 데이터의 LastName, FirstName, Company, Country 조회
        ```sql
        SELECT LastName, FirstName, Company, City 
        FROM customers 
        WHERE Company IS NULL OR Country = 'USA'
        ;
        ```
    5. 테이블 tracks에서 Bytes 필드 값이 100000 이상 500000 이하인 데이터의 Name, Bytes 조회
        ```sql
        SELECT Name, Bytes 
        FROM tracks 
        WHERE Bytes BETWEEN 100000 AND 500000
        ;
        ```
        ```sql
        SELECT Name, Bytes 
        FROM tracks 
        WHERE Bytes >= 100000 AND Bytes <= 500000
        ;
        ```
    6. 테이블 tracks에서 Bytes 필드 값이 10000 이상 500000 이하인 데이터의 Name, Bytes을 Bytes를 기준으로 오름차순 조회
        ```sql
        SELECT Name, Bytes 
        FROM tracks 
        WHERE Bytes BETWEEN 100000 AND 500000 
        ORDER BY Bytes
        ;
        ```
    7. 테이블 customers에서 Country 필드 값이 ‘Canada’ 또는 ‘Germany’ 또는 ‘France’인 데이터의 LastName, FirstName, Country 조회
        ```sql
        SELECT LastName, FirstName, Country 
        FROM customers 
        WHERE Country IN ('Canada', 'Germany', 'France')
        ;
        ```
        ```sql
        SELECT LastName, FirstName, Country 
        FROM customers 
        WHERE Country = 'Canada' OR Country = 'Germany' OR Country = 'France'
        ;
        ```
    8. 테이블 customers에서 Country 필드 값이 ‘Canada’ 또는 ‘Germany’ 또는
    ‘France’가 아닌 데이터의 LastName, FirstName, Country 조회
        ```sql
        SELECT LastName, FirstName, Country 
        FROM customers 
        WHERE Country NOT IN ('Canada', 'Germany', 'France')
        ;
        ```
    9. 테이블 customers에서 LastName 필드 값이 son으로 끝나는 데이터의 LastName, FirstName 조회
        ```sql
        SELECT LastName, FirstName 
        FROM customers 
        WHERE LastName LIKE '%son'
        ;
        ```
    10. 테이블 customers 에서 FirstName 필드 값이 4자리면서 ‘a’로 끝나는 데이터의 LastName, FirstName 조회
        ```sql
        SELECT LastName, FirstName 
        FROM customers 
        WHERE FirstName LIKE '___a'
        ;
        ```
---
### Operators
- Comparison Operators : 비교 연산자
    - =, >=, <=, !=, IS, LIKE, IN, BETWEEN...AND
- Logical Operators : 논리 연산자
    - AND(&&), OR(||), NOT(!)
- `IN` Operator
    - 값이 특정 목록 안에 있는지 확인
- `LIKE` Operator
    - 값이 특정 패턴에 일치하는지 확인
    - (Wildcards와 함께 사용)
- `Wildcard Characters`
    - `%`
        - 0개 이상의 문자열과 일치 하는지 확인
    - `_`
        - 단일 문자와 일치하는지 확인
---
### LIMIT
- `LIMIT` clause
    - 조회하는 레코드 수를 제한
- `LIMIT` syntax
    ```sql
    SELECT select_list
    FROM table_name
    LIMIT [offset,] row_count
    ;
    ```
    - 하나 또는 두 개의 인자를 사용 (0 또는 양의 정수)
    - row_count는 조회하는 최대 레코드 수를 지정
- `LIMIT & OFFSET` 예시
    ```sql
    SELECT select_list
    FROM table_name
    LIMIT 2, 5
    ;
    ```

- `LIMIT` 활용
    1. 테이블 tracks에서 TrackId, Name, Bytes 필드 데이터를 Bytes 기준 내림차순으로 7개만 조회
        ```sql
        SELECT TrackId, Name, Bytes 
        FROM tracks 
        ORDER BY Bytes DESC 
        LIMIT 7
        ;
        ```
    2. 테이블 tracks에서 TrackId, Name, Bytes 필드 데이터를 Bytes 기준 내림차순으로 4번째부터 7번째 데이터만 조회
        ```sql
        SELECT TrackId, Name, Bytes 
        FROM tracks 
        ORDER BY Bytes DESC 
        LIMIT 3, 4
        ;
        ```
        ```sql
        SELECT TrackId, Name, Bytes 
        FROM tracks 
        ORDER BY Bytes DESC 
        LIMIT 4 OFFSET 3
        ;
        ```
---
## Grouping data
### GROUP BY
- `GROUP BY` clause
    - 레코드를 그룹화하여 요약본 생성
    - ('집계 함수' 와 함께 사용)
- Aggregation Functions [집계 함수]
    - 값에 대한 계산을 수행하고 단일한 값을 반환하는 함수
    - SUM, AVG, MAX, MIN, COUNT
- `GROUP BY` syntax
    ```sql
    SELECT c1, c2, ..., cn, aggregate_function(ci)
    FROM table_name
    GROUP BY c1, c2, ..., cn
    ;
    ```
    - `FROM` 및 `WHERE` 절 뒤에 배치
    - `GROUP BY` 절 뒤에 그룹화 할 필드 목록을 작성
- `GROUP BY` 예시
    1. Country 필드를 그룹화
        ```sql
        SELECT Country 
        FROM customers 
        GROUP BY Country
        ;
        ```
    2. COUNT 함수가 각 그룹에 대한 집계된 값을 계산
        ```sql
        SELECT Country, COUNT(*) 
        FROM customers 
        GROUP BY Country
        ;
        ```
- `GROUP BY` 활용
    1. 테이블 tracks에서 Composer 필드를 그룹화하여 각 그룹에 대한 Bytes의 평균 값을 내림차순 조회
        ```sql
        SELECT Composer, AVG(Bytes) 
        FROM tracks 
        GROUP BY Composer 
        ORDER BY AVG(Bytes) DESC
        ;
        ```
        ```sql
        SELECT Composer, AVG(Bytes) AS avgOfBytes 
        FROM tracks 
        GROUP BY Composer 
        ORDER BY avgOfBytes DESC
        ;
        ```
    2. 테이블 tracks에서 Composer 필드를 그룹화하여 각 그룹에 대한 Milliseconds의 평균 값이 10 미만인 데이터 조회 (단, Milliseconds 필드는 60000으로 나눠 분 단위 값의 평균으로 계산)
        - 에러 발생
            ```sql
            SELECT Composer, AVG(Milliseconds / 60000) AS avgOfMinute 
            FROM tracks 
            WHERE avgOfMinute < 10 
            GROUP BY Composer
            ;
            ``` 
        - `HAVING` clause
            - 집계 항목에 대한 세부 조건을 지정
            - 주로 `GROUP BY`와 함꼐 사용되며 `GROUP BY`가 없다면 `WHERE` 처럼 동작
            ```sql
            SELECT Composer, AVG(Milliseconds / 60000) AS avgOfMinute 
            FROM tracks 
            GROUP BY Composer 
            HAVING avgOfMinute < 10
            ;
            ```
- `SELECT` statement 실행 순서
    1. 테이블 에서(FROM)
    2. 특정 조건에 맞추어(WHERE)
    3. 그룹화 하고(GROUP BY)
    4. 만약 그룹 중에서 조건이 있다면 맞추고(HAVING)
    5. 조회하여(SELECT)
    6. 정렬하고(ORDER BY)
    7. 특정 위치의 값을 가져옴(LIMIT)
---
# SQL 2
## INDEX
- Managing Tables
    - create a table
    - Modifying table fields
    - Delete a table
- Modifying Data
    - Insert data
    - Update data
    - Delete data
- Multi table queries
    - Join
    - Joining tables
---
## Managing Tables
### Create a table
- `CREATE TABLE` statement
    - 테이블 생성
- `CREATE TABLE` syntax
    ```sql
    CREATE TABLE table_name(
        column_1 data_type constraints,
        column_2 data_type constraints,
        column_3 data_type constraints,
        ...
    )
    ;
    ```
    - 각 필드에 적용할 데이터 타입 작성
    - 테이블 및 필드에 대한 제약조건(constraints) 작성
- `CREATE TABLE` 활용
    1. examples 테이블 생성 및 확인
        ```sql
        CREATE TABLE examples(
            ExamId INTEGER PRIMARY KEY AUTOINCREMENT,
            LastName VARCHAR(50) NOT NULL,
            FirstName TEXT NOT NULL
        )
        ;
        ```
    2. 테이블 스키마(구조)확인
        ```sql
        PRAGMA table_info('examples');
        ```
    
    - 데이터 타입
        - `INTEGER`
        - `VARCHAR(50)`
        - `TEXT`

    - 제약 조건
        - `PRIMARY KEY`
        - `NOT NULL`

    - `AUTOINCREMENT` 키워드
        - 자동으로 증가하는 값으로 채워줌
- SQLite 데이터 타입
    1. NULL
        - 아무런 값도 포함하지 않음을 나타냄
    2. INTEGER
        - 정수
    3. REAL
        - 부동 소수점
    4. TEXT
        - 문자열
    5. BLOB
        - 이미지, 동영상, 문서 등의 바이너리 데이터
- Constraints [제약 조건]
    - 테이블의 필드에 적용되는 규칙 또는 제한 사항
    - 데이터의 무결성을 유지하고 데이터베이스의 일관성을 보장
    - 대표적인 제약 조건
        1. `PRIMARY KEY`
            - 해당 필드를 기본 키로 지정
            - `INTEGER` 타입에만 적용되며 `INT`, `BIGINT`등과 같은 정수 유형은 적용되지 않음 
        2. `NOT NULL`
            - 해당 필드에 `NULL`값을 허용하지 않도록 지정
        3. `FOREIGN KEY`
            - 다른 테이블과의 외래 키 관계를 정의
- `AUTOINCREMENT` keyword
    - 자동으로 고유한 정수 값을 생성하고 할당하는 필드 속성
    - `AUTOINCREMENT` 특징
        - 필드의 자동 증가를 나타내는 특수한 키워드
        - 주로 Primary key 필드에 적용
        - `INTEGER PRIMARY KEY AUTOINCREMENT`가 작성된 필드는 항상 새로운 레코드에 대해 이전 최대 값보다 큰 값을 할당
        - 삭제된 값은 무시되며 재사용할 수 없게 됨 
    ---
    ## Modifying table fields
    ### ALTER TABLE
    - `ALTER TABLE` statement
        - 테이블 및 필드 조작
    - `ALTER TABLE` 역할
            1. 필드 추가
                - `ALTER TABLE ADD COLUMN`
            2. 필드 이름 변경
                - `ALTER TABLE RENAME COLUMN`
            3. 필드 삭제
                - `ALTER TABLE DROP COLUMN`
            4. 테이블 이름 변경
                - `ALTER TABLE RENAME TO`
    - `ALTER TABLE ADD COLUMN` syntax
        ```sql
        ALTER TABLE table_name ADD COLUMN column_definition;
        ```
        - `ADD COLUMN` 키워드 이후 추가하고자 하는 새 필드 이름과 데이터 타입 및 제약 조건 작성
    - `ALTER TABLE ADD COLUMN` 활용
        1. examples 테이블에 다음 조건에 맞는 Country 필드 추가
            ```sql
            ALTER TABLE examples ADD COLUMN Country VARCHAR(100) NOT NULL;
            ```
        2. examples 테이블에 다음 조건에 맞는 Age, Address 필드 추가
            ```sql
            ALTER TABLE examples ADD COLUMN Age INTEGER NOT NULL;

            ALTER TABLE examples ADD COLUMN Address INTEGER NOT NULL;
            ```
            - SQLite는 단을 문을 사용하여 한 번에 여러 필드를 추가할 수 없음
            