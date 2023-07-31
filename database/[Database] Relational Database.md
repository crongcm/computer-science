## Database

전자적으로(electronically) 저장되고 사용되는 관련있는(related) 데이터들의 조직화된 집합(organized collection)

- metadata
   - database를 정의하거나 기술하는 data
   - catalog라고도 부름
   - e.g) 데이터 유형, 구조, 제약 조건, 보안, 저장, 인덱스, 사용자 그룹 등등
   - metadata 또한 DBMS를 통해 저장/관리된다


## Relational Database

<img width="700" alt="db 24" src="https://github.com/crongcm/computer-science/assets/113030711/59bd1e9d-7bde-4920-88e8-0269e18ac838">

<img width="700" alt="db 25" src="https://github.com/crongcm/computer-science/assets/113030711/0be4d579-1cdd-4098-a45d-a179e4d26fdf">

### super key

relation에서 tuples를 unique하게 식별할 수 있는 attributes set<br/>
e.g. PLAYER(id, name, team_id, back_number, birth_date)의 superkey는 {id, name, team_id, back_number, birth_date}, {id, name}, {name, team_id, back_number}… etc

### candidate key

어느 한 attribute라도 제거하면 unique하게 tuples를 식별할 수 없는 super key<br/>
e.g. {id}, {team_id, back_number}

### primary key

relation에서 tuples를 unique하게 식별하기 위해 선택된 candidate key<br/>
e.g. {id} or {team_id, back_number}

### unique key

primary key가 아닌 candidate keys<br/>
e.g. PK가 id일 때, {team_id, back_number}

### foreign key

다른 relation의 PK를 참조하는 attributes set<br/>
e.g. PLAYER(id, name, team_id…)와 TEAM(id, name, manager)가 있을때 foreign key는 PLAYER의 {team_id}

### Constraint

- relational database의 relations들이 언제나 항상 지켜줘야 하는 제약 사항

domain contraints - attribute의 value는 해당 attribute의 domain에 속한 vlaue여야 한다.

<img width="700" alt="db 26" src="https://github.com/crongcm/computer-science/assets/113030711/d0b0e06c-25de-45d5-88b2-ee306c8e3b9b">

key constraints - 서로 다른 tuples는 같은 value의 key를 가질 수 없다

<img width="700" alt="db 27" src="https://github.com/crongcm/computer-science/assets/113030711/85d0ebd0-333a-4aec-bd90-8d78694fb73d">

NULL value constraint - attribute가 NOT NULL로 명시됐다면 NULL을 값으로 가질 수 없다

<img width="700" alt="db 28" src="https://github.com/crongcm/computer-science/assets/113030711/1350bd7d-0b8e-4d7b-a6d8-a1456048b449">

entity integrity constraint - primary key는 value에 NULL을 가질 수 없다.

<img width="700" alt="db 29" src="https://github.com/crongcm/computer-science/assets/113030711/cbcf3465-aefe-422f-a9f8-b26452ca46a8">

referrential integrity constraint - FK와 PK와 도메인이 같아야 하고 PK에 없는 vlaues를 FK가 값으로 가질 수 없다.

<img width="700" alt="db 30" src="https://github.com/crongcm/computer-science/assets/113030711/ef2a2bb6-6518-4943-af18-ce731b09704b">
