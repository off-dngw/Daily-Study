#### ALTER
ALTER 문법을 사용해 데이터베이스와 테이블의 내용을 수정 할 수 있습니다.


#### 데이터베이스 수정
데이터베이스의 문자 집합이나 콜레이션을 변경 할 수 있습니다.

#### 예시
1. ALTER DATABASE 데이터베이스이름 CHARACTER SET=문자집합이름
2. ALTER DATABASE 데이터베이스이름 COLLATE=콜레이션이름

#### 예제
ALTER DATABASE Exam CHARACTER SET=euckr_bin COLLATE=euckr_korean_ci;

#### 자주 사용하는 CHARACTER SET OR COLLATE
-  UTF8 : UTF-8 유니코드를 지원하는 문자(1~3바이트)
-  euckr : 한글을 지원하는 문자셋 (1~2바이트)
#### COLLATE
- utf8_bin
- utf8_general_ci (기본 설정)
- euckr_bin
- euckr_korean_ci

#### 테이블 수정
ALTER TABLE 문법은 테이블에 필드를 추가하거나 삭제 또는 변경 할 수 있습니다.

- ADD 
- DROP
- MODIFY COLUMN

#### 새로운 필드 추가
```
ALTER TABLE 테이블이름 ADD 필드이름 필드타입
```

#### 기존 필드 삭제

```
ALTER TABLE 테이블이름 DROP 필드이름
```

#### 필드 타입 변경
```
ALTER TABLE 테이블이름 MODIFY COLOMN 필드이름 필드타입
```

