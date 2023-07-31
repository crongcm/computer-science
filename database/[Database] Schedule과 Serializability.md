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
