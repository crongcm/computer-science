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
