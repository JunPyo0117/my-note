[MySQL 설치 및 datadir 변경]

#해당 주소에서 버전에 맞는 레포 다운로드(링크 복사)
`https://dev.mysql.com/downloads/repo/yum/`

#mysql 레포지토리 목록을 확인
`yum repolist enabled | grep "mysql.*"`

#mysql 패키지 목록도 확인
`yum search mysql`

#MySQL 8.0 저장소 설치
`yum install [복사 링크]`

#mysql 설치
`yum install -y mysql-server`

#mysql 버전 확인
`mysqld -V`

#mysql 시작
`systemctl enable mysqld && systemctl start mysqld && systemctl status mysqld`

#비밀번호 확인
`grep 'temporary password' /var/log/mysqld.log`

`mysql -u root -p`

# root 비밀번호 변경
`ALTER USER 'root'@'localhost' IDENTIFIED BY '설정 비밀번호';`

#mysql 데이터 디렉터리 변경
`mysql -u root -p`

# 저장 경로 확인
`mysql> select @@datadir;`

# mysql 중지
`systemctl stop mysqld`


# 신규 경로의 디렉토리 생성
`mkdir /data`

#rsync 설치
`sudo yum install rsync`

# mysql 복사  
`rsync -av /var/lib/mysql /data`

# mysql 권한 부여
`chown -R mysql:mysql /data/mysql`


# mysql 설정파일 조회
`vi /etc/my.cnf`
```
-----------

#datadir=/var/lib/mysql
#socket=/var/lib/mysql/mysql.sock
datadir=/data/mysql
socket=/data/mysql/mysql.sock
```
#mysql 재시작 
`systemctl start mysql`

#정상적으로 실행이 안될경우(소켓 에러)
`ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (2)`

`ln -sf /data/mysql/mysql.sock /var/lib/mysql/mysql.sock`
