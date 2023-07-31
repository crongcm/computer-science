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

