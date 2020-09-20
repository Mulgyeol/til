# 덱(Deque)
- 덱(Deque)은 데이터 값을 저장하는 기본 자료구조로, 일차원의 선형구조이다.
- 덱은 스택과 큐의 연산을 모두 지원하는 자료구조로, 양 끝에서 모두 삽입과 삭제가 가능한 큐라고 생각하면 된다.
- 나머지 부가적인 덱의 길이를 반환하는 연산이나 덱이 비어있는지 확인하는 연산 등은 스택과 큐에 구현되어 있는 연산들과 유사하게 구현된다.

## Python의 모듈을 이용하기
- Python의 queue 모듈은 thread 등을 잘 처리하기 위해 (문제 풀이에서는 불필요한) 동기화 과정을 거치기 때문에 collections.deque에 비해 많이 느리다.
- Deque은 collections라는 모듈에 deque라는 클래스로 이미 구현되어 있다.
- 양 끝에서 삽입과 삭제를 할 수 있어야하므로 `양방향 연결리스트(Doubly Linked List)로 구성되어 있다.
- 단순한 값의 삽입, 삭제는 O(1)의 시간이 걸리기 때문에 효율적이다.
- 메소드(method)
    - append(x)
    - appendleft(x)
    - extend(iterable)
        - `iterable argument` 는 arguments의 각 요소를 하나씩 반환 가능한 object를 의미한다.
    - extendleft(iterable)
    - pop()
    - popleft()
    - rotate
        - collections.deque.rotate(n)은 요소들(elements)을 n값 만큼 회전 해주는 메소드이다. n의 값이 음수(negative)이면 왼쪽으로 회전하고, n의 값이 양수이면 오른쪽으로 회전한다.
        

```python
from collections import deque

deq = deque()
print(type(d)) # <class 'collections.dequq>'

# Stack이나 Queue 처럼 덱의 오른쪾에 요소 삽입 : append
for i in range(10):
    d.append(i)
print(d) # deque([0, 1, 2, .... , 9])

# 덱의 왼쪽에 요소 삽입 : appendleft
d.appendleft(10)
print(d) #deque([10, 0, 1, 2, .... , 9])

# 덱 중간에 요소 삽입 : insert
d.insert(5,11)
print(d) # deque([10, 0, 1, 2, 3, 11, 4, 5, 6, 7, 8, 9]) 첫 번째에 인덱스, 해당 위치에 있던 요소부터는 뒤로 밀림

# 덱 왼쪽 / 오른쪽에 iterable한 객체를 통쨰로 append해서 연장시키는 연산 : extendleft / extend
d.extend([0,0,0])
print(d) #deque([10, 0, 1, 2, 3, 11, 4, 5, 6, 7, 8, 9, 0, 0, 0])
d.extendleft([1,1,1])
print(d) #deque([1, 1, 1, 10, 0, 1, 2, 3, 11, 4, 5, 6, 7, 8, 9, 0, 0, 0])

# Stack처럼 덱의 오른쪽에서 요소 삭제 : pop
for i in range(10):
    d.pop()
print(d) #deque([1, 1, 1, 10, 0, 1, 2, 3])

# Queue처럼 덱의 오른쪽에서 요소 삭제 : popleft
for i in range(10):
    d.popleft()
print(d) #deque([10, 0, 1, 2, 3])

print(list(d)) #작업을 완료한 후에는 리스트처럼 이용할 수 있음
```