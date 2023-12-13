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
- DB의 Table 내용 확인 `select * form [Table명];` (*: all)
- table의 스키마 구조 확인 `desc [Table명]` &rarr; [필드명, 데이터타입, 널값유무, 키값,기본값,시퀀스값]

## SELECT 출력문
- 단순 출력 `select [출력내용];`
- 테이블 내용 출력 `select [컬럼리스트] from [테이블명];`
- 여러 테이블 내용 출력 `select * from [테이블리스트];` &rarr; 결과 행 수 = 테이블1 행 수X테이블2 행 수X...X테이블n 행 수
 * ### 별칭 AS
 - 단순 출력에서: `select [출력내용] as [컬럼명];`
 - 테이블 출력 시 별칭(컬럼 AS 별칭, 테이블 AS 별칭)
 - AS는 생략 가능
   - 사용: `select [컬럼1] as [별칭1], [컬럼2] as [별칭2], ... from [테이블]`
   - 생략: `select [컬럼1] [별칭1], [컬럼2] [별칭2], ... from [테이블]` &larr; 공백으로 컬럼, 별칭 구분
   - 별칭에 공백 사용 가능, 단 ''으로 묶어야 함


###### 참고) 주석
- #: GUI에서 사용하는 # 주석
- --: MySQL line 주석
