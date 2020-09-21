# 연결 리스트(Linked List)

## 1. 연결 리스트(Linked List)의 구조
- 배열은 순차적으로 연결된 공간에 데이터를 나열하는 데이터 구조
- 링크드 리스트는 떨어진 곳에 존재하는 데이터를 화살표로 연결해서 관리하는 데이터 구조
- 본래 C언어에서는 주요한 데이터 구조이지만, 파이썬은 리스트 타입이 링크드 리스트의 기능을 모두 지원
- 연결 리스트 기본 구조와 용어
    - 노드(Node) : 데이터 저장 단위(데이터값, 포인터로 구성)
    - 포인터(pointer) : 각 노드 안에서, 다음이나 이전의 노드와의 연결 정보를 가지고 있는 공간
- 일반적인 연결 리스트 형태
<p align="center"><img src="/Data%20Structure/img/linkedlist01.png" width = "500px"></p><br>

## 2. 간단한 연결 리스트 예
### Node 구현
- 보통 파이썬에서 링크드 리스트 구현시, 파이썬 클래스를 활용함
  - 파이썬 객체지향 문법 이해 필요

```python
    class Node:
        def __init__(self, data):
            self.data = data
            self.next = None
```
```python
    class Node:
        def __init__(self, data, next=None): #인자 1개 쓰면 데이터, 주소는 None / 2게 쓰면 데이터, 주소
            self.data = data
            self.next = next
```

### Node와 Node 연결하기 (포인터 활용)
```python
    node1 = Node(1)
    node2 = Node(2)
    node1.next = node2
    head = node1
```

### 연결 리스트로 데이터 추가하기
```python
    class Node:
        def __init__(self, data, next=None):
            self.data = data
            self.next = next

    def add(data):
        node = head
        while node.next: #다음 노드가 있다면!
            node = node.next
        node.next = Node(data) 

    node1 = Node(1)
    head = node1
    for index in range(2, 10):
        add(index)
```

### 연결 리스트 데이터 출력하기(검색하기)
```
    node = head
    while node.next:
        print(node.data)
        node = node.next
    print(node.data)
```