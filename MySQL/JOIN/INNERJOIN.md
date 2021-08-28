#### INNER JOIN
INNER JOIN ON 절과 함께 사용되며, ON절의 조건을 만족하는 데이터만을 가져 옵니다.

#### 문법
```
1번째 문법
첫번째테이블이름
INNER JOIN 두번째테이블이름
ON 조건
2번째 문법
첫번째테이블이름
JOIN 두번째 테이블이름
ON 조건
```
ON 절에서는 WHERE 절에서 사용할 수 있는 모든 조건을 사용할 수 있습니다.
#### 표준SQL과는 달리 MYSQL에서는 JOIN,INNER JOUIN, CROSS JOIN이 모두 같은 의미로 사용됩니다.


#### 예제
Test1 테이블의 Name 필드와 Test1 테이블의 Name 필드가 서로 일치하는 레코드만을 INNER JOIN 가져오는 예제입니다.
```
1. 
SELECT * FROM Test1
INNER JOIN Test2
ON Test1.Name = Test2.Name;

2.
SELECT * FROM Test1
JOIN Test2
ON Test1.Name = Test2.Name;
```
#### 실행 결과
![실행결과](./img/4.png)
실행 결과 처럼 JOIN의 결과는 하나의 테이블 형태로 반환합니다.

MySQL에서만 사용할 수 있는 방식이 따로 존재 합니다.
#### INNER JOIN 예제 2
```
SELECT * 
FROM Test1,Test2
WHERE Test1.Name = Tes2.Name
```
위에 경우에는 테이블의 이름이 간단하지만 길거나 

복합한 경우에는 alias를 사용하여 구문을 간략화 할 수 있습니다.

testTestTest1 , TestTestTest2 테이블 이름이 길 경우
#### 별칭(alias)를 사용하여 간략화 한 예제
```
SELECT * 
FROM TestTestTest1 AS a, TestTestTest2 AS b
WHERE a.Name = b.Name
```

#### INNER JOIN의 결과를 벤 다이어 그램으로 나타낸 것입니다.

![벤다이어그램](./img/1.jpg)