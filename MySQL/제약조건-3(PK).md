#### PRIMARY KEY
해당 필드는 NOT NULL과 UNIQUE 제약 조건의 특징을 모두 가집니다. 이 제약 조건이 설정된 필드는 NULL, 값을 가질 수 없으며 또한 중복된 값을 가져서도 안됩니다. 
이러한 PRIMARY KEY 제약 조건을 기본 키 라고 합니다.

UNIQUE는 한 테이블의 여러 필드에 설정할 수 있지만 PRIMARY KEY는 테이블당 오직 하나의 필드에만 설정 할 수 있습니다. 


#### CREATE 문법으로 PRIMARY KEY 설정
CREATE 문법에서 테이블을 생성할 때 다음과 같이 PRIMARY KEY 제약 조건을 설정할 수 있습니다.

CREATE 문법으로 테이블을 생성할 때 해당 필드의 타입 뒤에 PRIMARY KEY를 명시하면, 해당 필드가 기본 키로 설정됩니다.

#### 예시
```
1. CREATE TABLE 테이블이름(
    필드이름 필드타입 PRIMARY KEY
)
2. CREATE TABLE 테이블이름(
    필드이름 필드타입
    [CONSTRAINT 제약조건이름] PRIMARY KEY (필드이름)
)
```
위에 문법은 모두 해당 필드에 모두 PRIMARY KEY 제약조건을 설정합니다. 두번째 문법을 사용하게 되면 해당 제약 조건에 이름을 설정 할 수 있습니다.

#### 예제
```
CRATE TABLE Test(
    ID IN PRIMARY KEY,
    NAME VARCHAR(30),
)
```
#### 실행 결과
![PK1](./img/PK1.png)


#### ALTER 문법으로 PRIMAY KEY 설정
ALTER 문법으로 테이블에 새로운 필드를 추가하거나 수정 할 때도 PRIMARY KEY 제약 조건을 설정 할 수 있습니다.

#### 테이블에 새로운 필드를 기본키로 설정
```
1. ALTER TABLE 테이블이름
   ADD 필드이름 필드타입 PRIMARY KEY
2. ALTET TABLE 테이블이름
    ADD [CONSTRAINT 제약조건이름] PRIMARY KEY (필드이름)
```

#### 기존에 존재하는 필드를 기본키로 설정
```
1. ALTER TABLE 테이블이름
   MODIFY COLUMN 필드이름 필드타입 PRIMARY KEY
2. ALTER TABLE 테이블이름
    MODIFY COLUMN [CONSTRAINT 제약조건이름] PRIMARY KEY (필드이름)
```
### PRIMARY KEY 제약 조건을 추가할 기존 필드는 NULL 값을 갖지 않도록 먼저 선언되어 있어야 합니다. 중요!

#### 예제
```
ALTER TABLE Reservation
CONSTRAINT CustomerID ADD PRIMARY KEY (ID);
```

#### 실행 결과 
![PK2](./img/PK2.png)

#### PRIMARY KEY 제약 조건을 삭제 할 수 있습니다
```
ALTER TABLE 테이블이름
DROP PRIMARY KEY
```