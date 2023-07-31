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
      
