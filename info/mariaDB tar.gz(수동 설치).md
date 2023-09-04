# MariaDB tar.gz(수동 설치)
## 목차
1. mariaDB 파일 다운로드
2. 유저 생성 압축파일 소유권 변경
3. 설치
4. 트러블슈팅

## 1. MariaDB 파일 다운로드
[MariaDB 다운로드 링크](https://mariadb.org/download/?t=mariadb&p=mariadb&r=11.1.2&os=windows&cpu=x86_64&pkg=msi&m=blendbyte)  
홈페이지에서 사용자가 원하는 버전의 tar.gz 파일을 다운 받고 서버에 업로드  
![image](https://github.com/JunPyo0117/my-note/assets/80608601/6948e86a-4f13-48ae-a4f3-28754b6b2e5b)  

## 2. 유저 생성 압축파일 소유권 변경
### 그룹 생성
`groupadd mysql`   

### 유저 생성
`useradd -g mysql mysql`  

## 3. 설치
### 압축 파일 소유권 변경
`chown -R mysql:mysql mariadb*.tar.gz`

### 압축 폴더를 /usr/local 아래로 이동
`mv mariadb-*-linux-systemd-x86_64.tar.gz /usr/local/ `

### 압축 해제
`tar -zxvf mariadb*-linux-systemd-x86_64.tar.gz`

### 심볼릭 링크 생성
`ln -s ./mariadb*-linux-systemd-x86_64 /usr/local/mysql`

### 환경변수 추가
`vi /etc/profile`  

```bash
export MARIADB_HOME=/usr/local/mysql 
export PATH=$PATH:$MARIADB_HOME/bin:.
```

### 저장 후 바로 적용
`source /etc/profile`

### mariaDB 설치
`cd /usr/local/mysql`
`./scripts/mysql_install_db --user=mysql`


### 상태 확인
`systemctl status mysqld`

`mysqladmin -u root password '비밀번호'`

`mysql -u root -p`
비밀번호 입력

### 원격 접근 허용
```
MariaDB [(none)]> grant all privileges on *.* to 'root'@'%' identified by 'root의 비밀번호';
MariaDB [(none)]> flush privileges;
```  

## 트러블슈팅
### libaio 오류
`yum install -y libaio`

### mysql.sock 오류 해결 
`sudo ln -s /var/lib/mysql/mysql.sock /tmp/mysql.sock`
