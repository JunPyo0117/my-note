# postgres replication - streaming 구성
## 목차
0. 서버 정보
1. Streaming 방식
2. Primary Server 서버 설정
3. Standby Server 서버 설정
4. 결과 확인  

## 0. 서버 정보

Replication|Primary Server|Standby Server
---|---|---|
Streaming|CentOS 7.9/Postgresql 14|CentOS 7.9/Postgresql 14

## 1. Streaming 방식
- Streaming 복제는 PostgreSQL에서 가장 일반적으로 사용되는 방식
- Primary Server 서버에서 변경된 로그 데이터를 Standby Server 서버로 스트리밍
- PostgreSQL은 데이터 변경 사항을 WAL 파일에 로그로 기록합니다. 이 로그 파일은 변경 사항이 발생할 때마다 생성되며 변경 사항을 안전하게 저장
- Standby 서버는 변경 로그를 실시간으로 적용하여 마스터 서버와 동일한 데이터베이스를 유지


## 2. Primary 서버 설정
postgres 동작 확인 `ps -ef | grep postgres`  
![image](https://github.com/JunPyo0117/my-note/assets/80608601/51628477-a788-4d56-89ac-31b105939b77)  

`su - postgre -c 'psql'` postgresql에 접속 후 Replication을 위한 User 생성  
`CREATE USER {USER NAME} REPLICATION;`  
![image](https://github.com/JunPyo0117/my-note/assets/80608601/49b3bd7d-a872-46df-a67d-db86b5ece825)


Standby DB에서 Primary DB로 접속하기 위해 `vi /var/lib/pgsql/14/data/postgresql.conf` 파일에서  
listen_address = 'localhost' -> listen_address = '*' 수정  
wal_level = replica 주석 제거  
![image](https://github.com/JunPyo0117/my-note/assets/80608601/a64fec3b-efd0-470a-a9b7-f920d1c2d914)  
![image](https://github.com/JunPyo0117/my-note/assets/80608601/c74a96d1-0ee9-4508-9331-d0b9123ecbcc)  

`vi /var/lib/pgsql/14/data/pg_hba.conf` 파일에 Standby 서버의 IP와 생성한 DB 유저를 지정(Replication User)  
![image](https://github.com/JunPyo0117/my-note/assets/80608601/f4b42e6e-012d-4966-b70f-ae0bfafab647)  

`systemctl restart postgresql-14` 설정 파일 변경으로 Postgresql 서비스 재시작  

## 3. Standby 서버 설정



## 4. 결과 확인
