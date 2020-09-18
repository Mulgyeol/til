# 큐(Queue)

## 1. 큐의 구조
- 줄을 서는 행위와 유사
- 가장 먼저 넣은 데이터를 가장 먼저 꺼낼 수 있는 구조
    - 식당에서 가장 먼저 줄을 선 사람이 제일 먼저 음식점에 입장하는 것과 동일
    - FIFO(First-In, First-Out) 또는 LILO(Last-In, Last-Out) 방식으로 스택과 꺼내는 순서가 반대

## 2. 알아둘 용어
- Enqueue : 큐에 데이터를 넣는 기능
- Dequeue : 큐에서 데이터를 꺼내는 기능

## 3. 파이썬 queue 라이브러리
- **quque 라이브러리에는 다양한 큐 구조로 Queue(), LifoQueue(), PriorityQueue()를 제공**
- 프로그램을 작설할 때 프로그램에 따라 적합한 자료 구조를 사용
    - Queue() : 가장 일반적인 큐 자료구조(FIFO)
    - LifoQueue(): 나중에 입력된 데이터가 먼저 출력되는 구조 (스택 구조와 비슷)
    - PriorityQueue(): 데이터마다 우선순위를 넣어서, 우선순위가 높은 순으로 데이터 출력

### 3.1 Queue()로 큐 만들어보기
```python
    import queue
    
    data_queue = queue.Queue() #큐 초기화
    data_queue.put('stringdata') #enqueue를 put으로 사용
    data_queue.put(1) #enqueue 숫자를 enqueue
    data_queue.qsize() #queue의 크기 => 2
    data_queue.get() #처음 집어넣은 데이터를 꺼냄 dequeue => 'stringdata'
    data_queue.qsize() #queue의 크기 => 1
    data_queue.get() # => 1
```

### 3.2. LifoQueue()로 큐 만들기 (LIFO(Last-In, First-Out))
```python
    import queue
    data_queue = queue.LifoQueue()
    data_queue.put('stringdata') #enqueue를 put으로 사용
    data_queue.put(1) #enqueue 숫자를 enqueue
    data_queue.qsize() #queue의 크기 => 2
    data_queue.get() #마지막에 집어넣은 데이터를 꺼냄 dequeue => 1

```

### 3.3. PriorityQueue()로 큐 만들기
```python
    import queue
    data_queue = queue.PriorityQueue()
    data_queue.put((10, "first data")) # 튜플 형태의 데이터를 집어넣음 (우선순위, 데이터)
    data_queue.put((5, "second data"))
    data_queue.put((15, "third data"))
    data_queue.qsize() #queue의 크기 => 3
    data_queue.get() #우선순위가 가장 높은(숫자가 낮은) 데이터 꺼냄 dequeue => (5, "second data")
    data_queue.get() #그 다음 우선순위가 가장 높은(숫자가 낮은) 데이터 꺼냄 dequeue => (10, "first data")
```

### 참고: 어디에 큐가 많이 쓰일까?
- 멀티 태스킹을 위한 프로세스 스케쥴링 방식을 구현하기 위해 많이 사용됨 (운영체제 참조)

> 큐의 경우에는 장단점 보다는 (특별히 언급되는 장단점이 없음), 큐의 활용 예로 프로세스 스케쥴링 방식을 함께 이해해두는 것이 좋음

## 4. 리스트로 큐를 다루는 enqueue, dequeue 기능 구현하기

```python
    queue_list = list()

    def enqueue(data):
        queue_list.append(data)
        
    def dequeue():
        data = queue_list[0]
        del queue_list[0]
        return data

    for i in range(10):
        enqueue(i)
    
    len(queue_list) # => 10

    dequeue() # => 0
```

  