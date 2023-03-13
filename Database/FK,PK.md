### FK 와 PK
* 관계형 데이터베이스에서 FK(외래키)와 PK(기본키)는 데이터베이스 테이블의 행을 다른 테이블의 행과 연결하는 데 사용된다.


#### 기본키(PK)
* 각 행을 고유하게 식별하는 열이다.
* 하나의 테이블에서 기본키는 중복되지 않는 값을 가져야하고, NULL값을 포함 할 수 없다.
* 기본키는 테이블에서 행을 수정하거나 삭제하는 데 사용된다.

#### 외래키(FK)
* 다른 테이블의 기본키를 참호나느 열이다.
* 외래키를 사용하여 두 테이블 사이의 관계를 설정할 수 있다. EX) 주문 테이블에서 고객 테이블의 고객 아이디를 외래키로 사용할 수 있따.

### 마지막으로
* 기본키와 외래키는 데이터베이스 설계에서 중요한 개념이며, 데이터베이스 관리자는 이러한 키를 올바르게 사용하여 데이터의 무결성을 유지하는 데 중요한 역할을 한다.