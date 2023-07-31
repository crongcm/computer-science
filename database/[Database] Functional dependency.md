## Functional dependency(함수 종속)

한 테이블에 있는 두 개의 attribute(s) 집합(set) 사이의 제약(a constraint)

X 값에 따라 Y 값이 유일하게(uniquely) 결정될 때 ‘X가 Y를 함수적으로 결정한다’, ‘Y가 X에 함수적으로 의존한다’라고 말할 수 있고, 두 집합 사이의 이러한 제약 관계를 functional dependency라고 부른다.

X → Y 로 표시

  <img width="700" alt="db 80" src="https://github.com/crongcm/computer-science/assets/113030711/00480a56-5d7d-4f74-a10d-147f0384f7e1">

### Functional dependency 파악하기

테이블의 스키마를 보고 의미적으로 파악해야 한다

즉, 테이블의 state를 보고 FD를 파악해서는 안된다

  <img width="700" alt="db 81" src="https://github.com/crongcm/computer-science/assets/113030711/c8b65fae-b18e-4259-b1db-ff4d82bb021f">

### {} → Y

Y 값은 언제나 하나만 갖는다.

  <img width="700" alt="db 82" src="https://github.com/crongcm/computer-science/assets/113030711/098a9a5b-99c4-4671-934c-3fc44c150068">

### trivial functional dependency

X → Y가 유효할 때, Y가 X의 부분 집합 일 때 trivial FD라고 한다

  ```
  {a, b, c} ->  {   c  } is trivial FD
  {a, b, c} ->  { a, c } is trivial FD
  {a, b, c} -> {a, b, c} is trivial FD
  ```

### Non-trivial functional dependency

X → Y가 유효할 때, Y가 X의 부분 집합이 아닐 때 non-trivial FD라고 한다

  ```
  {a, b, c} ->  {b, c, d} is non-trivial FD
  {a, b, c} ->  { d, e }  is non-trivial FD & completely non-trivial FD
  ```

### Partial functional dependency

X → Y가 유효할 때, X의 어떤 proper 부분집합이라도 Y를 결정지을 수 있다면, partial FD

  <img width="1049" alt="db 83" src="https://github.com/crongcm/computer-science/assets/113030711/9f4c4c4b-0f12-4841-8140-7f2b153ec375">

  ```
  when {empl_idm, empl_name} -> {birth_date} holds,
  because {empl_id} can determine {birth_date},
  then this FD is partial FD
  ```

### Full functional dependency

X → Y가 유효할 때, X의 모든 proper 부분집합이 Y를 결정지을 수 없다면 full FD

  ```
  when {stu_id, class_id} -> {grade} holds,
  because {stu_id}, {class_id}, {} can NOT determine {grade},
  then this FD is full FD
  ```
    
