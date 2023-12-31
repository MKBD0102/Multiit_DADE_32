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
- `IS (NOT) NULL`: 비어있다. (비어있지 않다.) &rarr; True/False

### ORDER BY
```
SELECT [컬럼리스트]
FROM [테이블리스트]
ORDER BY [정렬할 컬럼] ASC / DESC;  # ASC는 오름차순(기본값), DESC는 내림차순
```
- 정렬할 컬럼은 컬럼명으로도, 컬럼리스트에 등장한 순서(숫자)로도 입력 가능

### 집계함수
```
[함수명]([컬럼명])
```
- `SUM()` 합, `AVG()` 평균, `COUTN()` 계, `MAX()` 최대, `MIN()` 최소, `VAR()` 분산, `STD()` 편차

### GROUP BY / HAVING
```
SELECT [컬럼리스트]
FROM [테이블리스트]
GROUP BY [그룹화할 컬럼리스트]
HAVING [GROUP BY의 비교 연산];
```
- `GROUP BY [컬럼리스트]`:
  - 컬럼의 값 별로 묶어서 계산하겠다.
  - `ORDER BY [컬럼]`은 group by 출력 결과 기준으로 정렬
- `HAVING [비교연산]`: group by 연산으로 나누어진 데이터에 조건을 줌

### WITH ROLLUP
```
SELECT [컬럼리스트]
FROM [테이블리스트]
GROUP BY [그룹화할 컬럼리스트] WITH ROLLUP;
```
- group by와 함께 사용, group by에 명시된 컬럼 리스트 순서대로 단계적으로 소계 계산(요약 정보)

### CUBE
```
SELECT [컬럼리스트]
FROM [테이블리스트]
GROUP BY CUBE([그룹화할 컬럼리스트])
```
- 리스트에 있는 모든 컬럼에 대해 총계, 소계 출력.
- MySQL에는 없음

#### GROUPING()
```
GROUPING([컬럼])
```
- 행이 일반 그룹에 속해 있을 경우: 0
- 행이 with rollup에 속해 있을 경우: 1


### window 함수
#### ROW_NUMBER()
```
SELECT ROW_NUMBER() OVER (ORDER BY [컬럼명1] ASC/DESC, PARTITION BY [컬럼명2])
```
- [컬럼명2]의 값으로 그룹핑 분할 &rarr; [컬럼명1]의 값으로 정렬 후 각 행의 일련번호(순서) 리턴

#### RANK() / DENSE_RANK()
##### RANK()
```
SELECT RANK() OVER (ORDER BY [컬럼명1] ASC/DESC, PARTITION BY [컬럼명2])
```
- 동일한 값에 같은 순위 부여, 다음 순위는 중복 개수를 고려하여 skip
 - ex) 1, 2, 3, 3, 3, 6, 7, 8
##### DENSE_RANK()
```
SELECT DENSE_RANK() OVER (ORDER BY [컬럼명1] ASC/DESC, PARTITION BY [컬럼명2])
```
- 동일한 값에 같은 순위 부여, 중복이 있어도 순위를 건너뛰지 않음
 - ex) 1, 2, 3, 3, 3, 4, 5, 6

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
