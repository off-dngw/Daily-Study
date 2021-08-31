#### CREATE 
CREATE 문법을 사용하여 데이터베이스와 테이블을 생성 할 수 있습니다.

#### 데이터베이스 생성
CREATE DATEBASE 데이터베이스이름

#### 예제
```
CREATE DATABASE Exam;
```
#### 테이블 생성
데이터베이스는 하나 이상의 테이블로 구성이 됩니다.<br/>
테이블에 데이터를 저장하여 관리를 할 수가 있으며
CREATE TABLE 문법을 사용하여 새로운 테이블을 생성해 줍니다.

#### 예시
```
CREATE TABLE 테이블이름(
필드이름 , 필드타입
필드이름1, 필드타입1
)
```
#### 예제
```
CREATE TABLE Exam(
    ID INT,
    NAME VARCHAR(255);
)
```