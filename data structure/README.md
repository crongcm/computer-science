# Data Structure

## Array

- Array
    
  - 같은 타입의 데이터들을 저장하는 자료 구조
  - 연속된 메모리 공간에 데이터들을 저장
  - 데이터들은 각각은 이름이 없지만 인덱스로 접근 가능
    
  - 연속된 메모리 공간에 데이터들을 저장하기 때문에 cpu cache를 통해 같은 배열에 있는 다른 데이터에 접근하는 시간을 단축할 수 있다.
  
  
- 1차원 배열
  
    <img width="700" alt="ds" src="https://github.com/crongcm/computer-science/assets/113030711/f8526048-d978-46bd-9c5a-0c2b0f48aa03">

- 2차원 배열
  
    <img width="700" alt="ds 1" src="https://github.com/crongcm/computer-science/assets/113030711/f81e813e-3250-4987-a788-881cf6fffdc8">
    
- 객체를 배열에 담았을 경우
  
    <img width="700" alt="ds 2" src="https://github.com/crongcm/computer-science/assets/113030711/b267bcbb-109b-4fb1-bbfe-42aadabc7107">
    
### Dynamic array(동적 배열)
  
  - 크기가 변할 수 있는 array
  - 데이터를 더하거나 빼는 것이 가능한 자료 구조
  - resizable array, array list 등등으로 불림
  

  4개의 아이템을 담을 수 있는 공간에 3개의 아이템이 들어가 있다.<br/>
  추가로 하나의 아이템을 넣게되면 4개가 되고 배열이 가득차게 된다.<br/>
  추가로 하나의 아이템을 넣게되면 4개의 배열의 2배 크기인 배열을 생성하고 기존 배열을 복사한 뒤 새로운 아이템을 추가한다.<br/>
  결론적으로 가득찰 경우 2배 크기의 배열이 생성되게 된다.
  
  ### Associative arra(연관 배열)
  
  - key-value pair들을 저장하는 ADT
  - 같은 key를 가지는 pair는 최대 한 개만 존재
  - map, dictionary라고 불리기도 함<br/><br/>

## List
    
### List

- 값(value)들을 저장하는 추상자료형(ADT)
- 순서가 있음
- 중복을 허용

### Array list

<img width="700" alt="ds 3" src="https://github.com/crongcm/computer-science/assets/113030711/3da7bae0-bc13-42ad-b208-36533254d0c1">

### Linked list

<img width="700" alt="ds 4" src="https://github.com/crongcm/computer-science/assets/113030711/9e441bc0-332f-4e3b-8504-c974ec4486e1">
<img width="700" alt="ds 5" src="https://github.com/crongcm/computer-science/assets/113030711/5c8422aa-f5f8-4adc-8059-443631348e01"><br/><br/>
   

## Map
    
### Hash table(hash map)

- 배열과 해시 함수를 사용하여 map을 구현한 자료구조
- (일반적으로) 상수 시간으로 데이터에 접근하기 때문에 빠름

### Hash function

- 임의의 크기를 가지는 type의 데이터를 고정된 크기를 가지는 type의 데이터로 변화하는 함수
- (hash table에서) 임의의 데이터를 정수로 변환하는 함수

### Hash collision

- key는 다른데 hash가 같을 때
- key도 hash도 다른데 hash % map_capa 결과가 같을 때

### 해시 충돌 해결방법

  Separate chaining - 해시 충돌이 발생했을 경우 메모리안에 리스트를 만들어 데이터를 체이닝 하는 방식<br/>
  Open addressing(linear probing) - 해시 충돌이 발생했을 경우 바로 다음 버킷(다음에 비어있는 메모리 공간)에 저장하는 방식<br/>
  삭제시 더미값을 넣어주거나 다음 버킷에 있는 값을 이동시켜줘야 한다. 조회시 더미가 없을 경우 값이 없는 걸로 인식하고 찾을 수가 없다.<br/><br/>

## Set
    
### Set

- 데이터를 저장하는 추상자료형(ADT)
- 순서를 보장하지 않음
- 데이터 중복을 허용하지 않음
- 데이터 조회(search)가 List보다 빠름

중복을 제거 할 때, 데이터의 존재 여부를 확인해야 할 때

### Hash set

- 해시 테이블(hash table)을 사용하여 구현하기 때문에 크기 상관없이 데이터 조회가 빠름

Java에서 HashSet은 HashMap과 같다

<img width="700" alt="ds 6" src="https://github.com/crongcm/computer-science/assets/113030711/f09c535d-67f5-4c90-9de5-a1bd9bad71eb">
<img width="700" alt="ds 7" src="https://github.com/crongcm/computer-science/assets/113030711/a9297742-e765-4f13-bd51-6ec9a07ffc54">
<img width="700" alt="ds 8" src="https://github.com/crongcm/computer-science/assets/113030711/28190ad6-d263-4ad4-b6ef-36fc6f492674"><br/><br/>

    
## binary search tree
    
- 모든 노드의 왼쪽 서브 트리는 해당 노드의 값보다 작은 값들만 가지고 모든 노드의 오른쪽 서브 트리는 해당 노드의 값보다 큰 값들만 가진다.
- 이진 탐색 트리의 최소값
  - 트리의 가장 왼쪽에 존재
- 이진 탐색 트리의 최대값
  - 트리의 가장 오른쪽에 존재
    
<img width="700" alt="ds 9" src="https://github.com/crongcm/computer-science/assets/113030711/b35a26d6-be4b-4df2-a119-675ccfc206be">

<img width="700" alt="ds 10" src="https://github.com/crongcm/computer-science/assets/113030711/bc429b14-f319-4e55-8bea-cef2693cf80d">

<img width="700" alt="ds 11" src="https://github.com/crongcm/computer-science/assets/113030711/db01ea06-b980-4522-800f-1019ef6885b8">

<img width="700" alt="ds 12" src="https://github.com/crongcm/computer-science/assets/113030711/860676c5-208c-44f0-8b67-1877122e4831">

<img width="700" alt="ds 13" src="https://github.com/crongcm/computer-science/assets/113030711/e3c91dc3-d1e3-49cc-b771-042601c2f4d9"><br/><br/>

    
## AVL 트리
    
### AVL 트리

  - 이진 탐색 트리(BST)의 한 종류
  - 스스로 균형을 잡는 트리
  - balnace factor를 통해 균형 유지

  - 삽입/삭제가 발생한 위치에서 루트 노드로 거꾸로 올라오면서 BF를 확인하여 균형이 깨졌다면 재조정을 해준다.
  - 최악의 경우에도 삽입/삭제/검색의 시간 복잡도는 O(logN)이다
  - 엄격하게 균형을 유지하기 때문에 삽입/삭제 시 트리 균형을 확인하고 만약 균형이 깨졋다면 트리 구조를 재조정하기 때문에 이 때 시간이 꽤 소요된다.

<img width="700" alt="ds 14" src="https://github.com/crongcm/computer-science/assets/113030711/2833ebfb-318a-4646-9935-32781669fe5e">

<img width="700" alt="ds 15" src="https://github.com/crongcm/computer-science/assets/113030711/7b030ff7-5ab7-4116-88e3-c0e347405420"><br/><br/>

    
## Red-Black 트리
    
<img width="700" alt="ds 16" src="https://github.com/crongcm/computer-science/assets/113030711/70963aad-85f0-43d3-bb1b-b084650f3396"><br/><br/>

    
## Divide and Conquer

어떤 문제를 유사한 형태를 가지는 더 작은 크기의 서브 문제들로 나눈 후 이들을 재귀적으로 같은 방식으로 해결한 뒤 각 서브 문제들을 해결한 결과를 활용하여 원래 문제를 해결하는 방식
