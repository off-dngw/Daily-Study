#### FOREIGN KEY 
제약 조건을 설정한 필드는 외래 키 라고 부르며 한 테이블을 다른 테이블과 연결 시켜주는 역할을 합니다.
외래키가 설정된 테이블에 레코드를 입력하면 기준이 되는 테이블의 내용을 참조해서 레코드가 입력됩니다.
#### FOREIGN KEY 제약 조건은 하나의 테이블을 다른 테이블에 의존하게 만듭니다.
#### FK 제약 조건을 설정 할 때 참조되는 테이블의 필드는 반드시 UK,PK의 제약 조건이 설정 되어 있어야 합니다.

#### CREATE 문법으로 FOREIGN KEY 설정
CREATE 문법으로 테이블을 생성 할 때 해당 필드 타입 뒤에 FOREIGN KEY를 명시하면 해당 필드가 왜래키로 설정 됩니다.

#### 예시
```
CREATE TABLE 테이블이름(
    필드이름, 필드타입,
 [CONSTRAINT 제약조건이름]
 FOREIGN KEY (필드이름)
 REFERENCES 테이블이름 (필드이름)
)
```
위에 문법을 사용하게 되면 해당 필드에 FOREIGN KEY 제약 조건을 설정 합니다.
이때 참조되는 테이블의 이름은 REFERENCES 키워드 다음에 명시가 됩니다.

#### 예제
Test2 테이블의 ParentID 필드에 Test 테이블의 ID 필드를 참조하는 FOREIGN KEY의 제약 조건을 설정 하는 예제
```
CREATE TABLE Test2(
    ID INT,
    ParentID INT,
    FOREIGN KEY (ParentID)
    REFERENCES Test(ID) ON UPDATE CASCADE
);
```
#### 실행 결과

![FK1](./img/FK1.png)
위의 예제에서 Test2의 테이블의 ParentID 필드는 TEST 테이블의 ID 필드를 참조하도록 설정 하였습니다.
따라서 TEST의 테이블의 ID 필드가 변경이 되면 같은 값의 TEST2 테이블의 ParentID 필드도 같이 변경이 됩니다.


#### ALTER 문법으로 FOREIGN KEY 설정
ALTER 문법으로도 테이블의 새로운 필드를 추가하거나 수정 할 때도 FOREIGN KEY 제약 조건을 설정 할 수 있습니다.

#### 예시
```
ALTER TABLE 테이블이름
ADD [CONSTRAINT 제약조건이름]
FOREIGN KEY (필드이름)
REFERENCES 테이블이름 (필드이름)
```
#### 예제
Test 테이블의 ID 필드에서 Customer 테이블의 ID 필드를 참조하는 FOREIGN KEY 제약 조건을 설정하는 예제입니다.
```
ALTER TABLE Test
ADD CONSTRAINT CustomerID
FOREIGN KEY (ID)
REFERENCES Customer (ID);
```

#### 실행 결과

![FK2](./img/fk2.png)

#### FOREIGN KEY 제약 조건 삭제
```
ALTER TABLE 테이블이름
DROP FOREIGN KEY 제약조건이름
```

