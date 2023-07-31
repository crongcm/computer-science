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
