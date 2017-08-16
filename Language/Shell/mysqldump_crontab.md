#### mysql 백업 4가지 방법
- - -
1. Data dir 백업
	.  Data dir를 정기적으로 백업하고 문제 발생했을 때 덮어쓰면 된다.

2. mysqldump 사용
	. 백업시에 데이터베이스에 락을 걸 수 없어 변경이 발생하면 다시 백업해야함.


3. mysqlhotcopy 사용
	. mysql 백업 방법 중 속도가 빠르며 DB Dir를 다른 위치에 Copy한다.
    . InnoDB HotBackup은 지원하나, 상용.
    
4. xtraback을 사용하는 방법
	. mysql 서버는 running 상태에서 InnoDB를 핫백업[^1] 가능


[^1]: Hot Backup : DB 서버가 온라인 상태에서 DB를 백업하는 것.
Cold Backup : DB 서버를 중단시키고 백업하는 것

------------------------


[root@edgenode01 ~]# vi /u11/ews-1.0.4/maribackup/mysqldump.sh

shell script 명 : /u11/ews-1.0.4/maribackup/mysqldump.sh
```Shell 
#!/bin/sh

#백업 위치를 /u11/ews*/maria_backup 아래로 정한다.
#백업 시간을 년-월-일 형식으로 저장한다.
DATE=`date +"%Y%m%d"`

# 사용자 계정과 비밀번호
USERNAME="root"
PASSWORD="!root123$"

# 백업할 DB
# DATABASE=""

# 백업 작업
mysqldump -u$USERNAME -p$PASSWORD > /u11/ews-1.0.4/maria_bak_${DATE}.sql
```

※ USERNAME, PASSWORD, DATABASE 다음(=)은 꼭 붙여쓴다

-실행권한 부여
[root@edgenode01 ~]# chmod +x /u11/ews-1.0.4/maria_backup/mysqldump.sh
[root@edgenode01 ~]# vi /etc/crontab

- 매주 일요일 02시 30분에 자동으로 실행하게 설정
> 30 2 * * 7 /u11/ews-1.0.4/maria_backup/mysqldump.sh