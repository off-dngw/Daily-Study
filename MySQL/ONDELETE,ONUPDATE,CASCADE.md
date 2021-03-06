#### ON DELETE , ON UPDATE
제약 조건에 의해 참조 되는 테이블에서의 수정이나 삭제가 발생하면 참조 하고 있는 테이블의 데이터도 함께 영향을 받습니다. 
참조하고 있는 테이블의 동작은 키워드를 이용하여 FOREIGN KEY 제약 조건에서 미리 설정 할 수 있습니다.

1. ON DELETE
- 참조되는 테이블의 값이 삭제될 경우 동작은 ON DELETE 구문으로 설정 할 수 있습니다.
2. ON UPDATE
- 참조되는 테이블의 값이 변경될 경우 동작은 ON UPDATE 구문으로 설정 할 수 있습니다.

#### 위에 두 구문을 이용하여 설정 할 수 있는 동작도 있습니다.
1. CASCADE : 참조되는 테이블에서 데이터를 삭제하거나 수정하면 참조하는 테이블에서도 삭제와 수정이 같이 이루어 집니다.

2. SET NULL : 참조되는 테이블에서 데이터를 삭제하거나 수정하면 참조하는 테이블의 데이터는 NULL로 변경됩니다.

3. NO ACITION : 참조되는 테이블에서 데이터를 삭제하거나 수정해도, 참조하는 테이블의 데이터는 변경되지 않습니다.

4. SET DEFAULT : 참조되는 테이블에서 데이터를 삭제하거나 수정하면 참조하는 테이블의 데이터는 필드의 기본값으로 설정됩니다.

5. RESTRICT : 참조하는 테이블에 데이터가 남아 있으면 참조되는 테이블의 데이터를 삭제,수정 할 수 없습니다.

#### 예제
Test 테이블의 ID필드를 Test1 테이블의 ID필드를 참조하는 외래키로 설정하는데 <br>
이때 참조 되는 필드의 데이터가 수정될 때는 CASCADE 방식으로 <br>삭제될 때는 RESTRICT 방식으로 동작하는 방법입니다.

```
CREATE TABLE TEST (
    ID INT,
    ParentID INT,
    FOREIGN KEY (ParentID)
    REFERENCES Test1(ID) ON UPDATE CASCADE ON DELETE RESTRICT
)
```
위의 예제에서 Test2의 테이블의 ID 필드가 참조하고 있는 Test1 테이블의 ID 값이 수정되면<br> Test2 테이블의 ID 값도 같이 수정이 됩니다. 하지만 Test2 테이블의 레코드 중에서<br> Test1 테이블의 레코드가 ID 필드를 참조하는 레코드는 삭제 할 수 없습니다.