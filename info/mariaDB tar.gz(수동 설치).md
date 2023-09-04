# MariaDB tar.gz(수동 설치)
## 목차
1. mariaDB 파일 다운로드
2. 유저 생성 압축파일 소유권 변경
3. 설치

## 1. MariaDB 파일 다운로드
[MariaDB 다운로드 링크](https://mariadb.org/download/?t=mariadb&p=mariadb&r=11.1.2&os=windows&cpu=x86_64&pkg=msi&m=blendbyte)  
홈페이지에서 사용자가 원하는 버전의 tar.gz 파일을 다운 받고 서버에 업로드  
![image](https://github.com/JunPyo0117/my-note/assets/80608601/6948e86a-4f13-48ae-a4f3-28754b6b2e5b)  

## 2. 유저 생성 압축파일 소유권 변경
### 그룹 생성
`groupadd mysql`   

### 유저 생성
`useradd -g mysql mysql`  

