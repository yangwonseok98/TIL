# SQL 1
---
# INDEX
---
### 1. Database
### 2. Relational Database
### 3. SQL
### 4. Single Table Queries
- Querying data
- Sorting data
- Filtering data
- Grouping data
---
# 1. Database
---
### 1. 데이터 베이스
- 체계적인 데이터 모음
### 2. 데이터
- 저장이나 처리에 효율적인 형태로 변환된 정보
### 3. 증가하는 데이터 사용량
> - 매일 초당 2억 개의 메일이 전송되며, 3만명이 넷플릭스를 시청
> - 배달의 민족 월 평균 주문 약 6천만 건 (2020)
> - 전 세계 모든 데이터의 약 90%는 2015년 이후 생산된 것 (IBM)
### 4. 데이터 센터의 성장
> - 카카오 - 제1데이터센터와 제2데이터센터에 1.5조 투자 (2022)
> - 네이버 - 제2데이터센터에 6500억 투자 (2020)
> - 전 세계 데이터 센터 시장 2022년부터 2026년까지 연평균 20% 이상 성장 예상
### 5. 데이터를 저장하고 잘 관리하여 활용할 수 있는 기술이 중요해짐
- 우리가 알고 있는 데이터 저장 방식은 어떤 것이 있을까?
### 6. 기존의 데이터 저장 방식
1. 파일(File) 이용
2. 스프레드 시트(Spreadsheet)이용
### 7. 파일을 이용한 데이터 관리
- 어디에서나 쉽게 사용 가능
- 데이터를 구조적으로 관리하기 어려움
### 8. 스프레드 시트를 이용한 데이터 관리
- 테이블의 열과 행을 사용해 데이터를 구조적으로 관리 가능
### 9. 스프레드 시트의 한계
1. 크기
    - 일반적으로 약 100만 행까지만 저장가능
2. 보안
    - 단순히 파일이나 링크 소유 여부에 따른 단순한 접근 권한 기능 제공
3. 정확성
    - 만약 공식적으로 "강원"의 지명이 "강언"으로 바뀌었다고 가정한다면?
    - 이 변경으로 인해 데이블의 모든 위치에서 해당 값을 업데이트 해야 함
    - 찾기 및 바꾸기 기능을 사용해 바꿀 수 있지만 만약 데이터가 여러 시트에 분산되어 있다면 변경에 누락이 생기거나 추가 문제가 발생할 수 있음
### 10. 데이터베이스 역할
- 데이터를 저장하고 조작 (CRUD)
---
# 2. Relational Database
---
### 1. 데이터베이스 역할
- 데이터를 "저장(구조적 저장)"하고 "조작(CRUD)"
### 2. 관계형 데이터베이스
- 데이터 간에 "관계"가 있는 데이터 항목들의 모음
1. 테이블, 행, 열의 정보를 구조화하는 방식
2. 서로 관련된 데이터 포인터를 저장하고 이에 대한 액세스를 제공
    ### - 관계
    - 여러 테이블 간의 (논리적) 연결
3. 이 관계로 인해 두 테이블을 사용하여 데이터를 다양한 형식으로 조회할 수 있음
    > - 특정한 날짜에 구매한 모든 고객 조회
    > - 지난 달에 배송일이 지연된 고객 조회 등
### 3. 관계형 데이터베이스 예시
1. 고객 데이터 간 비교를 위해서는 어떤 값을 활용해야 할까?
    > - 이름? 주소? 만약 동명이인이나 같은 주소지가 있다면?
    - 각 데이터에 고유한 식별 값을 부여하기 "(기본키, Primary Key)"
2. 누가 어떤 주문을 했는지 어떻게 식별할 수 있을까?
    > - 고객 이름? 마찬가지로 동명이인이 있다면?
    - 고객의 고유한 식별 값을 저장하자 "(외래 키, Foreign Key)"
### 4. 관계형 데이터베이스 관련 키워드
1. Table (aka. Relation)
    - 데이터를 기록하는 곳
2. Field (aka. Column, Attribure)
    - 각 필드에는 고유한 데이터 형식(타입)이 지정됨
3. Record (aka. Row, Tuple)
    - 각 레코드에는 구체적인 데이터 값이 저장됨
4. Database (aka. Schema)
    - 테이블의 집합
5. Primary Key (기본 키)
    - 각 레코드의 고유한 값
    - 관계형 데이터 베이스에서 "레코드의 식별자"로 활용
6. Foreign Key (외래 키)
    - 테이블 필드 중 다른 테이블의 레코드를 식별할 수 있는 키
    - 다른 테입ㄹ의 기본 키를 참조
    - 각 레코드에서 서로 다른 테이블 간의 "관계를 만드는데" 사용
---
## RDBMS
### 1. DBMS (Database Management System)
- 데이터베이스를 관리하는 소프트웨어 프로그램
> - 데이터 저장 및 관리를 용이하게 하는 시스템
> - 데이터베이스와 사용자 간의 인터페이스 역할
> - 사용자가 데이터 구성, 업데이트, 모니터링, 백업, 복구 등을 할수 있도록 도움
### 2. RDBMS (Relational Database Management System)
- 관계형 데이터베이스를 관리하는 소프트웨어 프로그램
### 3. RDBMS 서비스 종류
> 1. SQLite
> 2. MySQL
> 3. Postgre SQL
> 4. Oracle Database
...
### 4. SQLite
- 경량의 오픈 소스 데이터베이스 관리 시스템
- 컴퓨터나 모바일 기기에 내장되어 간단하고 효율적인 데이터 저장 및 관리를 제공
### 5. 데이터베이스 정리
> - Table은 데이터가 기록되는 곳
> - Table에는 행에서 고유하게 식별 가능한 "기본 키(Primary Key)"라는 속성이 있으며,
> "왜래 키(Foreign Key)"를 사용하여 각 행에서 서로 다른 테이블 간의 관계를 만들 수 있음
> - 데이터는 "기본 키(Primary Key)" 또는 "왜래 키(Foreign Key)"를 통해 "결합(Join)"될 수 있는 여러 테이블에 걸쳐 구조화 됨
---
# 3. SQL
---
## 개요
### 1. SQL (Structure Query Language)
- 데이터베이스에 정보를 저장하고 처리하기 위한 프로그래밍 언어
- 테이블의 형태로 "구조화"된 관계형 데이터베이스에게 요청을 "질의(요청)" 하는 "언어"
### 2. SQL 이란
- 관계형 데이터베이스와의 대화를 위해 사용하는 프로그래밍 언어
### 3. SQL Syntax
```sql
SELECT column_name
FROM table_name
;
```
1. SQL 키워드는 대소문자를 구분하지 않음
    - 하지만 대문자로 작성하는 것을 권장 (명시적 구분)
2. 각 SQL Statements의 끝에는 세미콜론(;)이 필요
    - 세미콜론은 각 SQL Statements을 구분하는 방법 (명령어의 마침표)
---
## SQL Statements
### 1. SQL Statements
- SQL을 구성하는 가장 기본적인 코드 블록
### 2. SQL Statements 예시
```sql
SELECT column_name
FROM table_name
;
```
- 해당 예시 코드는 SELECT Statement 라 부름
- 이 statement는 `SELECT`, `FROM`이라는 2개의 Keyword로 구성됨
### 3. 수행 목적에 따른 SQL Statements 유형
1. DDL(Data Definition Language) - 데이터 정의
    1. `CREATE`
    2. `DROP`
    3. `ALTER`
2. DML(Data Manipulation Language) - 데이터 조작 언어
    1. `INSERT`
    2. `SELECT`
    3. `UPDATE`
    4. `DELETE`
3. DCL(Data Control Language) - 데이터 제어
    1. `GRANT`
    2. `REVOKE`
    3. `COMMIT`
    4. `ROLLBACK`
### 4. SQL 학습
- 단순히 SQL 문법을 암기하고 상황에 따라 실행만 하는 것이 아닌 SQL을 통해 관계형 데이터베이스를 잘 이해하고 다루는 방법을 학습
---
# 참고
---
### 1. Query
- "데이터베이스로부터 정보를 요청" 하는 것
- 일반적으로 SQL로 작성하는 코드를 쿼리문(SQL문)이라 함
### 2. SQL 표준
> - SQL은 미국 국립 표준 협회(ANSI)와 국제 표준화 기구(ISO)애 의해 표준이 채택됨
> - 모든 RDBMS에서 SQL 표준을 지원
> - 다만 각 RDBMS마다 독자적인 기능에 따라 표준을 벗어나는 문법이 존재하니 주의
---
# 4. Single Table Queries
---
# Querying data
---
## `SELECT`
### 1. `SELECT` statement
- 테이블에서 데이터를 조회
### 2. `SELECT` syntax
```sql
SELECT select_list
FROM table_name
;
```
1. `FROM` 키워드 이후 데이터를 선택하려는 테이블의 이름을 지정
2. `SELECT` 키워드 이후 데이터를 선택하려는 필드를 하나 이상 지정
### 3. `SELECT` 활용
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
3. 태이블 employees에서 모든 필드 데이터를 조회
```sql
SELECT *
FROM employees
;
```
4. 테이블 employees에서 FirstName 필드의 모든 데이터를 조회
(단, 조회 시 FirstName이 아닌 '이름'으로 출력 될 수 있도록 변경)
```sql
SELECT FirstName AS '이름'
FROM employees
;
```
5. 테이블 tracks에서 Name, Milliseconds 필드의 모든 데이터를 조회
(단, Milliseconds 필드는 60000으로 나눠 분 단위 값으로 출력)
```sql
SELECT Name, Milliseconds / 60000 AS '재생시간(분)'
FROM tracks
;
```
### 4. `SELECT` 정리
1. `SELECT` 문을 사용하여 테이블의 데이터를 조회 및 반환
2. *(asterisk)를 사용하여 모든 필드 선택
3. 연산을 한 결과값을 출력, `AS` 를 사용하여 필드의 이름을 바꿔 출력 가능
    - `SELECT Name, Milliseconds / 60000 AS '재생시간(분)'`
---
# Querying data
---
## `ORDER BY`
### 1. `ORDER BY` statement
- 조회 결과의 레코드를 정렬
### 2. `ORDER BY` syntax
```sql
SELECT select_list
FROM table_name
ORDER BY column1 [ASC|DESC], column2 [ASC|DESC]
;
```
1. `FROM` clause 뒤에 위치
2. 하나 이상의 컬럼을 기준으로 결과를 정렬
    - 오름차순(`ASC`, 기본값)
    - 내림차순(`DESC`)
### 3. `ORDER BY` 활용
1. 테이블 employees에서 FirstName 필드의 모든 데이터를 오름차순으로 조회
```sql
SELECT FirstName
FROM employees
ORDER BY FirstName ASC
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
ORDER BY Country DESC, City ASC
;
```
4. 테이블 tracks에서 Milliseconds 필드를 기준으로 내림차순으로 정렬한 다음 Name, Milliseconds 필드의 모든 데이터를 조회
(단, Milliseconds 필드는 60000으로 나눠 분 단위 값으로 출력)
```sql
SELECT Name, Milliseconds/60000 AS '재생시간(분)'
FROM tracks
ORDER BY Milliseconds DESC
;
```
### 4. 정렬에서의 `NULL`
- `NULL`값이 존재할 경우 오른차순 정렬 시 결과에 `NULL`이 먼저 출력
### 5. `SELECT` statement 실행 순서
1. `FROM` (테이블에서)
2. `SELECT` (조회하여)
3. `ORDER BY` (정렬)
---
# Fitering data
---
### Filtering data 관련 Keywords
1. Clause
    - `DISTINCT`
    - `WHERE`
    - `LIMIT`
2. Operator
    - `BETWEEN`
    - `IN`
    - `LIKE`
    - Comparison
    - Logical
---
## `DISTINCT`
### 1. `DISTINCT` statement
- 조회 결과에서 중복된 레코드를 제거
### 2. `DISTINCT` syntax
```sql
SELECT DISTINCT select_list
FROM table_name
;
```
1. `SELECT` 키워드 바로 뒤에 작성해야 함
2. `SELECT DISTINCT` 키워드 다음에 고유한 값을 선택하려는 하나 이상의 필드를 지정
### 3. `DISTINCT` 활용
1. 테이블 customers에서 Country 필드의 모든 데이터를 오름차순 조회
```sql
SELECT Country
FROM customers
ORDER BY Country ASC
;
```
2. 테이블 customers 에서 Country 필드의 모든 데이터를 중복없이 오름차순 조회
```sql
SELECT DISTINCT Country
FROM customers
ORDER BY Country ASC
;
```
---
## `WHERE`
### 1. `WHERE` statement
- 조회 시 특정 검색 조건을 지정
### 2. `WHERE` syntax
```sql
SELECT select_list
FROM table_name
WHERE search_condition
;
```
1. `FROM` clause 뒤에 위치
2. search_condition은 비교연산자 및 논리연산자(`AND`, `OR`, `NOT` 등)를 사용하는 구문이 사용됨

### 3. `WHERE` 활용
1. 테이블 customers에서 City 필드 값이 ‘Prague’인 데이터의 LastName, FirstName, City 조회
```sql
SELECT LastName, FirstName, City
FROM customers
WHERE City = 'Prague'
;
```
2. 테이블 customers에서 City 필드 값이 ‘Prague’가 아닌 데이터의 LastName, FirstName, City 조회
```sql
SELECT LastName, FirstName, City
FROM customers
WHERE City != 'Prague'
;
```
3. 테이블 customers에서 Company 필드 값이 NULL이고 Country 필드 값이 ‘USA’인 데이터의 LastName, FirstName, Company, Country 조회
```sql
SELECT LastName, FirstName, Company, Country
FROM customers
WHERE Company IS NULL AND Country = 'USA'
;
```
4. 테이블 customers에서 Company 필드 값이 NULL이거나 Country 필드 값이 ‘USA’인 데이터의 LastName, FirstName, Company, Country 조회
```sql
SELECT LastName, FirstName, Company, Country
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
6. 테이블 tracks에서 Bytes 필드 값이 100000 이상 500000 이하인 데이터의 Name, Bytes을 Bytes를 기준으로 오름차순 조회
```sql
SELECT Name, Bytes
FROM tracks
WHERE Bytes BETWEEN 100000 AND 500000
ORDER BY Bytes ASC
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
8. 테이블 customers에서 Country 필드 값이 ‘Canada’ 또는 ‘Germany’ 또는 ‘France’가 아닌 데이터의 LastName, FirstName, Country 조회
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
## Operators
### 1. Comparison Operators(비교 연산자)
- `=`, `>=`, `<=`, `IS`, `LIKE`, `IN`, `BETWEEN ... AND ...`
### 2. Logical Operatiors(논리 연산자)
- `AND`(&&), `OR`(||), `NOT`(!)
### 3. `IN` Operator
- 값이 특정 목록 안에 있는지 확인
### 4. `LIKE` Operator
- 값이 특정 패턴에 일치하는지 확인
- (Wildcards와 함께 사용)
### 5. Wildcard Characters
1. `%` - "0개 이상의 문자열"과 일치 하는지 확인
2. `_` - "단일 문자"와 일치하는지 확인
---
## `LIMIT`
### 1. `LIMIT` clause
- 조회하는 레코드 수를 제한
### 2. `LIMIT` syntax
```sql
SELECT select_list
FROM table_name
LIMIT [offset,] row_count
;
```
1. 하나 또는 두 개의 인자를 사용 (0 또는 양의 정수)
2. `row_count`는 조회하는 최대 레코드 수를 지정
### 3. `LIMIT` & OFFSET 예시
```sql
SELECT select_list
FROM table_name
LIMIT 2, 5
;
```
- OFFSET = 2, ROW_COUNT = 5
- 0, 1 번은 제외 시키고 2번 부터 5개를 읽음
### 4. `LIMIT` 활용
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
---
# Grouping data
---
## `GROUP BY`
### 1. `GROUP BY` clause
- 레코드를 그룹화하여 요약본 생성
- ('집계 함수'와 함께 사용)
### 2. Aggregation Functions(집계함수)
- 값에 대한 계산을 수행하고 단일한 값을 반환하는 함수
- `SUM`, `AVG`, `MAX`, `MIN`, `COUNT`
### 3. `GROUP BY` syntax
```sql
SELECT c1, c2, ... , cn, aggregation_function(ci)
FROM table_name
GROUP BY c1, c2, ... , cn
;
```
1. `FROM` 및 `WHERE` 절 뒤에 배치
2. `GROUP BY` 절 뒤에 그룹화 할 필드 목록을 작성
### 4. `GROUP BY` 예시
1. Country 필드를 그룹화
```sql
SELECT Country
FROM customers
GROUP BY Country
;
```
2. `COUNT`함수가 각 그룹에 대한 집계된 값을 계산
```sql
SELECT Country, COUNT(*)
FROM customers
GROUP BY Country
;
```
### 5. `GROUP BY` 활용
1. 테이블 tracks에서 Composer 필드를 그룹화하여 각 그룹에 대한 Bytes의 평균 값을 내림차순 조회
```sql
SELECT Composer, AVG(Bytes) AS avgOfBytes
FROM tracks
GROUP BY Composer
ORDER BY avgOfBytes DESC
;
```
```sql
SELECT Composer, AVG(Bytes)
FROM tracks
GROUP BY Composer
ORDER BY AVG(Bytes) DESC
;
```
2. 테이블 tracks에서 Composer 필드를 그룹화하여 각 그룹에 대한 Milliseconds의 평균 값이 10 미만인 데이터 조회
(단, Milliseconds 필드는 60000으로 나눠 분 단위 값의 평균으로 계산)
```sql
SELECT Composer, AVG(Milliseconds/60000) AS avgOfMinute 
FROM tracks
GROUP BY Composer
HAVING avgOfMinute < 10
;
```
### 6. `SELECT` statement 실행 순서
1. 테이블에서(`FROM`)
2. 특정 조건에 맞추어(`WHERE`)
3. 그룹화 하고(`GROUP BY`)
4. 만약 그룹중에서 조건이 있다면 맞추고(`GROUP BY`)
5. 조회하여 (`SELECT`)
6. 정렬하고 (`ORDER BY`)
7. 특정 위치의 값을 가져옴 (`LIMIT`)
---
# SQL 2
---
# INDEX
---
## 1. Managing Tables
1. Create a table
2. Modifying table fields
3. Delete a table
## 2. Modifying Data
1. Insert data
2. Update data
3. Delete data
## 3. Multi table queries
1. Join
2. Joining tables
---
# 1. Managing Tables
---
### SQL Statements 유형
- DDL(Data Definition Language)
    - 데이터의 기본 구조 및 형식 변경
    1. `CREATE`
    2. `DROP`
    3. `ALTER`
---
## `CREATE TABLE`
### 1. `CREATE TABLE` statement
- 테이블 생성
### 2. `CREATE TABLE` syntax
```sql
CREATE TABLE table_name (
    column_1 data_type constraints,
    column_1 data_type constraints,
    ...,
);
```
1. 각 필드에 적용할 데이터 타입 작성
2. 테이블 및 필드에 대한 제약조건(constraints)작성
### 3. `CREATE TABLE` 활용
1. examples 테이블 생성 및 확인
```sql
CREATE TABLE examples(
    ExamID INTEGER PRIMARY KEY AUTOINCREMENT,
    LastName VARCHAR(50) NOT NULL,
    FirstName VARCHAR(50) NOT NULL
);
```
2. 테이블 스키마(구조) 확인
```sql
PRAGMA table_info('examples');
```
### 4. SQLite 데이터 타입
1. `NULL`
    - 아무런 값도 포함하지 않음을 나타냄
2. `INTEGER`
    - 정수
3. `REAL`
    - 부동 소수점
4. `TEXT`
    - 문자열
4. `BLOB`
    - 이미지, 동영상, 문서 등의 바이너리 데이터
### 5. Constraints(제약 조건)
- 테이블 필드에 적용되고 있는 규칙 또는 제한사항
- 데이터의 무결성을 유지하고 데이터베이스의 일관성을 보장
    ### 대표적인 제약 조건
    1. `PRIMARY KEY`
        - 해당 필드를 기본 키로 지정
        - "`INTEGER` 타입에만 적용"되며 `INT`, `BIGINT`등과 같은 정수 유형은 적용되지 않음
    2. `NOT NULL`
        - 해당 필드에 `NULL`값을 허용하지 않도록 지정
    3. `FOREIGN KEY`
        - 다른 테이블과의 외래 키 관계를 정의
### 6. `AUTOINCREMENT` keyword
- 자동으로 고유한 정수 값을 생성하고 할당하는 필드 속성
    ### `AUTOINCREMENT` 특징
    - 필드의 자동 증가를 나타내는 특수한 키워드
    - 주로 primary key 필드에 적용
    - `INTEGER PRIMARY KEY AUTOINCREMENT`가 작성된 필드는 항상 새로운 레코드에 대해 이전 최대 값보다 큰 값을 할당
    - 삭제된 값은 무시되며 재사용할 수 없게 됨
---
## `ALTER TABLE`
### 1. `ALTER TABLE` statement
- 테이블 및 필드 조작
### 2. `ALTER TABLE` 역할
1. `ALTER TABLE ADD COLUMN`
    - 필드 추가
2. `ALTER TABLE REMANE COLUMN`
    - 필드 이름 변경
3. `ALTER TABLE DROP COLUMN`
    - 필드 삭제
4. `ALTER TABLE RENAME TO`
    - 테이블 이름 변경
### 3. `ALTER TABLE ADD COLUMN` syntax
```sql
ALTER TABLE table_name
ADD COLUMN column_definition;
```
- `ADD COLUMN`키워드 이후 추가하고자 하는 새 필드 이름과 데이터 타입 및 제약 조건 작성
### 4. `ALTER TABLE ADD COLUMN` 활용
1. examples 테이블에 Country 필드 추가
```sql
ALTER TABLE examples 
ADD COLUMN Country VARCHAR(100) NOT NULL;
```
2. examples 테이블에 Age,Address 필드 추가
```sql
ALTER TABLE examples
ADD COLUMN Age INTEGER NOT NULL;

ALTER TABLE examples
ADD COLUMN Address VARCHAR(100) NOT NULL;
```
- SQLite는 단일 문을 사용하여 한번에 여러 필드를 추가할 수 없음
### 5. `ALTER TABLE REMANE COLUMN` syntax
```sql
ALTER TABLE table_name
RENAME COLUMN current_name TO new_name;
```
- `RENAME COLUMN` 키워드 뒤에 이름을 바꾸려는 필드의 이름을 지정하고 `TO` 키워드 뒤에 새 이름을 지정
### 6.`ALTER TABLE REMANE COLUMN` 활용
- examples 테이블 Address 필드의 이름을 PostCode로 변경
```sql
ALTER TABLE examples
RENAME COLUMN Address TO PostCode;
``` 
### 7. `ALTER TABLE DROP COLUMN` syntax
```sql
ALTER TABLE table_name
DROP COLUMN current_name
```
- `DROP COLUMN` 키워드 뒤에 삭제하려는 필드의 이름을 지정
- 삭제하는 필드가 다른 부분에서 참조되지 않고 `PRIMARY KEY`가 아니며 `UNIQUE`제약 조건이 없는 경우에만 작동
### 8.`ALTER TABLE DROP COLUMN` 활용
- examples 테이블 PostCode 필드를 삭제
```sql
ALTER TABLE examples
DROP COLUMN PostCode;
``` 
### 9. `ALTER TABLE RENAME TO` syntax
```sql
ALTER TABLE table_name
RENAME TO new_table_name
```
- `RENAME TO` 키워드 뒤에 새로운 테이블 이름 지정
### 10.`ALTER TABLE RENAME TO` 활용
- examples 테이블 이름을 new_examples로 변경
```sql
ALTER TABLE examples
RENAME TO new_examples;
```
---
## `DROP TABLE`
### 1. `DROP TABLE` statement
- 테이블 삭제
### 2. `DROP TABLE` syntax
```sql
DROP TABLE table_name;
```
- `DROP TABLE` 키워드 이후 삭제할 테이블 이름 작성
### 3. `DROP TABLE` 활용
- examples 테이블 삭제
```sql
DROP TABLE examples;
```
---
# 참고
---
### 1. 타입 선호도(Type Affinity)
- 컬럼에 데이터 타입이 명시적으로 지정되지 않았거나 지원하지 않을 때 SQLite가 자동으로 데이터 타입을 추론하는 것
### 2. 타입 선호도 목적
1. 유연한 데이터 타입 지원
    - 데이터 타입을 명시적으로 지정하지 않고도 데이터를 작성하고 조회할 수 있음
    - 컬럼에 저장되는 값의 특성을 기반으로 데이터 타입을 유추
2. 간편한 테이터 처리
    - `INTEGER` Type Affinity를 가진 열에 문자열 데이터를 저장해도 
    SQLite는 자동으로 숫자로 변환하여 처리
3. SQL 호환성
    - 다른 데이터베이스 시스템과 호환성을 유지
### 반드시 `NOT NULL` 제약을 사용해야 할까?
- "NO"
- 하지만 데이터베이스를 사용하는 프로그램에 따라 `NULL`을 저장할 필요가 없는 경우가 많으므로 대부분 `NOT NULL`을 정의
- "값이 없다." 라는 표현을 테이블에 기록하는 것은 '0'이나 '빈 문자열' 등을 사용하는 것으로 대체하는 것을 권장
---
# 2. Modifying Data
---
### SQL Statements 유형
- DML(Data Multipulation Language)
    - 데이터 조작(읽기, 추가, 수정, 삭제)
    1. `INSERT`
    2. `SELECT`
    3. `UPDATE`
    4. `DELETE`
---
## `INSERT`
### 1. `INSERT` statement
- 테이블 레코드 삽입
### 2. `INSERT` syntax
```sql
INSERT INTO table_name (c1, c2, ...)
VALUES (V1, V2, ...);
```
- `INSERT INTO` 절 다음에 테이블 이름과 괄호 안에 필드 목록 작성
- `VALUES` 키워드 다음 괄호 안에 해당 필드에 삽입할 값 목록 작성
### 3. 실습 테이블 생성
```sql
CREATE TABLE articles(
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    title VARCHAR(100) NOT NULL,
    content VARCHAR(200) NOT NULL,
    createdAt DATE NOT NULL
);
```
### 4. `INSERT` 활용
1. articles 테이블에 다음과 같은 데이터 입력
    - title = 'hello'
    - content = 'world'
    - createdAt = '2000-01-01'
```sql
INSERT INTO articles(title, content, createdAt)
VALUES ('hello', 'world', '2000-01-01');
```
2. articles 테이블에 다음과 같은 데이터 추가 입력
    - title = 'title1'
    - content = 'content1'
    - createdAt = '1990-01-01'
```sql
INSERT INTO articles(title, content, createdAt)
VALUES ('title1', 'content1', '1990-01-01');
```
3. `DATE` 함수를 사용해 articles 테이블에 다음과 같은 데이터 추가 입력
    - title = 'mytitle'
    - content = 'mycontent'
    - createdAt = 오늘
```sql
INSERT INTO articles(title, content, createdAt)
VALUES ('mytitle', 'mycontent', DATE());
```
---
## `UPDATE`
### 1. `UPDATE` statement
- 테이블 레코드 수정
### 2. `UPDATE` syntax
```sql
UPDATE table_name
SET column_name = expressions,
[WHERE condition];
```
1. `SET` 절 다음에 수정 할 필드와 새 값을 지정
2. `WHERE` 절에서 수정 할 레코드를 지정하는 조건 작성
3. `WHERE` 절을 작성하지 않으면 모든 레코드를 수정
### 3. `UPDATE` 활용
1. articles 테이블 1번 레코드의 title 필드 값을 'update Title'로 변경
```sql
UPDATE articles
SET title = 'update Title'
WHERE id = 1;
```
2. articles 테이블 2번 레코드의 title, content 필드 값을 각각 'update Title', 'update Content'로 변경
```sql
UPDATE articles
SET title = 'update Title', content = 'update Content'
WHERE id = 2;
```
---
## `DELETE`
### 1. `DELETE` statement
- 테이블 레코드 삭제
### 2. `DELETE` syntax
```sql
DELETE FROM table_name
[WHERE condition];
```
1. `DELETE FROM` 절 다음에 테이블 이름 작성
2. `WHERE` 절에서 삭제할 레코드를 지정하는 조건 작성
3. `WHERE` 절을 작성하지 않으면 모든 레코드를 삭제
### 3. `DELETE` 활용
1. articles 테이블의 1번 레코드 삭제
```sql
DELETE FROM articles
WHERE id = 1;
```
2. articles 테이블에서 작성일이 오래된 순으로 레코드 2개 삭제
```sql
DELETE FROM articles 
WHERE id IN (
    SELECT id
    FROM articles
    ORDER BY createdAt ASC
    LIMIT 2
);
```
---
# 참고
### 1. SQLite의 날짜와 시간
- SQLite에는 날짜 및/또는 시간을 저장하기 위한 별도 데이터 타입이 없음
- 대신 날짜 및 시간에 대한 함수를 사용해 표기 형식에 따라 TEXT, REAL, INTEGER 값으로 저장
---
# 3. Multi table queries
---
### 1. 관계
- "여러" 테이블 간의 (논리적) 연결
### 2. 관계의 필요성
1. 커뮤니티 게시판에 필요한 데이터 생각해보기
    - 하석주가 작성한 모든 게시글을 조회하기
    - 어떤 문제점이 있을까?
        - 동명이인이 있다면, 혹은 특정 데이터가 수정된다면
```sql
SELECT *
FROM 테이블
WHERE writer = '하석주'
;
```
2. 테이블을 나누어서 분류하자
    - 각 게시글은 누가 작성했는지 알 수 있을까?
    - 작성자들의 역할은 무엇일까?

3. articles와 users테이블에 각각 userId, roleId 외래 키 필드 작성
    - 관리자인 사람만 보고 싶다면 -> roleID가 1인 데이터 조회
    - 하석주라는 사람이 권미숙으로 개명한다면 -> users에서 한번만 변경하면 자동으로 모두 변경
### 3. `JOIN` 이 필요한 순간
- 테이블을 분리하면 데이터 관리는 용이해질 수 있으나 출력시에는 문제가 있음
- 테이블을 한 개 만을 출력할 수 밖에 없어 다른 테이블과 결합하여 출력하는 것이 필요해힘
- `JOIN`
---
## `JOIN`
### 1. `JOIN` clause
- 둘 이상의 테이블에서 데이터를 검색하는 방법
### 2. `JOIN` 종류
1. `INNER JOIN`
2. `LEFT JOIN`
### 3. 사전 준비
1. users 및 articles 테이블 생성
```sql
CREATE TABLE users(
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    name VARCHAR(50) NOT NULL
);

CREATE TABLE articles(
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    title VARCHAR(50) NOT NULL,
    content VARCHAR(100) NOT NULL,
    userID INTEGER NOT NULL,
    FOREIGN KEY (userID)
    REFERENCES users(id)
);
```
2. 각 테이블에 실습 데이터 입력
```sql
INSERT INTO users(name)
VALUES ('하석주'), ('송윤미'), ('유하선');

INSERT INTO articles(title, content, userID)
VALUES ('제목1', '내용1', 1),
('제목2', '내용2', 2),
('제목3', '내용3', 1),
('제목4', '내용4', 4),
('제목5', '내용5', 1);
```
---
## `INNER JOIN`
### 1. `INNER JOIN` clause
- 두 테이블에서 값이 일치하는 레코드에 대해서만 결과를 반환
### 2. `INNER JOIN` syntax
```sql
SELECT select_list
FROM table_a
INNER JOIN table_b
ON table_b.fk = table_a.pk
```
1. `FROM` 절 이후 메인 테이블 지정 (table_a)
2. `INNER JOIN` 절 이후 메인 테이블과 조인할 테이블을 지정(table_b) 
3. `ON` 키워드 이후 조인 조건을 작성
4. 조인 조건은 table_a과 table_b 간의 레코드를 일치시키는 규칙을 지정
### 3. `INNER JOIN` 예시
```sql
SELECT *
FROM articles
INNER JOIN users
ON users.id = articles.userID;
```
### 4. `INNER JOIN` 활용
- 1번 회원(하석주)가 작성한 모든 게시글의 제목과 작성자명을 조회
```sql
SELECT title, name
FROM articles
INNER JOIN users
ON users.id = articles.userID
WHERE name = '하석주';
```
---
## `LEFT JOIN`
### 1. `LEFT JOIN` clause
- 오른쪽 테이블의 일치하는 레코드와 함께 왼쪽 테이르의 모든 레코드를 반환
### 2. `LEFT JOIN` syntax
```sql
SELECT select_list
FROM table_a
LEFT JOIN table_b
ON table_b.fk = table_a.pk;
```
1. `FROM` 절 이후 왼쪽 테이블 지정 (table_a)
2. `LEFT JOIN` 절 이후 오른쪽 테이블 지정 (table_b)
3. `ON` 키워드 이후 조인 조건을 작성
    - 왼쪽 테이블의 각 레코드를 오른쪽 테이블의 모든 레코드와 일치시킴
### 3. `LEFT JOIN` 예시
```sql
SELECT *
FROM articles
LEFT JOIN users
ON users.id = articles.userID;
```
### 4. `LEFT JOIN` 특징
1. 왼쪽은 테이블의 모든 레코드를 표기
2. 오른쪽 테이블과 매칭되는 레코드가 없으면 `NULL`을 표시
### 5. `LEFT JOIN` 활용
- 게시글을 작성한 이력이 없는 회원 정보 조회
```sql
SELECT *
FROM users
LEFT JOIN articles
ON articles.userID = users.id
WHERE articles.userID IS NULL;
```
---