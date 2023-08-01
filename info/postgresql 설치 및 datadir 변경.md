# Postgresql 설치
- https://www.postgresql.org/download/ 해당 사이트에서 환경에 맞게 선택   
![image](https://github.com/JunPyo0117/my-history/assets/80608601/774defee-fb65-473e-9f0f-3490c1bf84bb)

## yum repository 설치
- 버전, 플랫폼, 아키텍쳐 선책 후 postgresql 설치  
![image](https://github.com/JunPyo0117/my-history/assets/80608601/75e2ceb4-94c7-4310-ae51-d85947034f4a)  
(예시 postgresql 11)
```linux
# Install the repository RPM:
sudo yum install -y https://download.postgresql.org/pub/repos/yum/reporpms/EL-7-x86_64/pgdg-redhat-repo-latest.noarch.rpm

# Install PostgreSQL:
sudo yum install -y postgresql11-server postgresql11-contrib

# Optionally initialize the database and enable automatic start:
sudo /usr/pgsql-11/bin/postgresql-11-setup initdb
sudo systemctl enable postgresql-11
sudo systemctl start postgresql-11
```

## 기본 Database 생성
`sudo /usr/pgsql-11/bin/postgresql-11-setup initdb`

## 서비스 싱행 및 등록
```
sudo systemctl start postgresql-11
sudo systemctl enable postgresql-11
```

# datadir 변경  
psql 접속  
`su - postgres -c 'psql'`  
접속 후 `show data_directory;`로 데이터 저장 위치 확인 
![image](https://github.com/JunPyo0117/my-history/assets/80608601/709b9ceb-0991-42ce-adff-4acc860f2063)  

Postgres service 중지(버전 확인)  
`systemctl stop postgresql-11.service`

설정파일 확인(버전 확인)  
`vi /var/lib/pgsql/11/data/postmaster.opts`  
/usr/pgsql-11/bin/postgres "-D" "/data/postgres/data"  

vi /usr/lib/systemd/system/postgresql-11.service  
Environment=PGDATA=/data/postgres/data/  

기존에 있는 data 파일 새 경로로 복사  
```
mkdir /data/postgres/
mv /var/lib/pgsql/9.3/data /data/postgres/
```
서비스 적용 및 재시작
```
systemctl daemon-reload 
systemctl start postgresql-11.service
```
접속 후 `show data_directory;`로 변경된 데이터 저장 위치 확인  
![image](https://github.com/JunPyo0117/my-history/assets/80608601/f3eb4f09-abae-4ddd-8c0c-7f50c83cfc4c)

