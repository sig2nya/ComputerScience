Index
=====
* 정의 : DB에서 검색 속도를 향상시키기 위한 자료구조이다. 특정 컬럼에 대하여 Index를 생성하면, 해당 컬럼들의 데이터를 <b>'정렬'</b>하여 별도 메모리에 저장한다.(정렬 되어있다는 것이 큰 장점)
* 사용 : Index를 생성했다면, 쿼리문에 '\[Index Column] where ~' 등의 작업을 통하여 옵티마이저를 거쳐 생성된 Index를 탈 수 있다.
* 장점
* * 결론적으로 '속도 향상'을 목적으로 한다. Select / Where 조건에서 특히나 속도 저하가 일어나는데 SQL 튜닝에 있어서 가장 먼저 대안으로 생각할 수 있는 것이 Index 생성이다.
* 단점 
* * 항상 Index 상태를 정렬 상태로 유지해야하기 때문에, Index Table과 Original Table 두 테이블을 모두 수정 작업 해주어야한다.(번거롭다)
* * 전체 데이터 중에서, 10~15% 이하의 데이터를 처리할 때에만 Index가 효율적이다. Index를 추가하려면, 전체 DB의 10% 정도의 추가 저장 공간이 필요하다.
* * Index 남발은 좋은 SQL 튜닝 방법이 아니다. 생성된 Index를 참조하는 SQL에 대해서는 성능이 좋을지 몰라도, 전체적인 DB 성능은 떨어진다.
* * Index 생성은 가장 마지막에 고려하자.
```java
CREATE INDEX [인덱스명] ON [테이블명](컬럼1, 컬럼2, 컬럼3.......)
DROP INDEX [인덱스 명]
```