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
