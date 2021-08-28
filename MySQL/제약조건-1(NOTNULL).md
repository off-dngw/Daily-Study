#### 제약조건(constraint)
데이터의 무결성을 지키기 위해 데이터를 입력받을 때 실행되는 검사규칙을 의미합니다.
#### 제약 조건은 CREATE 문법으로 테이블을 생성할 때나 ALTER 문법으로 필드를 추가할 때도 설정 할 수도 있습니다.

MYSQL 에서 사용할 수 있는 제약조건은 5가지 입니다.

### NOT NULL
NOT NULL 제약 조건을 설정하면 해당 필드는 NULL 값을 저장할 수 없습니다. 
즉, 이 제약 조건이 설정된 필드는 무조건 데이터를 가지고 있어야 합니다
#### CREATE 문법 사용 예시
```
CREATE TABLE Test
ID INT NOT NULL,
Name VARCHAR(30)
```
#### 실행 결과
![NN1](./img/NN1.png)

위에 실행결과 에서는 이제부터 Test 테이블에 INSERT 문법으로 새로운 레코드를 추가 할 때 ID의 필드의 값으로 NULL을 사용할 수 없습니다.

#### NOT NULL 제약 조건이란 해당 필드에 NULL 값을 저장 할 수 없도록 설정하는 것으로 해당 필드를 생략하도록 하는 제약 조건은 아닙니다. INSERT 문법으로 레코드를 저장할 때 NOT NULL 제약 조건이 설정된 필드의 값을 생략 할 수 도 있습니다. 
#### INSERT 문법으로 NOT NULL 제약 조건이 걸린 필드를 생략 할 수있는 방법
```
INSERT INTO Test(Name, ReserveDate, RoomNum)
VALUES('김동우', '2016-02-16', 1108)
```
#### 실행 결과
ID|NAME|ReverveDate|RoomNum
|---|---|---|---|
0 | 김동우 | 2016-02-16 | 1108
#### 위에서 처럼 NOT NULL 제약 조건이 설정된 필드의 값이 생략된 레코드도 정상적으로 저장되는 것을 확인 할 수 있습니다.

#### ALTER 문법으로 NOT NULL 설정
ALTER 문법으로 테이블에 새로운 필드를 추가하거나 수정할 때도 NOT NULL 제약 조건을 설정 할 수 있습니다.

테이블에 새로운 필드를 추가할 때 NOT NULL 제약조건을 설정하는 문법은 다음과 같습니다.
#### 사용 예시
```
ALTER TABLE 테이블 이름
ADD 필드이름 필드타입
```

기존 필드에 NOT NULL 제약 조건을 설정하는 문법은 다음과 같습니다.

```
ALTER TABLE 테이블 이름
MODIFY COLUMN 필드이름 필드타입 NOT NULL

예를 들어 

ALTER TABLE Reservation
MODIFY COLUMN Name VARCHAR(30) NOT NULL;
```
#### 실행 결과

![NN2](./img/NN2.png)