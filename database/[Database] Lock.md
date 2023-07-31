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
