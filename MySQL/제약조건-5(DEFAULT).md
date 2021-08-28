#### DEFAULT 
제약 조건은 필드의 기본값을 설정 할 수 있게 해줍니다.
레코드를 입력할 때 해당 필드 값을 전달 하지 않으면 자동으로 설정된 기본 값을 저장 합니다.

#### CREATE 문법으로 DEFAULT 설정
CREATE 문으로 테이블을 생성 할 때 해당 필드의 타입 뒤에 DEFAULT를 명시하면 해당 필드의 기본값을 설정 할 수 있습니다.

#### 예시
```
CREATE TABLE 테이블이름(
    필드이름, 필드타입, DEFAULT 기본값,
)
```

#### 예제
CREATE TABLE 문법을 사용하여 Test 테이블을 생성 하면서 NAME 필드의 DEFAULT 제약 조건을 이용하는 예제입니다.
```
CREATE TABLE TEST(
    ID , INT
    NAME VARCHAR(30) DEFAULT 'Annoymous'
)
```
#### 실행 결과
![DEFAULT1](./img/DEFAULT1.png)


#### ALTER 문법으로 DEFAULT 설정
테이블에 새로운 필드를 추가 할 때 DEFAULT 제약 조건을 설정 하는 문법은 다음과 같습니다.

```
ALTER TABLE
ADD 필드이름 필드타입 DEFAULT 기본값
```

#### 기존 필드에 DEFAULT 제약 조건을 설정
```
1. ALTER TABLE 테이블이름
   MODIFY COLUMN 필드이름 필드타입 DEFAULT 기본값
2. ALTER TABLE 테이블이름
   ALTER 필드이름 SET DEFAULT 기본값
```

#### 예제
ALTER TABLE 문법을 사용하여 Test 테이블의 Name 필드에서
DEFAULT 제약 조건을 이용하여 기본값을 설정하는 예제입니다.
```
ALTER TABLE Test
ALTER Name SET DEFAULT 'Annonymous'
```

#### 실행 결과

![DEFAULT2](./img/DEFAULT2.png)

#### DEFAULT 제약 조건 삭제 
```
ALTER TABLE 테이블이름
ALTER 필드이름 DROP DEFAULT;
```