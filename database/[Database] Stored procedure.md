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
