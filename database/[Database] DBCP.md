## DBCP(database connection pool)

백엔드 서버에서 요청을 했을 때 TCP 기반으로 동작하게 되는데 이때 커넥션 연결시 3-handshake, 커넥션 끊을시 4-way-handshake라고 하는데 데이터를 주고 받는 데 비용을 소모하게 된다

❗매번 connection을 열고 닫는 시간적인 비용 발생

connection을 미리 연결해 놓고 pool에 담아 connection을 재사용 하는 것을 말한다

### DBCP 설정 방법

1. DB 서버 설정
- max_connections
    - client와 맺을 수 있는 최대 connection 수
```
ex) 만약 max_connections 수가 4, DBCP의 최대 connection 수가 4라면 ?
적절한 값을 설정해야 서비스 확장을 위해 신규 서버를 증설하거나, DBCP의 커넥션 수를 늘린다해도 에러가 발생하지 않는다
```
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

```    
ex) 만약 minimumIdle이 2, maximumPoolSize가 4라면?
요청이 들어와 유휴 자원이 2개에서 1개가 되면 connection을 만들어 3개, 또 요청이 들어와 2개를 사용하고 있다면 connection을 연결해 4개, 또 요청이 들어와 3개를 사용하면 그대로 4개, 추후 모든 요청이 완료되면 4개의 connection에서 2개의 connection은 끊어준다.
```

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
