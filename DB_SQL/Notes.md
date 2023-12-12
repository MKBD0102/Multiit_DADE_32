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
- DB 가져오기 `use [DB명];`
- DB의 Table 내용 확인 `select * form [Table명];` (*: all)
- Table의 columns 정보 확인 `desc [Table명]`
