# Postgresql 설치 및 변경

- https://www.postgresql.org/download/ 해당 사이트에서 환경에 맞게 선택  
![image](https://github.com/JunPyo0117/my-history/assets/80608601/774defee-fb65-473e-9f0f-3490c1bf84bb)

## yum repository 설치
- 버전, 플랫폼, 아키텍쳐 선책 후 postgresql 설치
![image](https://github.com/JunPyo0117/my-history/assets/80608601/75e2ceb4-94c7-4310-ae51-d85947034f4a)  

```linux
# Install the repository RPM:
sudo yum install -y https://download.postgresql.org/pub/repos/yum/reporpms/EL-7-x86_64/pgdg-redhat-repo-latest.noarch.rpm

# Install PostgreSQL:
sudo yum install -y postgresql11-server

# Optionally initialize the database and enable automatic start:
sudo /usr/pgsql-11/bin/postgresql-11-setup initdb
sudo systemctl enable postgresql-11
sudo systemctl start postgresql-11
```

