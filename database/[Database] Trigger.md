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
