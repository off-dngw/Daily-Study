#### UNIQUE 
UNIQUE 제약 조건을 설정하면 해당 필드는 서로 다른 값을 가져야 합니다. UNIQUE 조건이 설정된 필드는 중복된 값을 저장 할 수 없습니다.

#### CREATE 문법으로 UNIQUE 설정
CREATE 문에서 테이블을 생성할 때 해당 필드의 타입 뒤에 UNIQUE를 명시하면 해당 필드는 더는 중복된 값을 저장 할 수 없습니다.

#### 사용 예시

```
1. CREATE TABLE 테이블이름 (
    필드명 필드타입 UNIQUE,
)
2. CREATE TABLE 테이블이름(
    필드이름 필드타입,
    [CONSTRAINT 제약조건이름] UNIQUE(필드이름)
)

```
위에 두 문법은 모두 해당 필드에 QUNIQUE 제약 조건을 설정하는 것입니다.
2.두번째 문법을 사용하게 되면 해당 제약조건에 이름을 설정 할 수 있습니다.
#### 예제
```
CREATE TABLE Test 
(   
    ID INT UNIQUE,
    Name VARCHAR(30)
)
```
#### 실행 결과
![UNIQUE2](./img/UNIQUE1.png)
위에 예제에서는 이제 부터 Test 테이블에 새로운 레코드를 저장 할 때 ID 필드의 값이 중복 되는 값을 가지는 레코드는 저장 할 수 없습니다.

#### ALTER 문법으로 UNIQUE 설정
ALTER 문법으로 테이블에 새로운 필드를 추가하거나 수정 할 떄도 UNIQUE 제약 조건을 설정 할 수 있습니다.

#### 테이블에 새로운 필드를 추가 할 때 UNIQUE 제약 조건 설정

```
1. ALTER TABLE 테이블이름
   ADD 필드이름 필드타입 UNIQUE
2. ALTER TABLE 테이블이름
   ADD [CONSTRAINT 제약조건이름] UNIQUE(필드이름)
```

#### 기존 필드에 UNIQUE 제약 조건을 설정
```
1. ALTER TABLE 테이블이름
   MODIFY COLUMN 필드이름 필드타입 UNIQUE
2. ALTER TABLE 테이블이름
   MODIFY CLOUMN [CONSTRAINT 제약조건이름]UNIQUE(필드이름)   
```

위에 두 문법은 모두 해당 필드에 UNIQUE 제약 조건을 설정합니다.
이때 2.에 해당하는 문법을 사용하면 해당 제약 조건에 이름을 설정 할 수 있습니다.

#### 예제
```
ALTER TABLE TEST
ADD CONSTRAINT RevervedROOM UNIQUE (RoomNum);
```

#### 실행 결과
![UNIQUE2](./img/UNIQUE2.png)

#### 제약 조건에 이름을 설정 하면 아래와 같이 해당 제약 조건을 삭제 할 수도 있습니다.
```
ALTER TABLE 테이블이름
DROP INDEX 제약조건이름
```
UNIQUE 제약 조건을 설정 하면 해당 필드는 자동으로 INDEX로 만들어 집니다.