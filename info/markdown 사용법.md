# MarkDown 사용법
## 개요
1. 장점
2. 단점
3. 사용법
   1. 제목(Header)
   2. 수평선(Horizontal Rules)
   3. 줄바꿈(Line Breaks)
   4. 강조(Emphasis)
   5. 인용(Blockquotes)
   6. 목록(List)
   7. 특수문자 표현(Backslash Escapes)
   8. 이미지(img)
   9. 링크(Links)
   10. 코드 블록(Code Block)
   11. 표(Table)
4. GitHub 블로그 포스팅

## 1.장점
- 문법이 쉽고 간결
- 관리 용이성
- 별도의 도구 없이 작성 가능
- 다양한 형태로 변환 가능
- 텍스트(Text)로 저장되기 떄문에 용량이 적어 보관 용이  

## 2. 단점
- 표준이 없음
- 모든 HTML 마크업을 대신하지 못하는 한계

## 3. 사용법
### 3-1 제목(Header)
- \#뒤에 띄어쓰기 넣기
- \<h1>~\<h6> 까지 표현 가능
```
# 제목1
## 제목2
### 제목3
#### 제목4
##### 제목5
###### 제목6
```
# 제목1
## 제목2
### 제목3
#### 제목4
##### 제목5
###### 제목6

### 3-2 수평선(Horizontal Rules)
- \- 또는 " 또는 _를 3개 이상 사용
```
___
***
---
```
___
***
---
### 3-3 줄바꿈(Line Breaks)
- \<br>를 활용해서 줄바꿈
- 또는 마지막 띄어쓰기 두 번
```
안녕하세요
반갑습니다.<br>

안녕하세요
반갑습니다.  
```
안녕하세요
반갑습니다.<br>
안녕하세요  
반갑습니다.  

### 3-4 강조(Emphasis)
- 기울여 쓰기: * 또는 _로 감싸기
- 두껍게 쓰기(bold): **또는 __로 감싸기
- 취소선: ~~로 감싸기
- 혼합 사용 가능
```
_기울여 쓰기_
*기울여 쓰기*
__두껍게 쓰기__
**두껍게 쓰기**
~~취소선~~
_혼합_ **사용** ~~가능~~
```  
_기울여 쓰기_   
*기울여 쓰기*   
__두껍게 쓰기__   
**두껍게 쓰기**    
~~취소선~~   
_혼합_ **사용** ~~가능~~   

### 3-5 인용(Blockquotes)
- \>으로 시작하는 텍스트
- \>는 3개까지 사용 가능
```
인용구:
> 안녕하세요
>> 반갑습니다
>>> 어서오세요
```
인용구:
> 안녕하세요
>> 반갑습니다
>>> 어서오세요

### 3-6 목록(List)
#### 순서 없는 목록
- *,+,-를 이용하여 순서 없는 목록 생성 가능
- 들여쓰기 시 모양 바뀜
```
* 안녕하세요
  * 반갑습니다
    * 어서오세요
+ 안녕하세요
  + 반갑습니다
    * 어서오세요
- 안녕하세요
- 반갑습니다
- 어서오세요
```
* 안녕하세요
  * 반갑습니다
    * 어서오세요
+ 안녕하세요
  + 반갑습니다
    * 어서오세요
- 안녕하세요
- 반갑습니다
- 어서오세요

#### 순서 있는 목록
- 숫자를 기입
- 들여쓰기시 모양 변환
```
1. LIST 1
2. LIST 2
3. LIST 3
```
1. LIST 1
2. LIST 2
3. LIST 3
- 리스트 안 리스트 사용시 들여씌기와 함께 숫자 1번 부터 나열
```
1. LIST 1
   1. LIST 1-1
2. LIST 2
3. LIST 3
   1. LIST 3-1
   2. LIST 3-2
```
1. LIST 1
   1. LIST 1-1
2. LIST 2
3. LIST 3
   1. LIST 3-1
   2. LIST 3-2

### 3-7 특수문자 표현(Backslash Escapes)
- 특수 문자 표현 시 표시할 문자 앞에 \ 입력
```
* 특수문자 표시 안됨
- 특수문자 표시 안됨

\* 특수문자 표시 됨
\- 특수문자 표시 됨
```
* 특수문자 표시 안됨  
- 특수문자 표시 안됨  

\* 특수문자 표시 됨  
\- 특수문자 표시 됨  

### 3-8 이미지(img)
- 캡쳐한 이미지 붙여넣기로 업로드 가능
```
![텍스트](이미지파일경로.jpg)
![텍스트](이미지파일URL)
```
![image](https://github.com/JunPyo0117/my-note/assets/80608601/2135387a-96ac-4724-989f-9c7f5b87b8d2)

### 3-9 링크(Links)
- 외부 링크
```
[Google](http://www.google.com "구글")

[Naver](http://www.naver.com "네이버")

[Github](http://www.github.com "깃허브")
```
[Google](http://www.google.com "구글")  
  
[Naver](http://www.naver.com "네이버")  

[Github](http://www.github.com "깃허브")  

- 링크 이름 변경
```
[검색엔진](http://www.naver.com "네이버")
```
[검색엔진](http://www.naver.com "네이버")

### 3-10 코드 블럭(Code Block)
- 간단한 코드는 텍스트 앞 뒤로 ``기호 사용
- \``` 또는 \~~~
- \``` 옆에 언어 지정 시 syntax color 적용
- 지원 언어(마크다운 에디터 적용 시)
  + Bash (bash)
  + C# (cs)
  + C++ (cpp)
  + CSS (css)
  + Diff (diff)
  + HTML, XML (html)
  + HTTP (http)
  + Ini (ini)
  + JSON (json)
  + Java (java)
  + JavaScript (javascript)
  + PHP (php)
  + Perl (perl)
  + Python (python)
  + Ruby (ruby)
  + SQL (sql)
  + Dart (dart)
```
```javascript
function myFunc(theObject) {
  theObject.make = "Toyota";
}

const mycar = {
  make: "Honda",
  model: "Accord",
  year: 1998,
};```
```

```javascript
function myFunc(theObject) {
  theObject.make = "Toyota";
}

const mycar = {
  make: "Hondaa",
  model: "Accord",
  year: 1998,
};
```

### 3-11 표(Table)
- 헤더와 셀을 구분할 때 3개 이상의 - 기호 필요
```
테이블 생성

헤더1|헤더2|헤더3|헤더4
---|---|---|---
셀1|셀2|셀3|셀4
셀5|셀6|셀7|셀8
셀9|셀10|셀11|셀12
```
테이블 생성

헤더1|헤더2|헤더3|헤더4
---|---|---|---
셀1|셀2|셀3|셀4
셀5|셀6|셀7|셀8
9|10|11|12

## 4. 깃허브 블로그 포스팅
- [Wins Cloud 기술 블로그](https://wins-cloud-msp.github.io/ "기술 블로그")
- GitHub 블로그 레포지토리 `_post` 디렉터리에 `.md` 파일 생성
- yyyy-mm-dd-제목.md 형식으로 저장
![image](https://github.com/JunPyo0117/my-note/assets/80608601/31dcba5f-9748-4029-9cef-7901833fdd7b)
![image](https://github.com/JunPyo0117/my-note/assets/80608601/2ec87edd-e557-46f8-9445-d609bce14fc4)  
- 에디터에서 최상단 아래 입력값 입력 후 아래에 MarkDown 언어로 글 작성(필수 작성)
```
---
layout: post
title: PostSQL 설치 가이드
subtitle: PostSQL 설치 가이드
categories: DBMS
tags: [DBMS, PostgreSQL]
---
```
![image](https://github.com/JunPyo0117/my-note/assets/80608601/304e0fb8-a085-4bfc-8aa3-db7e00d91206)
- 업로드 후 블로그 포스팅 확인
![image](https://github.com/JunPyo0117/my-note/assets/80608601/e4b0e29f-7400-422d-a6fc-40f78576ae45)
