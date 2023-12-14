# MySQL 시작
<br/><br/>
## 명령프롬포트(cmd)에서 MySQL 실행하기
- 버전 확인 `경로> mysql -V`
- MySQL 실행 `경로> mysql -u [계정명] -p -h [호스트주소]`
  * 입력 후 Enter &rarr; `Enter password: `에 비밀번호 입력
  * `경로>` 부분이 `mysql>`로 바뀜
- 명령어 목록 확인 `help` `\help` `\h` `?` `\?`
- MySQL 빠져나오기 `exit` 또는 `quit`
<br/>

## cmd에서 SQL
- MySQL 실행
- SQL문은 문장 끝에 반드시 ';' 필요
- 스키마 이동 `use [DB명];`
- 전체 테이블 목록 모기 `show tables;`
- DB의 Table 내용 확인 `select * form [Table명];` (*: all)
- table의 스키마 구조 확인 `desc [Table명]` &rarr; [필드명, 데이터타입, 널값유무, 키값,기본값,시퀀스값]

###### 참고) 주석
- #: GUI에서 사용하는 # 주석
- --: MySQL line 주석
- /* */: multi line 주석

## SELECT 출력문
> ```
> SELECT 컬럼리스트
> FROM 테이블리스트
> WHERE 조건문 [숫자비교, 문자비교, 대소문자 비교, NULL, 날짜]
> HAVING 'GROUP BY' 비교연산
> GROUP BY 집계 연산 [SUM, AVG, VAR, MEAN, MAX, MIN ...]
> ORDER BY 정렬
> ```
### SELECT / FROM
- 단순 출력 `select [출력내용];`
- 테이블 내용 출력 `select [컬럼리스트] from [테이블명];`
- 여러 테이블 내용 출력 `select * from [테이블리스트];` &rarr; 결과 행 수 = 테이블1 행 수X테이블2 행 수X...X테이블n 행 수
### AS 별칭
  - 단순 출력에서: `select [출력내용] as [컬럼명];`
  - 테이블 출력 시 별칭(컬럼 AS 별칭, 테이블 AS 별칭)
  - AS는 생략 가능
    - 사용: `select [컬럼1] as [별칭1], [컬럼2] as [별칭2], ... from [테이블]`
    - 생략: `select [컬럼1] [별칭1], [컬럼2] [별칭2], ... from [테이블]` &larr; 공백으로 컬럼, 별칭 구분
    - 컬럼 별칭에 공백 사용 가능, 단 '' 또는 ""로 묶어야 함
    - 테이블 별칭은 공백 및 ''(또는 "")를 사용할 수 없음
      ```
      select [테이블1별칭].[테이블1의 컬럼] [컬럼별칭1], [테이블2별칭].[테이블2의 컬럼] [컬럼별칭2]
      from [테이블1] [테이블1별칭], [테이블2][테이블2별칭]
      ```
       - 여러 테이블에서 컬럼 가져올 때, 동일한 컬럼이 존재할 경우 어느 테이블의 컬럼을 가져올 지 명시해야함.
         ```
         select [컬럼1], [별칭2].[동일컬럼], [컬럼3]
         from [테이블1] as [별칭1], [테이블2] as [별칭2]
         ```
### WHERE
```
SELECT [컬럼리스트]
FROM [테이블리스트]
WHERE [조건문];
```
- 비교 연산자: >, >=, <, <=, =, !=(<>)
- 문자열 비교 `WHERE [문자열] LIKE [비교문자, wildcard]`
 -  `%`: 모든 문자(0개의 문자도 포함)
 -  `_`: 한 개의 문자

### ORDER BY
```
SELECT [컬럼리스트]
FROM [테이블리스트]
ORDER BY [정렬할 컬럼] ASC / DESC;  # ASC는 오름차순(기본값), DESC는 내림차순
```
- 정렬할 컬럼은 컬럼명으로도, 컬럼리스트에 등장한 순서(숫자)로도 입력 가능

### GROUP BY / HAVING
```
SELECT [컬럼리스트]
FROM [테이블리스트]
GROUP BY [그룹화할 컬럼리스트]
HAVING [GROUP BY의 비교 연산];
```
- 집계함수
- 

### WITH ROLLUP

### CUBE

### window 함수
#### GROUPING()
#### ROW_NUMBER()
#### RANK() / DENSE_RANK()
#### DATE TYPE
- YEAR(): 1000 ~  9999  4자리 표시  
- MONTH() : 1 ~ 12
- DAY ()  : 1~  31
- WEEKDAY(): 0  ~  6 (월 - 일)
- DAYOFMONTH()  = DAY()  
- HOUR() / MINUTE() / SECOND() 
- DATE_ADD( INTERVAL ) , DATE_SUB() 

### Language Structure
- Literal
 - string
 - Numeric
 - Date and Time
 - 
