##  list

array -  여러 element 들이 연속된 메모리에 순차적을 저장

list - 여러 분리된 노드가 서로 연결되어 있는 구조

<br>

- 어떤 노드에 접근 시 시간복잡도 array O(1) list O(n)
- 어떤 위치 항목에 삽입 하려면 array O(n) list O(1)

#### list 항목 추가 삭제

list .append() -시간복잡도 O(1)

list.pop()  - 시간복잡도 O(1)

#### 항복 검색

list.remove() - 시간복잡도 O(n)

list.index() -시간복잡도 O(n)

<br>

del 문 

```python
a=[1,2,3,4]
del a[0] # 0번째 항목 삭제
del a[0:2] # 범위 지정 삭제
del a #자체를 삭제
```

<br>

#### list unpacking

```python
a=[1,2,3,4]
a,*y  # * iterator 를 사용해 특정 변수 뒤에 값을 나눠줌
a # 1
*y #[2,3,4]
```

<br>

#### list method test

import timeit 를 추가해 테스트시간을 확인 할 수 있음	