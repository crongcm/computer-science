## Index

### Index를 쓰는 이유

- 조건을 만족하는 튜플(들)을 빠르게 조회하기 위해!

- 빠르게 정렬(order by)하거나 그룹핑(group by)하기 위해!

### 기존 테이블에 인덱스를 거는 방법

  <img width="700" alt="db 103" src="https://github.com/crongcm/computer-science/assets/113030711/557f5e63-a75f-405f-a077-7e8ea61120da">

### 테이블 생성시 인덱스를 거는 방법

- 대부분의 RDBMS에서는 primary key에는 index가 자동 생성된다

  <img width="700" alt="db 104" src="https://github.com/crongcm/computer-science/assets/113030711/700efa78-046d-4aef-9ae7-a62a7b719e9e">

### 인덱스 확인 방법

  <img width="700" alt="db 105" src="https://github.com/crongcm/computer-science/assets/113030711/cb1917bd-4aa4-431b-840b-5162d1d6075f">

### SELECT시 인덱스 검색이 이루어지는 과정

1. 조건이 1개 일때
   - Index 테이블에 Index와 포인터가 있다.
   - 검색조건의 값에 따라 Binary Search를 통해 검색된 인덱스의 포인터에 해당하는 데이터를 조회한다.

2. 조건이 2개 일때
   - a 검색시 인덱스를 통해 binary search 후 b는 full scan<br/>
   <img width="700" alt="db 106" src="https://github.com/crongcm/computer-science/assets/113030711/46e48eac-8a35-498d-90c9-4511171029c2"><br/>
   <img width="700" alt="db 107" src="https://github.com/crongcm/computer-science/assets/113030711/2e8e9ef3-e956-4d59-9253-b2b71b364a92"><br/>
   ⚠️ 인덱스 생성시 순서가 중요하다 a 먼저 검색 후 b 검색<br/>
   <img width="700" alt="db 108" src="https://github.com/crongcm/computer-science/assets/113030711/4e52cae3-ea23-4374-8946-a9487cfb45d0"><br/>
   ⚠️ b로만 검색시 a는 정렬되어 있고, b는 정렬되어 있지 않아 full scan과 다를바가 없다<br/>
   <img width="700" alt="db 109" src="https://github.com/crongcm/computer-science/assets/113030711/ebf6c2ef-bb6b-47a6-abce-751b8692d436"><br/>
   ⚠️ 위의 2쿼리의 경우에는 정상적으로 인덱스가 동작, 아래의 2쿼리는 인덱스를 타기위해 backnumber를 추가해줘야함<br/>

👍 사용되는 query에 맞춰서 적절하게 index를 걸어줘야 query가 빠르게 처리될 수 있다

  ```sql
  # optimizer가 알아서 적절하게 index를 선택해준다
  
  # 직접 index를 고르고 싶다면?
  # 권장사항 느낌 / 얘를 안쓰면 full scan으로 동작
  SELECT * FROM player USE INDEX (backnumber_id) WHERE backnumber_id = 7;
  # 거의 사용하게 유도 / 얘를 안쓰면 full scan으로 동작
  SELECT * FROM player FORCE INDEX (backnumber_id) WHERE backnumber_id = 7;
  # 인덱스 제외
  SELECT * FROM player IGNORE INDEX (backnumber_id) WHERE backnumber_id = 7;
  ```

index는 막 만들어도 괜찮을까?

- table에 write할 때마다 index도 변경 발생
- 추가적인 저장 공간 차지
- 불필요한 index를 만들지 말자

### Covering index

인덱스에 모든 조회에 대한 정보가 있어 실제 테이블에 접근하지 않고 인덱스만으로 조회가 가능하다

- 조회하는 attribute(s)를 index가 모두 cover할 때
- 조회 성능이 빠름

  <img width="700" alt="db 110" src="https://github.com/crongcm/computer-science/assets/113030711/02ba7e2e-9b10-4fa4-ab48-a9b791b02054">

### Hash index

- hash table을 사용하여 index를 구현
- 시간복잡도 O(1)의 성능
- rehashing에 대한 부담
- equality 비교만 가능, range 비교 불가능
- multicolumn index의 경우 전체 attributes에 대한 조회만 가능

### Full scan이 더 좋은 경우

- table에 데이터가 조금 있을 때 (몇 십, 몇 백건 정도?)
- 조회하려는 데이터가 테이블의 상당 부분을 차지할 때

  <img width="1056" alt="db 111" src="https://github.com/crongcm/computer-science/assets/113030711/f5659a34-0e25-4549-b95f-b9c27b83813a">

### 그 외

- order by나 group by에도 index가 사용될 수 있다
- foreign key에는 index가 자동으로 생성되지 않을 수 있다 (join 관련)
- 이미 데이터가 몇 백만 건 이상 있는 테이블에 인덱스를 생성하는 경우 시간이 몇 분 이상 소요될 수 있고 DB 성능에 안좋은 영향을 줄 수 있다
    

