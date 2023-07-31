# Database

## 바른 DB schema 설계

1. 의미적으로 관련있는 속성들끼리 테이블을 구성
2. 중복 데이터를 최대한 허용하지 않도록 설계
3. join 수행 시 가짜 데이터가 생기지 않도록 설계
4. 되도록이면 null 값을 줄일 수 있는 방향으로 설계

⚠️ 성능 향상을 위해 일부러 테이블을 나누지 않는 경우도 있다.

## DB
    
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

## SQL (Structured Query Language)
    
현업에서 쓰이는 relational DBMS의 표준 언어

종합적인 database 언어 : DDL + DML + VDL

<img width="700" alt="db 31" src="https://github.com/crongcm/computer-science/assets/113030711/e1434413-7a83-4334-b9e8-cd0443a60704">

### SQL에서 relation이란?

- multiset(=bag) of tuples @ SQL
- 중복된 tuple을 허용한다

<img width="700" alt="db 32" src="https://github.com/crongcm/computer-science/assets/113030711/ec2766cc-47c4-43c7-a31f-486cdb6fb48f">

## Stored function
  - 사용자가 정의한 함수
  - DBMS에 저장되고 사용되는 함수
  - SQL의 select, insert, update, delete statement에서 사용할 수 있다.

    
1. 임직원의 ID를 열자리 정수로 랜덤하게 발급하고 싶다.
    
    ID의 맨 앞자리는 1로 고정이다.
    
    <img width="700" alt="db 33" src="https://github.com/crongcm/computer-science/assets/113030711/bd2c9a0d-be3f-4d14-a68b-57689d1e37cb">

    <img width="700" alt="db 34" src="https://github.com/crongcm/computer-science/assets/113030711/85854bd9-7232-4a84-9db6-4ff70640c359">

2. 부서의 ID를 파라미터로 받으면 해당 부서의 평균 연봉을 알려주는 함수를 작성하자
    
    <img width="700" alt="db 35" src="https://github.com/crongcm/computer-science/assets/113030711/f1225a6c-c6d2-4e8b-baa1-7b96fa46d136">

    <img width="700" alt="db 36" src="https://github.com/crongcm/computer-science/assets/113030711/9df83414-7451-4b31-be19-e9f755dd2431">

3. 졸업 요건 중 하나인 토익 800 이상을 충족했는지 알려주는 함수를 작성하자
    
   <img width="700" alt="db 37" src="https://github.com/crongcm/computer-science/assets/113030711/603b5d3f-1ee6-4d44-8a50-579ba2d7d945">
   
   <img width="700" alt="db 38" src="https://github.com/crongcm/computer-science/assets/113030711/f2564a0d-2216-43f5-89cb-c582ce7e0da1">

   - 이외에도 loop를 돌면서 반복적인 작업을 수행하거나
   - case 키워드를 사용해서 값에 따라 분기 처리 하거나
   - 에러를 핸들링하거나 에러를 일으키는 등의 다양한 동작을 정의할 수 있다
    
### stored function 삭제하기
    
  ```sql
  DROP FUNCTION stored_funtion_name;
  ```
    
### stored function 파악하기
    
  ```sql
  SHOW FUNCTION STATUS where DB = 'company' #schemas
  ```
    
  <img width="668" alt="db 39" src="https://github.com/crongcm/computer-science/assets/113030711/9cf40731-1fb2-4ff1-b573-d294b6ee2d73">

  ```sql
  SHOW CREATE FUNCTION id_generator;
  ```
    
  <img width="700" alt="db 40" src="https://github.com/crongcm/computer-science/assets/113030711/fea23567-28b0-4bbc-84e2-ce4b0b0ca4ab">

### stored function은 언제 써야할까? (쉬운코드님의 개인적인 생각, 로마에 가면 로마법을 따르라)
    
  - Three-tier carchitecture
    
  <img width="700" alt="db 41" src="https://github.com/crongcm/computer-science/assets/113030711/9934004f-29fc-4b32-87c5-10b059426276">

  - util 함수로 쓰기에는 괜찮을 것 같다
  - 비즈니스 로직을 stored function에 두는 것은 좋지 않을 것 같다
    
## Stored procedure
  - 사용자가 정의한 프로시저
  - RDBMS에 저장되고 사용되는 프로시저
  - 구체적인 하나의 태스크를 수행한다
    
1. 두 정수의 곱셈 결과를 가져오는 프로시저를 작성하자
    
   <img width="700" alt="db 42" src="https://github.com/crongcm/computer-science/assets/113030711/8a481d0a-7d59-4baa-9fde-6cfe5f2e868f">

2. 두 정수를 맞바꾸는 프로시저를 작성하자
    
   <img width="700" alt="db 43" src="https://github.com/crongcm/computer-science/assets/113030711/45f590f9-70bd-47fb-85ca-4599dad8dfb9">

   <img width="700" alt="db 44" src="https://github.com/crongcm/computer-science/assets/113030711/9f8a5003-d38c-4fa1-889a-95993de1c608">

3. 각 부서별 평균 연봉을 가져오는 프로시저를 작성하자

  <img width="700" alt="db 45" src="https://github.com/crongcm/computer-science/assets/113030711/8061aeef-75d7-4f03-9c59-65ef157f9e3e">

  <img width="700" height="400" alt="db 46" src="https://github.com/crongcm/computer-science/assets/113030711/a04f1e72-7885-4990-b825-55658d95a900">

4. 사용자가 프로필 닉네임을 바꾸면 이전 닉네임을 로그에 저장하고 새 닉네임으로 업데이트하는 프로시저를 작성하자

  <img width="700" alt="db 47" src="https://github.com/crongcm/computer-science/assets/113030711/117b6de1-a9d1-4812-afe7-4be325d659d0">

  <img width="700" alt="db 48" src="https://github.com/crongcm/computer-science/assets/113030711/1a53ff6d-879b-4a8c-8621-dd8ca722b290">
  
  <img width="700" alt="db 49" src="https://github.com/crongcm/computer-science/assets/113030711/4d9b5721-b4dc-4731-8688-26a7dd397ddf">

- 이외에도 조건문을 통해 분기처리를 하거나
- 반복문을 수행하거나
- 에러를 핸들링하거나 에러를 일으키는 등의 다양한 로직을 정의할 수 있다
    
### stored procedure vs stored function
    
  <img width="700" alt="db 50" src="https://github.com/crongcm/computer-science/assets/113030711/0f8a1baa-5db0-4fe1-9399-4d2de3609925">

### 프로시저 장점
    
   - application에 transparent하다
   - 네트워트 트래픽을 줄여서 응답 속도를 향상시킬 수 있다
   - 여러 서비스에서 재사용 가능하다
   - 민감한 정보에 대한 접근을 제한할 수 있다
    
### 프로시저 단점
    
   - stored procedure를 쓰게 되면 유지 관리 보수 비용이 커진다
   - DB 서버를 추가하는 것은 간단한 작업이 아니다(logic tier에 애플리케이션 서버 투입은 간단하다)
   - stored procedure가 언제나 transparent인건 아니다
   - 재사용 가능하다는 것이 양날의 검이 될 수도..
   - procedure로는 복잡하고 유연한 코드를 작성하기 어렵다
   - 오늘날의 프로그래밍 언어는 훨씬 다양하고 강력한 기능들을 제공한다
   - procedure는 가독성이 떨어진다
   - procedure는 디버깅이 어렵다
    
   비즈니스 로직을 소스 코드에 두고도 응답 속도를 향상 시킬 수 있다(비동기 로직 구현, 캐싱)

## Transaction
  - 단일한 논리적인 작업 단위 (a single logical unit of work)
  - 논리적인 이유로 여러 SQL문들을 단일 작업으로 묶어서 나눠질 수 없게 만든 것이 transaction이다
  - transaction의 SQL문들 중에 일부만 성공해서 DB에 반영되는 일은 일어나지 않는다
  
  ### 일반적인 transaction 사용 패턴
  
  1. transaction을 시작(begin)한다
  2. 데이터를 읽거나 쓰는 등의 SQL문들을 포함해서 로직을 수행한다
  3. 일련의 과정들이 문제없이 동작했다면 transaction을 commit한다
  
   Or 중간에 문제가 발생했다면 transaction을 rollbalk한다
  
  ### ACID
  
  - Atomicity(원자성) - ALL or NOTHING
  
    transaction은 논리적으로 쪼개질 수 없는 작업 단위이기 때문에 내부의 SQL문들이 모두 성공해야 한다
    
    중간에 SQL문이 실패하면 지금까지의 작업을 모두 취소하여 아무 일도 없었던 것처럼 rollback한다
  
  - Consistency(일관성)
  
    transaction은 DB 상태를 consistent 상태에서 또 다른 consistent 상태로 바꿔줘야 한다
    
    constraints, trigger 등을 통해 DB에 정의된 rules을 transaction이 위반했다면 rollback 해야한다
    
    transaction이 DB에 정의된 rule을 위반했는지는 DBMS가 commit 전에 확인하고 알려준다
    
    그 외에 application 관점에서 transaction이 consistent하게 동작하는지는 개발자가 챙겨야 한다
    
  - Isolation(격리성)
  
    여러 transaction들이 동시에 실행될 때도 혼자 실행되는 것처럼 동작하게 만든다
    
    DBMS는 여러 종류의 isolation level을 제공한다
    
    개발자는 isolation level 중에 어떤 level로 transaction을 동작시킬지 설정할 수 있다
    
    concurrency control의 주된 목표가 isolation이다
  
  - Durability(영존성)
  
    commit된 transation은 DB에 영구적으로 저장한다
    
    즉, DB system에 문제(power fail or DB crash)가 생겨도 commit된 transaction은 DB에 남아 있는다
    
    ‘영구적으로 저장한다’라고 할 때는 일반적으로 ‘비휘발성 메모리(HDD, SDD, …)에 저장함’을 의미한다
    
    기본적으로 transaction의 durability는 DBMS가 보장한다
  
  ### Commit
  
  - 지금까지 작업한 내용을 DB에 영구적으로 저장하라
  - transaction을 종료한다.
  
  ```sql
  # mysql
  START TRANSACTION;
  UPDATE account SET balance = balance - 2000000 WHERE id = 'J';
  UPDATE account SET balance = balance - 2000000 WHERE id = 'H';
  COMMIT;
  ```
  
  ### Rollback

  - 지금까지 작업들을 모두 취소하고 transaction 이전 상태로 되돌린다.
  - transaction을 종료한다.
  
  ```sql
  # mysql
  START TRANSACTION;
  UPDATE account SET balance = balance - 300000 WHERE id = 'J';
  SELECT * FROM account;
  ROLLBACK;
  ```
  
  ### Autocommit

  ```sql
  # mysql
  SELECT @@AUTOCOMMIT;
  ```

  - 각각의 SQL문을 자동으로 transaction 처리 해주는 개념
  - SQL문이 성공적으로 실행되면 자동으로 commit 한다
  - 실행 중에 문제가 발생한다면 알아서 rollback 한다
  - MySQL에서는 default로 autocommit이 enabled 되어 있다
  - 다른 DBMS에서도 대부분 같은 기능을 제공한다.

  ```sql
  # mysql
  START TRANSACT;
  UPDATE account SET balance = balance - 2000000 WHERE id = 'J';
  COMMIT;
  ```

  - START TRANSACTION 실행과 동시에 autocommit은 off 된다
  - COMMIT / ROLLBACK과 함께 transaction이 종료되면 원래 autocommit 상태로 돌아간다<br/><br/>

  ## trigger
    
  데이터베이스에서 어떤 이벤트가 발생했을 때 자동적으로 실행되는 프로시저(procedure)
  
  1. 사용자의 닉네임 변경 이력을 저장하는 트리거를 작성해보자.
    <img width="700" alt="db 51" src="https://github.com/crongcm/computer-science/assets/113030711/a634dbb7-73b8-4e5f-8b8e-819241c642c1">
    <img width="700" alt="db 52" src="https://github.com/crongcm/computer-science/assets/113030711/f9f33f3b-2d8a-49da-8be3-e3309e21aaad">

  2. 사용자가 마트에서 상품을 구매할 때 마다 지금까지 누적된 구매 비용을 구하는 트리거를 작성해보자.
    <img width="700" alt="db 53" src="https://github.com/crongcm/computer-science/assets/113030711/158ad1eb-a932-4e39-a1d4-c287ebf37834">
    ```sql
    insert into by (user_id, price, by_at) values (1, 5000, now());
    insert into by (user_id, price, by_at) values (1, 15000, now());
    Query OK, 1 row affected (0.01 sec)
    ```
    <img width="700" alt="db 54" src="https://github.com/crongcm/computer-science/assets/113030711/5535287b-acc9-4a6d-9bcb-eb33e346e8fe">

  ### trigger 사용 시 주의사항
  
  - 소스코드로는 발견할 수 없는 로직이기 때문에 어떠한 동작이 일어나는지 파악하기 어렵고 문제가 생겼을 때 대응하기 어렵다
  - 가시적이지 않아서 개발도, 관리도, 문제 파악도 힘들어진다
  - 과도한 트리거 사용은 DB에 부담을 주고 응답을 느리게 만든다
  - 디버깅이 어렵다
  - 문서 정리가 특히나 중요하다<br/><br/>

  ## schedule과 serializability(트랜잭션들이 동시에 실행될 때 isolation을 보장하는 기초 이론)
    
  ### Schedule
  
  - 여러 transaction들이 동시에 실행될 때 각 transaction에 속한 operation들의 실행 순서
    
  - 각 transaction 내의 operation들의 순서는 바뀌지 않는다
  
    <img width="700" alt="db 59" src="https://github.com/crongcm/computer-science/assets/113030711/57286231-3fb4-49a4-be26-bb4b504d9c45">
  
    <img width="700" alt="db 60" src="https://github.com/crongcm/computer-science/assets/113030711/8d96395f-d160-47ae-9929-3d705390fdb1">
  
    <img width="700" alt="db 61" src="https://github.com/crongcm/computer-science/assets/113030711/c86a1054-d8cc-4880-aa24-373852666a75">
  
    <img width="700" alt="db 62" src="https://github.com/crongcm/computer-science/assets/113030711/929c0d2b-bab4-4744-9dcb-24247c08bb76">
  
    <img width="700" alt="db 63" src="https://github.com/crongcm/computer-science/assets/113030711/07ca727c-963a-4b90-9a9c-76f91c58b226">

  ### Serial schedule
  
  - transaction들이 겹치지 않고 한 번에 하나씩 실행되는 schedule (sched.1, sched.2)
    
  - 한 번에 하나의 transaction만 실행되기 때문에 좋은 성능을 낼 수 없고 현실적으로 사용할 수 없는 방식
  
  ### Nonserial schedule
  
  - transaction들이 겹처서(interleaving) 실행되는 schedule (sched.3, sched.4)
    
  - transaction들이 겹쳐서 실행되기 때문에 동시성이 높아져서 같은 시간 동안 처리할 수 있다.
    
    ⚠️transaction들이 어떤 형태로 겹쳐서 실행되는지에 따라 이상한 결과가 나올 수 있다
  
  ### **conflict operations**
  
  - 하나의 schedule에 존재하는 두 operations에 대해서 사용할 수 있는 개념이다
    
  - 한 schedule 내에 있는 두 operations가 아래 세 가지 조건을 만족하면 '**두 operations는 conflict하다**'라고 말할 수 있다
  
    1. 두 operation이 서로 다른 transaction에 속해 있다
    
    2. 두 operation이 같은 데이터에 접근한다
    
    3. 두 operation 중에 적어도 하나는 데이터를 쓴다(write)
  
  ## **conflict equivalent**
  
  - 두 개의 schedule에 대해서 사용될 수 있는 개념이다
    
  - 두 개의 schedule이 아래의 두 가지 조건을 만족하면 '**두 schedule은 conflict equivalent하다**'라고 말할 수 있다
  
    1. 두 schedule은 같은 transaction들을 가진다
    
    2. 어떤(any) conflict operations의 순서도 양쪽 schedule이 모두 동일하다
  
  ## **conflict serializable**
  
  - 어느 한 schedule이 serial schedule과 conflict equivalent하다면, '**이 schedule은 conflict serializable하다**'라고 말할 수 있다
  
  - 다르게 표현하자면, 두 개의 schedule이 conflict equivalent 할 때, 한 schedule이 serial schedule이라면, '**다른 한 schedule은 conflict serializable하다**'라고 말할 수 있다
    
  - 여러 transaction을 동시에 실행해도 shedule이 confilct serializable하도록 보장하는 프로토콜을 적용

## recoverability
    
  ### unrecoverable schedule
  
  schedule 내에서 commit된 transaction이 rollback 된 transaction이 write 했었던 데이터를 읽은 경우
  
  rollback을 해도 이전 상태로 회복 불가능할 수 있기 때문에 이런 schedule은 DBMS가 허용하면 안된다
  
  ### recoverable schedule
  
  schedule 내에서 그 어떤 transaction도 자신이 읽은 데이터를 write한 transaction이 먼저 commit/rollback 전까지는 commit 하지 않는 경우
  
  rollback할 때 이전 상태로 온전히 돌아갈 수 있기 때문에 DBMS는 이런 schedule만 허용해야 한다
  
  ### cascading rollback
  
  하나의 transaction이 rollback하면 의존성이 있는 다른 transaction도 rollback 해야 한다
  
  여러 transaction의 rollback이 연쇄적으로 일어나면 처리하는 비용이 많이 든다
  
  ### strict schedule
  
  schedule 내에서 어떤 transaction도 commit 되지 않은 transaction들이 write한 데이터는 쓰지도 읽지도 않는 경우
  
  <img width="700" alt="db 64" src="https://github.com/crongcm/computer-science/assets/113030711/9a22e511-4b6e-439d-a8a5-2cc5f3e641a2">


## Isolation level

<img width="700" alt="db 65" src="https://github.com/crongcm/computer-science/assets/113030711/df4d034b-1055-42eb-a14e-1828058e54f9">

### Dirty read
<img width="700" alt="db 66" src="https://github.com/crongcm/computer-science/assets/113030711/fa36bf3b-ebc6-4714-8a50-703032b0048b">
<img width="700" alt="db 67" src="https://github.com/crongcm/computer-science/assets/113030711/045197ac-0481-4ba8-ac74-5d51ad48362d">

### Non-repeatable read (Fuzzy read)
<img width="700" alt="db 68" src="https://github.com/crongcm/computer-science/assets/113030711/2a8b3515-0814-49ee-978c-7eefb00da5f6">

### Phantom read
<img width="700" alt="db 69" src="https://github.com/crongcm/computer-science/assets/113030711/0e8f52cd-729d-4d5b-ae6a-4d50c09deab7">
<img width="700" alt="db 70" src="https://github.com/crongcm/computer-science/assets/113030711/7cb077b6-ab87-4731-a5cd-89ebd6f0f1b3">

### Dirty write
<img width="700" alt="db 71" src="https://github.com/crongcm/computer-science/assets/113030711/fb80bc82-c006-4780-90ee-79b11ab98a6e">

### Lost update
<img width="700" alt="db 72" src="https://github.com/crongcm/computer-science/assets/113030711/4bb76f94-91ec-4cba-98c1-a06395d50849">

### Read skew
<img width="700" alt="db 73" src="https://github.com/crongcm/computer-science/assets/113030711/bc0eb028-8804-486d-9cca-b3d4c2413168">

### Write skew
<img width="700" alt="db 74" src="https://github.com/crongcm/computer-science/assets/113030711/6ed77b8c-2aef-4f31-abab-f9ca25081968">

### Snapshot isolation
<img width="700" alt="db 75" src="https://github.com/crongcm/computer-science/assets/113030711/b85205ac-e45f-4630-8f4a-5cd683040e96"><br/><br/>

## Lock
    
### Write-lock (exclusive lock)

- read/write(insert, modify, delete)할 때 사용한다
- 다른 tx가 같은 데이터를 read/write 하는 것을 허용하지 않는다

### Read-lock (shared lock)

- read 할 때 사용한다
- 다른 tx가 같은 데이터를 read 하는 것은 허용한다

### 2PL protocol (two-phase locking)

한번 unlock이 되기 시작하면 새로운 lock을 획득하지 않는다

⚠️상황에 따라서 Deadlock이 발생할 수 있다

<img width="700" alt="db 76" src="https://github.com/crongcm/computer-science/assets/113030711/a066ab33-9186-4365-be65-0759430f0460">

### conservation 2PL
<img width="700" alt="db 77" src="https://github.com/crongcm/computer-science/assets/113030711/90500427-ac88-4c25-a115-27532abf0e1a">

### strict 2PL
<img width="700" alt="db 78" src="https://github.com/crongcm/computer-science/assets/113030711/8e5e31dd-82b0-49f9-b775-b62b189496fe">

### strong strict 2PL
<img width="700" alt="db 79" src="https://github.com/crongcm/computer-science/assets/113030711/320f89cb-9938-4f8e-8fb0-eb5593f47511">

read_lock 해제 시점에 밑으로 가기 때문에 처리량 이슈가 생길 수 있다

## MVCC (multi version concurrency control)
    
  데이터를 읽을 때 특정 시점 기준으로 가장 최근에 commit 된 데이터를 읽는다(Consistent read)
  
  데이터 변화(write) 이력을 관리한다
  
  read와 write는 서로를 block하지 않는다
  
  ### read uncommitted
  
  - MVCC는 committed된 데이터를 읽기 때문에 이 level에서는 보통 MVCC가 적용되지 않는다
  
  ### read committed
  
  - read하는 시간을 기준으로 그전에 commit된 데이터를 읽는다
  
  ### repeatable read
  
  - tx 시작 시간 기준으로 그 전에 commit된 데이터를 읽는다
  
  ### Serializable
  
  - MVCC로 동작하기 보다는 lock으로 동작한다
  
  - repeatable read와 유사
  
  - tx의 모든 평범한 select문은 암묵적으로 select … for share 처럼 동작한다
  
## repeatable read 문제 해결

  ### lost update
  
  - Locking update
  
    - SELECT … FOR UPDATE;
  
  - Locking read
  
    - SELECT … FOR UPDATE; (exclusive lock)
  
    - SELECT … FOR SHARE; (shared lock)
  
    - 최근에 commit 된 내용을 읽는다
  
  ### write skew
  
  - Locking read를 사용하면 된다
      
## Functional dependency(함수 종속)
    
  한 테이블에 있는 두 개의 attribute(s) 집합(set) 사이의 제약(a constraint)
  
  X 값에 따라 Y 값이 유일하게(uniquely) 결정될 때 ‘X가 Y를 함수적으로 결정한다’, ‘Y가 X에 함수적으로 의존한다’라고 말할 수 있고, 두 집합 사이의 이러한 제약 관계를 functional dependency라고 부른다. 
  
  X → Y 로 표시
  
  <img width="700" alt="db 80" src="https://github.com/crongcm/computer-science/assets/113030711/00480a56-5d7d-4f74-a10d-147f0384f7e1">

  ### Functional dependency 파악하기
  
  테이블의 스키마를 보고 의미적으로 파악해야 한다
  
  즉, 테이블의 state를 보고 FD를 파악해서는 안된다
  
  <img width="700" alt="db 81" src="https://github.com/crongcm/computer-science/assets/113030711/c8b65fae-b18e-4259-b1db-ff4d82bb021f">

  ### {} → Y
  
  Y 값은 언제나 하나만 갖는다.
  
  <img width="700" alt="db 82" src="https://github.com/crongcm/computer-science/assets/113030711/098a9a5b-99c4-4671-934c-3fc44c150068">

  ### trivial functional dependency
  
  X → Y가 유효할 때, Y가 X의 부분 집합 일 때 trivial FD라고 한다
  
  ```
  {a, b, c} ->  {   c  } is trivial FD
  {a, b, c} ->  { a, c } is trivial FD
  {a, b, c} -> {a, b, c} is trivial FD
  ```
  
  ### Non-trivial functional dependency
  
  X → Y가 유효할 때, Y가 X의 부분 집합이 아닐 때 non-trivial FD라고 한다
  
  ```
  {a, b, c} ->  {b, c, d} is non-trivial FD
  {a, b, c} ->  { d, e }  is non-trivial FD & completely non-trivial FD
  ```
  
  ### Partial functional dependency
  
  X → Y가 유효할 때, X의 어떤 proper 부분집합이라도 Y를 결정지을 수 있다면, partial FD
  
  <img width="1049" alt="db 83" src="https://github.com/crongcm/computer-science/assets/113030711/9f4c4c4b-0f12-4841-8140-7f2b153ec375">

  ```
  when {empl_idm, empl_name} -> {birth_date} holds,
  because {empl_id} can determine {birth_date},
  then this FD is partial FD
  ```
  
  ### Full functional dependency
  
  X → Y가 유효할 때, X의 모든 proper 부분집합이 Y를 결정지을 수 없다면 full FD
  
  ```
  when {stu_id, class_id} -> {grade} holds,
  because {stu_id}, {class_id}, {} can NOT determine {grade},
  then this FD is full FD
  ```
    
## DB 정규화(normalization)
    
  데이터 중복과 insertion, update, deletion anomaly를 최소화하기 위해 일련의 normal forms(NF)에 따라 relational DB를 구성하는 과정
  
  <img width="700" alt="db 84" src="https://github.com/crongcm/computer-science/assets/113030711/255533df-a79a-4f45-a834-747ff188b69d">

  ### 1NF, 2NF, 3NF, BCNF
  
  FD와 key만으로 정의되는 normal forms
  
  3NF까지 도달하면 정규화 됐다고 말하기도 함
  
  보통 실무에서는 3NF 혹은 BCNF까지 진행 (많이 해도 4NF 정도까지만 진행)
  
  <img width="700" alt="db 85" src="https://github.com/crongcm/computer-science/assets/113030711/ae11c799-4b56-430f-9e18-4f2cec9b377e">

  ### Key
  
  **super key** - table에서 tuple들을 unique하게 식별할 수 있는 attributes set
  
  **(candidate) key** - 어느 한 attribute라도 제거하면 unique하게 tuple를 식별할 수 없는 super key
  
  {account_id}, {bank_name, account_num}
  
  **primary key** - table에서 tuple들을 unique하게 식별하려고 선택된 (candidate) key
  
  {account_id}]
  
  **prime attribute** - 임의의 key에 속하는 attribute
  
  account_id, bank_name, account_num
  
  **non-prime attribute** - 어떠한 key에도 속하지 않는 attribute
  
  class, ratio, empl_id, empl_name, card_id
  
  ### Functional dependency
  
  <img width="700" alt="db 86" src="https://github.com/crongcm/computer-science/assets/113030711/f4586eb5-6720-4e99-993e-b3c8d7ff0476">

  {account_id} → {bank_name, account_num, class, ratio, empl_id, empl_name, card_id}
  
  <img width="700" alt="db 87" src="https://github.com/crongcm/computer-science/assets/113030711/0871360f-07f1-45cb-b0dc-2fbdcf85239e">

  <img width="700" alt="db 88" src="https://github.com/crongcm/computer-science/assets/113030711/bc9c1d2d-8ee7-4a49-902a-008667e04727">

  ### Normalization
  
  <img width="700" alt="db 89" src="https://github.com/crongcm/computer-science/assets/113030711/d58acf4b-eb81-4ba0-8c08-3e0c93ba12f0">

  ### 1NF
  
  attribute의 value는 반드시 나눠질 수 없는 단일한 값이어야 한다
  
  <img width="700" alt="db 90" src="https://github.com/crongcm/computer-science/assets/113030711/6addf2f0-0a70-447b-8c4e-d005facedc88">

  ### 2NF
  
  모든 non-prime attribute는 모든 key에 fully functionally dependent 해야 한다
  
  <img width="700" alt="db 91" src="https://github.com/crongcm/computer-science/assets/113030711/95a7f43e-8cdf-4cf8-a24c-45ec66a3a3b4">

  <img width="700" alt="db 92" src="https://github.com/crongcm/computer-science/assets/113030711/cd21a0f4-a080-46af-83c6-86b11ce74574">

  ### 2NF 해결
  
  EMPLOYEE_ACCOUNT 테이블 에서 card_id를 제거하고, a21 중복데이터를 삭제한다.
  
  <img width="700" alt="db 93" src="https://github.com/crongcm/computer-science/assets/113030711/56561c64-521a-47c6-a4e8-80b8641e1d13">

  ### 3NF
  
  모든 non-prime attribute는 어떤 key에도 transitively dependent 하면 안된다
  
  non-prime attribute와 non-prime attribute 사이에는 FD가 있으면 안된다
  
  ❗ {empl_id} → {empl_name}
  
  <img width="700" alt="db 94" src="https://github.com/crongcm/computer-science/assets/113030711/73960737-df07-4288-9761-51336f75cede">

  ### transitive FD
  
  X → Y & Y → Z가 유효할 때, X → Z를 transitive FD 라고 한다
  
  Y와 Z가 어떤 키에 대해서도 부분집합이 아니어야 한다는 제약 조건이 있다.
  
  <img width="700" alt="db 95" src="https://github.com/crongcm/computer-science/assets/113030711/46ae5b4d-b892-4ccc-8a1c-114750d7c978">

  ### BCNF
  
  모든 유효한 non-trivial FD X → Y는 X가 super key여야 한다
  
  <img width="700" alt="db 96" src="https://github.com/crongcm/computer-science/assets/113030711/b8a09249-0699-4180-88b2-0b4693583806">

  <img width="700" alt="db 97" src="https://github.com/crongcm/computer-science/assets/113030711/a03d0188-c8f3-410b-a70a-c0fb147772e4">

  <img width="700" alt="db 98" src="https://github.com/crongcm/computer-science/assets/113030711/c0122659-1997-4ab7-b12b-753164964f10">

  ### 2NF 참고사항
  
  2NF는 key가 composite key가 아니라면 2NF는 자동적으로 만족한다 ?  

  <img width="700" alt="db 99" src="https://github.com/crongcm/computer-science/assets/113030711/eb2f1e4a-668c-42c4-8b10-5836c0ec0c01">

  <img width="700" alt="db 100" src="https://github.com/crongcm/computer-science/assets/113030711/bbe5d41f-da30-4b81-a9af-b691382bc8f9">

  ### denormalization
  
  DB를 설계할 때 과도한 조인과 중복 데이터 최소화 사이에서 적정 수준을 잘 선택할 필요가 있다
  
  <img width="700" alt="db 101" src="https://github.com/crongcm/computer-science/assets/113030711/ac3b9d7e-132b-4b31-b969-c95106b068f0">

  <img width="700" alt="db 102" src="https://github.com/crongcm/computer-science/assets/113030711/d91f3bf3-d071-46e5-b470-d8be8d93c044">

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
    - a 검색시 인덱스를 통해 binary search 후 b는 full scan
    <img width="700" alt="db 106" src="https://github.com/crongcm/computer-science/assets/113030711/46e48eac-8a35-498d-90c9-4511171029c2">
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
    
## Partitioning, Sharding, Replication
    
  <img width="700" alt="db 112" src="https://github.com/crongcm/computer-science/assets/113030711/d8f0e892-0c2c-46d2-a244-da755f0d0f15">

  ### Partitioning
  
  database table을 더 작은 table들로 나누는 것
  
  <img width="700" alt="db 113" src="https://github.com/crongcm/computer-science/assets/113030711/f7919ba7-b1c0-47c0-b578-2680f2e6e0e7">

  ### vertical partitioning
  
  <img width="700" alt="db 114" src="https://github.com/crongcm/computer-science/assets/113030711/0c073d37-a03a-4654-8f88-1697c328b592">

  정규화
  
  <img width="700" alt="db 115" src="https://github.com/crongcm/computer-science/assets/113030711/3008c4fd-015d-4e51-a7e9-5947a8bf5888">

  content의 경우 데이터가 크기 때문에 파티셔닝을 통해 테이블을 분리하여
  
  article 셀렉트 시 I/O 비용을 줄일 수 있다. (select시 모든 컬럼을 가져온 후 필터링을 하기 때문에)
  
  <img width="700" alt="db 116" src="https://github.com/crongcm/computer-science/assets/113030711/be353a89-07f4-4735-9271-ce786aa17875">

  ### horizontal partitioning
  
  <img width="700" alt="db 117" src="https://github.com/crongcm/computer-science/assets/113030711/2a832809-9e45-4864-aca5-3a10351d1fcc">

  <img width="700" alt="db 118" src="https://github.com/crongcm/computer-science/assets/113030711/5f5a50f2-d936-4d43-988a-0947c1dbe53c">

  ### hash-based
  
  - 가장 많이 사용될 패턴에 따라 partition key를 정하는 것이 중요
  - 데이터가 균등하게 분배될 수 있도록 hash function을 잘 정의하는 것도 중요
  - hash-based horizontal partitioning은 한번 partition이 나눠져서 사용되면 이후에 partition을 추가하기 까다롭다
  
  partition key = user_id
  
  dingyo가 구독한 채널들 정보를 모두 조회하고 싶다면 ? where user_id = dingyo
  
  id가 1인 channel을 구독한 사용자의 id를 모두 조회하고 싶다면 ? where channel_id = 1 (두 테이블 모두 스캔)
  
  <img width="700" alt="db 119" src="https://github.com/crongcm/computer-science/assets/113030711/d186bf4b-bd4c-43f5-a5c6-3634461f0b4a">

  ### sharding
  
  <img width="691" alt="db 120" src="https://github.com/crongcm/computer-science/assets/113030711/56596228-1440-4fbc-a277-253f7b391bac">

  - horizontal partitioning처럼 동작
  - 각 partition이 독립된 DB 서버에 저장
  - 각 partition들을 서로 다른 DB 서버에 저장
  - 부하(load)를 분산시키는 목적
  - partition key를 shard key라고 부름
  - 각 partition을 shard라고 부름
  
  ### replication
  
  mater/primary/leader - read/write
  
  slave/secondary/replica - read
  
  master에서 문제가 생겼을 경우 slave를 master로 변경하여 fail over 할 수 있다
  
  - 고가용성 (High Availablility)HA
  - 서버 부하(load)를 낮춘다
    
## DBCP(database connection pool)
    
  백엔드 서버에서 요청을 했을 때 TCP 기반으로 동작하게 되는데 이때 커넥션 연결시 3-handshake, 커넥션 끊을시 4-way-handshake라고 하는데 데이터를 주고 받는 데 비용을 소모하게 된다
  
  ❗매번 connection을 열고 닫는 시간적인 비용 발생
  
  connection을 미리 연결해 놓고 pool에 담아 connection을 재사용 하는 것을 말한다
  
  ### DBCP 설정 방법
  
  1. DB 서버 설정
  - max_connections
      - client와 맺을 수 있는 최대 connection 수
  
  ex) 만약 max_connections 수가 4, DBCP의 최대 connection 수가 4라면 ?
  
  적절한 값을 설정해야 서비스 확장을 위해 신규 서버를 증설하거나, DBCP의 커넥션 수를 늘린다해도 에러가 발생하지 않는다
  
  - wait_timeout
      - connection이 inactive 할 때 다시 요청이 오기까지 얼마의 시간을 기다린 뒤에 close 할 것인지를 결정
      - 시간 내에 요청이 도착하면 0으로 초기화
  
  비정상적인 connection 종료
  
  connection 다 쓰고 반환이 안됨
  
  네트워크 단절
  
  2. DBCP 설정
  - minimumIdle
      - pool에서 유지하는 최소한의 idle(유휴) connection 수
      - idle connection 수가 minimumIdle보다 작고, 전체 connection 수도 maximumPoolSize보다 작다면 신속하게 추가로 connection을 만든다
      - 기본 값은 maximumPoolSize와 동일(=pool size 고정)
  - maximumPoolSize
      - pool이 가질 수 있는 최대 connection 수
      - idle과 active(in-use) connection 합쳐서 최대 수
  
  ex) 만약 minimumIdle이 2, maximumPoolSize가 4라면?
  
  요청이 들어와 유휴 자원이 2개에서 1개가 되면 connection을 만들어 3개, 또 요청이 들어와 2개를 사용하고 있다면 connection을 연결해 4개, 또 요청이 들어와 3개를 사용하면 그대로 4개, 추후 모든 요청이 완료되면 4개의 connection에서 2개의 connection은 끊어준다.
  
  - maxLifetime
      - pool에서 connection의 최대 수명
      - maxLifetime을 넘기면 idel일 경우 pool에서 바로 제거, active인 경우 pool로 반환된 후 제거
      - pool로 반환이 안되면 maxLifetime 동작 안함
      - DB의 connection time limit(mysql의 경우 wait_timeout) 보다 몇 초 짧게 설정해야
  
  ex) 만약 DB의 wait_timeout 이 60초, DBCP의 maxLifetime이 60초 라면?
  
  - connectionTimeout
      - pool에서 connection을 받기 위한 대기 시간
  
  ex) 만약 connectionTimeout이 30초라면 ?
  
  ### 적절한 connection 수를 찾기 위한 과정
  
  - 모니터링 환경 구축 (서버 리소스, 서버 스레드 수, DBCP 등등)
  - 백엔드 시스템 부하 테스트
  - request per second와 avg response time 확인 (부하가 발생되는 지점을 확인)
  - 백엔드 서버, DB 서버의 CPU, Memory 등등 리소스 사용률 확인
  - secondary 추가, cache layer, sharding
  - thread per request 모델이라면 active thread 수 확인 (쓰레드 풀에 비해 쓰레드가 남을 경우)
  - DBCP의 active connection 수 확인
  - 사용할 백엔드 서버 수를 고려하여 DBCP의 max pool size 결정
    
## NoSQL
    
  - relational database
    - 새로운 타입이 추가될 경우 스키마를 계속 변경해 줘야한다
    - multi-master, sharding 같은 방법도 있지만 일반적으로 RDB는 scale-out에 유연한 DB는 아님
    - ACID를 보장하려다 보니 DB 서버의 performance에 어느 정도 영향을 미침
    - 인터넷 사용자가 늘어나고, SNS 서비스가 생기면서 높은 처리량과 짧은 응답성을 요구함
      - high-throughput 요구됨
      - low-latency 요구됨
      - 비정형 데이터의 증가

### NoSQL의 특징

- flexible schema - `application 레벨에서 스키마 관리가 필요`
- 중복 허용 (join 회피) - `application 레벨에서 중복된 데이터들이 모두 최신데이터를 유지할 수 있도록 관리해야 함`
- scale-out - 서버 여러대로 하나의 클러스터를 구성하여 사용
- ACID의 일부를 포기하고 high-throughput, low-latency 추구 - `금융 시스템처럼 consistency가 중요한 환경에서는 사용하기가 조심스러움`

### Redis

- in-memory, key-value database, cache or …
- data type : stirngs, lists, sets, hashes, sorted sets, ..
- hash-based charded cluster
- High Availability (replication, automatic failover)
