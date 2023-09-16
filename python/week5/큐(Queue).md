# 큐(Queue)

## INDEX

> **INDEX**
> 
> - 선형 큐
> - 원형 큐
> - 우선순위 큐
> - 큐의 활용 : 버퍼
> - BFS
> - BFS 예제

## 큐

> **큐(Queue)의 특성**
> 
> - 스택과 마찬가지로 삽입과 삭제의 위치가 제한적인 자료구조
>     - 큐의 뒤에서는 삽입만 하고, 큐의 앞에서는 삭제만 이루어지는 구조
> - 선입선출구조(FIFO : First In First Out)
>     - 큐에 삽입한 순서대로 원소가 저장되어, 가장 먼저 삽입(First In)된 원소는 가장 먼저 삭제(First Out)된다.

> **큐의 구조 및 기본 연산**
> 
> - 큐의 선입선출 구조
>     
>     ![Untitled](%E1%84%8F%E1%85%B2(Queue)%2073c94fc8f5cd416bbb9e68903489cf6f/Untitled.png)
>     
> - 큐의 기본 연산
>     - 삽입 : enQueue
>     - 삭제 : deQueue

> **큐의 주요 연산**
> 
> - 큐의 사용을 위해 필요한 주요 연산은 다음과 같음
>     
>     
>     | 연산 | 기능 |
>     | --- | --- |
>     | enQueue(item) | 큐의 뒤쪽(rear 다음)에 원소를 삽입하는 연산 |
>     | deQueue() | 큐의 앞쪽(front)에서 원소를 삭제하고 반환하는 연산 |
>     | createQueue() | 공백 상태의 큐를 생성하는 연산 |
>     | isEmpty() | 큐가 공백상태인지를 확인하는 연산 |
>     | isFull() | 큐가 포화상태인지를 확인하는 연산 |
>     | Qpeek() | 큐의 앞쪽(front)에서 원소를 삭제없이 반환하는 연산 |

> **큐의 연산 과정**
> 
> 1. 공백 큐 생성 : createQueue();
>     
>     ![Untitled](%E1%84%8F%E1%85%B2(Queue)%2073c94fc8f5cd416bbb9e68903489cf6f/Untitled%201.png)
>     
> 2. 원소 A 삽입 : enQueue(A);
>     
>     ![Untitled](%E1%84%8F%E1%85%B2(Queue)%2073c94fc8f5cd416bbb9e68903489cf6f/Untitled%202.png)
>     
> 3. 원소 B 삽입 : enQueue(B);
>     
>     ![Untitled](%E1%84%8F%E1%85%B2(Queue)%2073c94fc8f5cd416bbb9e68903489cf6f/Untitled%203.png)
>     
> 4. 원소 반환/삭제 : deQueue();
>     
>     ![Untitled](%E1%84%8F%E1%85%B2(Queue)%2073c94fc8f5cd416bbb9e68903489cf6f/Untitled%204.png)
>     
> 5. 원소 C 삽입 : enQueue(C);
>     
>     ![Untitled](%E1%84%8F%E1%85%B2(Queue)%2073c94fc8f5cd416bbb9e68903489cf6f/Untitled%205.png)
>     
> 6. 원소 반환/삭제 : deQueue();
>     
>     ![Untitled](%E1%84%8F%E1%85%B2(Queue)%2073c94fc8f5cd416bbb9e68903489cf6f/Untitled%206.png)
>     
> 7. 원소 반환/삭제 : deQueue();
>     
>     ![Untitled](%E1%84%8F%E1%85%B2(Queue)%2073c94fc8f5cd416bbb9e68903489cf6f/Untitled%207.png)
>     

---

## 선형 큐

> **선형 큐**
> 
> - 1차원 배열을 이용한 큐
>     - 큐의 크기 = 배열의 크기
>     - front : 저장된 첫 번째 원소의 인덱스
>     - rear : 저장된 마지막 원소의 인덱스
> - 상태 표현
>     - 초기 상태 : front = rear = -1
>     - 공백 상태 : front == rear
>     - 포화 상태 : rear == n-1 (n : 배열의 크기, n-1: 배열의 마지막 인덱스)

> **초기 공백 큐 생성**
> 
> - 크기가 n인 1차원 배열 생성
> - front와 rear를 -1로 초기화

> **삽입 : enQueue(item)**
> 
> - 마지막 원소 뒤에 새로운 원소를 삽입하기 위해
>     1. rear 값을 하나 증가 시켜 새로운 원소를 삽입할 자리를 마련
>     2. 그 인덱스에 해당하는 배열 원소 Q[rear]에 item을 저장
>     
>     ```python
>     def enQueue(item):
>         global rear
>         if len(Q)-1 == rear:
>             print('Queue_FULL')
>         else:
>             rear += 1
>             Q[rear] = item
>     
>     Q = [0 for i in range(3)]
>     front = rear = -1
>     for i in range(1, 5):
>         enQueue(i)
>         print(Q[front+1:rear+1])
>     
>     '''
>     [1]
>     [1, 2]
>     [1, 2, 3]
>     Queue_FULL
>     [1, 2, 3]
>     '''
>     ```
>     

> **삭제 : deQueue()**
> 
> - 가장 앞에 있는 원소를 삭제하기 위해
>     1. front 값을 하나 증가시켜 큐에 남아있게 될 첫 번째 원소 이동
>     2. 새로운 첫 번째 원소를 리턴 함으로써 삭제와 동일한 기능을 함
>         
>         ```python
>         def enQueue(item):
>             global rear
>             if len(Q)-1 == rear:
>                 print('Queue_FULL')
>             else:
>                 rear += 1
>                 Q[rear] = item
>         
>         def deQueue():
>             global front
>             if front == rear:
>                 print('Queue_Empty')
>             else:
>                 front += 1
>                 return Q[front]
>         
>         Q = [0 for i in range(3)]
>         front = -1
>         rear = -1
>         
>         for i in range(1, 5):
>             enQueue(i)
>             print(Q[front+1:rear+1])
>         
>         for i in range(4):
>             print(deQueue())
>         ```
>         

> **공백 상태 및 포화 상태 검사 : isEmpty(), isFull()**
> 
> - 공백 상태 : front == rear
> - 포화 상태 : rear == n-1 (n : 배열의 크기, n-1 : 배열의 마지막 인덱스)
>     
>     ```python
>     def isEmpty():
>         global front
>         global rear
>         return front == rear
>     
>     def isFull():
>         global rear
>         return rear == len(Q) - 1
>     
>     def enQueue(item):
>         global rear
>         if isFull():
>             print('Queue_FULL')
>         else:
>             rear += 1
>             Q[rear] = item
>     
>     def deQueue():
>         global front
>         if isEmpty():
>             print('Queue_Empty')
>         else:
>             front += 1
>             return Q[front]
>     
>     Q = [0 for i in range(3)]
>     front = -1
>     rear = -1
>     
>     for i in range(1, 5):
>         enQueue(i)
>         print(Q[front+1:rear+1])
>     
>     for i in range(4):
>         print(deQueue())
>     ```
>     

> **검색 : Qpeek()**
> 
> - 가장 앞에 있는 원소를 검색하여 반환하는 연산
> - 현재 front의 한자리 뒤(front+1)에 있는 원소, 즉 큐의 첫 번째에 있는 원소를 반환
>     
>     ```python
>     def isEmpty():
>         global front
>         global rear
>         return front == rear
>     
>     def isFull():
>         global rear
>         return rear == len(Q) - 1
>     
>     def enQueue(item):
>         global rear
>         if isFull():
>             print('Queue_FULL')
>         else:
>             rear += 1
>             Q[rear] = item
>     
>     def deQueue():
>         global front
>         if isEmpty():
>             print('Queue_Empty')
>         else:
>             front += 1
>             return Q[front]
>     
>     def Qpeek():
>         if isEmpty():
>             print('Queue_Empty')
>         else:
>             return Q[front+1]
>     
>     Q = [0 for i in range(3)]
>     front = -1
>     rear = -1
>     
>     for i in range(1, 5):
>         enQueue(i)
>         print(Q[front+1:rear+1])
>     
>     for i in range(4):
>         print(Qpeek())
>         print(deQueue())
>     ```
>     

---

### <연습 문제 1>

> **<연습 문제 1>**
> 
> - 큐를 구현하여 다음 동작을 확인해 봅시다.
>     - 세 개의 데이터 1, 2, 3을 차례로 큐에 삽입하고
>     - 큐에서 세 개의 데이터를 차례로 꺼내서 출력한다.
>         - 1, 2, 3이 출력 되어야 함.
>     
>     ```python
>     def is_empty():
>         return front == rear
>     
>     def is_full():
>         return rear == len(Q) - 1
>     
>     def enqueue(item):
>         global rear
>         if is_full():
>             print('Queue_Full')
>         else:
>             rear += 1
>             Q[rear] = item
>     
>     def dequeue():
>         global front
>         if is_empty():
>             print('Queue_Empty')
>         else:
>             front += 1
>             return Q[front]
>     
>     Q = [-1 for i in range(3)]
>     front = -1
>     rear = -1
>     enqueue(1)
>     enqueue(2)
>     enqueue(3)
>     print(dequeue())
>     print(dequeue())
>     print(dequeue())
>     ```
>     

---

## 원형 큐

> **선형 큐 이용 시 문제점**
> 
> - 잘못된 포화상태 인식
>     - 선형 큐를 이용하여 원소의 삽입과 삭제를 계속할 경우, 배열의 앞 부분에 활용할 수 있는 공간이 있음에도 불구하고, rear = n -1 인 상태 즉, 포화 상태로 인식하여 더 이상의 삽입을 수행하지 않게 됨
>         
>         ![Untitled](%E1%84%8F%E1%85%B2(Queue)%2073c94fc8f5cd416bbb9e68903489cf6f/Untitled%208.png)
>         
> - 해결 방법 1
>     - 매 연산이 이루어질 때마다 저장된 원소들을 배열의 앞 부분으로 모두 이동 시킴
>     - 원소 이동에 많은 시간이 소요되어 큐의 효율성이 급격히 떨어짐
>         
>         ![Untitled](%E1%84%8F%E1%85%B2(Queue)%2073c94fc8f5cd416bbb9e68903489cf6f/Untitled%209.png)
>         
> - 해결 방법 2
>     - 1차원 배열을 사용하되, 논리적으로는 배열의 처음과 끝이 연결되어 원형 형태의 큐를 이룬다고 가정하고 사용
>     - 원형 큐의 논리적 구조

> **원형 큐의 구조**
> 
> - 초기 공백 상태
>     - front = rear = 0
> - Index의 순환
>     - front와 rear의 위치가 배열의 마지막 인덱스인 n-1를 가리킨 후, 그 다음에는 논리적 순환을 이루어 배열의 처음 인덱스 0으로 이동해야 함
>     - 이를 위해 나머지 연산자 mod를 사용함.
> 
> - front 변수
>     - 공백 상태와 포화 상태 구분을 쉽게 하기 위해 front가 있는 자리는 사용하지 않고 항상 빈 자리로 둠
> - 삽입 위치 및 삭제 위치
>     
>     
>     |  | 삽입 위치 | 삭제 위치 |
>     | --- | --- | --- |
>     | 선형 큐 | rear = rear + 1 | front = front +1 |
>     | 원형 큐 | rear = (rear + 1) mod n | front = (front + 1) mod n |

> **원형 큐의 연산 과정**
> 
> 1. create Queue
>     
>     ![Untitled](%E1%84%8F%E1%85%B2(Queue)%2073c94fc8f5cd416bbb9e68903489cf6f/Untitled%2010.png)
>     
> 2. enQueue(A);
>     
>     ![Untitled](%E1%84%8F%E1%85%B2(Queue)%2073c94fc8f5cd416bbb9e68903489cf6f/Untitled%2011.png)
>     
> 3. enQueue(B);
>     
>     ![Untitled](%E1%84%8F%E1%85%B2(Queue)%2073c94fc8f5cd416bbb9e68903489cf6f/Untitled%2012.png)
>     
> 4. deQueue();
>     
>     ![Untitled](%E1%84%8F%E1%85%B2(Queue)%2073c94fc8f5cd416bbb9e68903489cf6f/Untitled%2013.png)
>     
> 5. enQueue(C);
>     
>     ![Untitled](%E1%84%8F%E1%85%B2(Queue)%2073c94fc8f5cd416bbb9e68903489cf6f/Untitled%2014.png)
>     
> 6. enQueue(D);
>     
>     ![Untitled](%E1%84%8F%E1%85%B2(Queue)%2073c94fc8f5cd416bbb9e68903489cf6f/Untitled%2015.png)
>     

> **원형 큐의 구현**
> 
> - 초기 공백 큐 생성
>     - 크기 n인 1차원 배열 생성
>     - front와 rear를 0으로 초기화
>         
>         ```python
>         cQ = [-1 for i in range(4)]
>         front = 0
>         rear = 0
>         ```
>         
> 
> - 공백 상태 및 포화 상태 검사 : isEmpty(), isFull()
>     - 공백 상태 : front == rear
>     - 포화 상태 : 삽입할 rear의 다음 위치 == 현재 front
>         - (rear + 1) mod n == front
>     
>     ```python
>     def is_empty():
>         return front == rear
>     
>     def is_full():
>         return (rear + 1) % len(cQ) == front
>     
>     cQ = [-1 for i in range(4)]
>     front = 0
>     rear = 0
>     
>     print(is_empty())
>     print(is_full())
>     ```
>     
> 
> - 삽입 : enQueue(item)
>     - 마지막 원소 뒤에 새로운 원소를 삽입하기 위해
>         1. rear 값을 조정하여 새로운 원소를 삽입할 자리를 마련함
>             - rear = (rear + 1) mod n
>         2. 그 인덱스에 해당하는 배열 원소 cQ[rear]에 item을 저장
>             
>             ```python
>             def is_empty():
>                 return front == rear
>             
>             def is_full():
>                 return (rear + 1) % len(cQ) == front
>             
>             def enqueue(item):
>                 global rear
>                 if is_full():
>                     print('Queue_Full')
>                 else:
>                     rear = (rear + 1) % len(cQ)
>                     cQ[rear] = item
>             
>             cQ = [None for i in range(4)]
>             front = 0
>             rear = 0
>             
>             for i in range(4):
>                 enqueue(i)
>                 print(cQ)
>             ```
>             
> 
> - 삭제 : deQueue(), delete()
>     - 가장 앞에 있는 원소를 삭제하기 위해
>         1. front 값을 조정하여 삭제할 자라를 준비함
>         2. 새로운 front 원소를 리턴 함으로써 삭제와 동일한 기능함
>             
>             ```python
>             def is_empty():
>                 return front == rear
>             
>             def is_full():
>                 return (rear + 1) % len(cQ) == front
>             
>             def enqueue(item):
>                 global rear
>                 if is_full():
>                     print('Queue_Full')
>                 else:
>                     rear = (rear + 1) % len(cQ)
>                     cQ[rear] = item
>             
>             def dequeue():
>                 global front
>                 if is_empty():
>                     print('Queue_Empty')
>                 else:
>                     front = (front + 1) % len(cQ)
>                     return cQ[front]
>             
>             cQ = [None for i in range(4)]
>             front = 0
>             rear = 0
>             
>             for i in range(4):
>                 enqueue(i)
>                 print(cQ)
>             
>             for j in range(4):
>                 print(dequeue())
>             ```
>             

---

## 우선순위 큐

> **우선순위 큐(Priority Queue)**
> 
> - 우선순위 큐의 특성
>     - 우선순위를 가진 항목들을 저장하는 큐
>     - FIFO 순서가 아니라 우선순위가 높은 순서대로 먼저 나가게 된다.
> - 우선순위 큐의 적용 분야
>     - 시뮬레이션 시스템
>     - 네트워크 트래픽 제어
>     - 운영체제의 테스크 스케줄링
> 
> - 우선순위 큐의 구현
>     - 배열을 이용한 우선순위 큐
>     - 리스트를 이용한 우선순위 큐
> - 우선순위 큐의 기본 연산
>     - 삽입 : enQueue
>     - 삭제 : deQueue
>     
>     ![Untitled](%E1%84%8F%E1%85%B2(Queue)%2073c94fc8f5cd416bbb9e68903489cf6f/Untitled%2016.png)
>     

> **배열을 이용한 우선순위 큐**
> 
> - 배열을 이용하여 우선순위 큐 구현
>     - 배열을 이용하여 자료 저장
>     - 원소를 삽입하는 과정에서 우선순위를 비교하여 적절한 위치에 삽입하는 구조
>     - 가장 앞에 최고 우선순위의 원소가 위치하게 됨
> - 문제점
>     - 배열을 사용하므로, 삽입이나 삭제 연산이 일어날 때 원소의 재배치가 발생함
>     - 이에 소요되는 시간이나 메모리 낭비가 큼

---

## 큐의 활용 : 버퍼(Buffer)

> **버퍼(Buffer)**
> 
> - 버퍼
>     - 데이터를 한 곳에서 다른 한 곳으로 전송하는 동안 일시적으로 그 데이터를 보관하는 메모리의 영역
>     - 버퍼링 : 버퍼를 활용하는 방식 또는 버퍼를 채우는 동작을 의미한다.
> - 버퍼의 자료 구조
>     - 버퍼는 일반적으로 입출력 및 네트워크와 관련된 기능에서 이용된다.
>     - 순서대로 입력/출력/전달되어야 하므로 FIFO 방식의 자료구조인 큐가 활용된다.

> **키보드 버퍼**
> 
> - 키보드 버퍼는 아래와 같이 수행된다.
>     
>     ![Untitled](%E1%84%8F%E1%85%B2(Queue)%2073c94fc8f5cd416bbb9e68903489cf6f/Untitled%2017.png)
>     

---

### <연습 문제 2>

> **<연습 문제 2>**
> 
> - Queue를 이용하여 마이쮸 나눠주기 시뮬레이션을 해 보자
>     
>     1번이 줄을 선다.
>     
>     1번이 한 개의 마이쮸를 받는다.
>     
>     1번이 다시 줄을 선다.
>     
>     새로 2번이 들어와 줄을 선다.
>     
>     1번이 두 개의 마이쮸를 받는다.
>     
>     1번이 다시 줄을 선다.
>     
>     새로 3번이 들어와 줄을 선다.
>     
>     2번이 한 개의 마이쮸를 받는다.
>     
>     2번이 다시 줄을 선다.
>     
>     새로 4번이 들어와 줄을 선다.
>     
>     …
>     
>     20개의 마이쮸가 있을 때 마지막 것을 누가 가져갈까?
>     
> 
> - 엔터를 칠 때 마다 다음 정보를 화면에 출력해 보자.
>     - 큐에 있는 사람 수
>     - 현재 일인당 나눠주는 사탕의 수
>     - 현재까지 나눠준 사탕의 수
>     
>     ```python
>     def is_empty():
>         return front == rear
>     
>     def is_full():
>         return (rear + 1) % len(cQ) == front
>     
>     def enqueue(item):
>         global rear
>         if is_full():
>             print('Queue_Full')
>         else:
>             rear = (rear + 1) % len(cQ)
>             cQ[rear] = item
>     
>     def dequeue():
>         global front
>         if is_empty():
>             print('Queue_Empty')
>         else:
>             front = (front + 1) % len(cQ)
>             return cQ[front]
>     
>     cQ = [None for i in range(20)]
>     front = 0
>     rear = 0
>     
>     enqueue([1, 1])
>     ct = 20
>     num = 2
>     ans = 0
>     while ct > 0:
>         garbage = input()
>         len_cQ = rear - front
>         if len_cQ < 0:
>             len_cQ += len(cQ)
>         print(len_cQ)
>         now_n = 0
>         if not is_empty():
>             info = dequeue()
>             ans = info[0]
>             now_n = min(info[1], ct)
>             ct -= now_n
>             info[1] += 1
>             enqueue(info)
>         enqueue([num, 1])
>         print(now_n)
>         print(20 - ct)
>         num += 1
>     print(ans)
>     ```
>     

---

## BFS

> **BFS(Breadth First Search)**
> 
> - 그래프를 탐색하는 방법에는 크게 두 가지가 있음
>     - 깊이 우선 탐색(Depth First Search, DFS)
>     - 너비 우선 탐색(Breadth First Search, BFS)
> - 너비 우선 탐색은 탐색 시작점의 인접한 정점들을 먼저 모두 차례로 방문한 후에, 방문했던 정점들을 시작점으로 하여 다시 인접한 정점들을 차례로 방문하는 방식
> - 인접한 정점들에 대해 탐색을 한 후, 차례로 다시 너비 우선 탐색을 진행해야 하므로, 선입 선출 형태의 자료구조인 큐를 활용함
> 
> - BFS는 예제 그래프를 아래와 같은 순서로 탐색함
>     
>     ![Untitled](%E1%84%8F%E1%85%B2(Queue)%2073c94fc8f5cd416bbb9e68903489cf6f/Untitled%2018.png)
>     

> **BFS 알고리즘**
> 
> - 입력 파라미터 : 그래프 G와 탐색 시작점 V
>     
>     ```python
>     def BFS(G, v):
>         visited = [False] * (len(G))
>         queue = []
>         queue.append(v)
>         while queue:
>             t = queue.pop(0)
>             if not visited[t]:
>                 visited[t] = True
>                 ans.append(chr(t+ord('A')))
>                 for i in G[t]:
>                     if not visited[i]:
>                         queue.append(i)
>     
>     graph = [[1, 2, 3], [4, 5], [], [6, 7, 8], [], [], [], [], []]
>     ans = []
>     s = 0
>     BFS(graph, s)
>     print(*ans)
>     
>     '''
>     A B C D E F G H I
>     '''
>     ```
>     

---

## BFS 예제

> **BFS 예제**
> 
> 1. 초기 상태
>     - visited 배열 초기화
>     - Q 생성
>     - 시작점 enqueue
> 2. A 점부터 시작
>     - dequeue : A
>     - A를 방문한 것으로 표시
>     - A의 인접 점 enqueue
> 3. 탐색 진행
>     - dequeue : B
>     - B를 방문한 것으로 표시
>     - B의 인접 점 enqueue
> 4. 탐색 진행
>     - dequeue : C
>     - C를 방문한 것으로 표시
> 5. 탐색 진행
>     - dequeue : D
>     - D를 방문한 것으로 표시
>     - D의 인접 점 enqueue
> 6. 탐색 진행
>     - dequeue : E
>     - E를 방문한 것으로 표시
> 7. 탐색 진행
>     - dequeue : F
>     - F를 방문한 것으로 표시
> 8. 탐색 진행
>     - dequeue : G
>     - G를 방문한 것으로 표시
> 9. 탐색 진행
>     - dequeue : H
>     - H를 방문한 것으로 표시
> 10. 탐색 진행
>     - dequeue : I
>     - I를 방문한 것으로 표시
> 11. Q가 비었으므로 탐색 종료

---

### <연습 문제 3>

> **<연습 문제 3>**
> 
> - 다음은 연결되어 있는 두 개의 정점 사이의 간선을 순서대로 나열 해 놓은 것이다.
> 모든 정점을 너비 우선 탐색하여 경로를 출력하시오. 시작 정점을 1로 시작 하시오.
>     - 입력 : 1 2 1 3 2 4 2 5 4 6 5 6 6 7 3 7
>     - 출력 : 1 2 3 4 5 7 6
>     
>     ```python
>     def BFS(G, s):
>         visited = [False for i in range(len(G))]
>         queue = []
>         queue.append(s)
>         while queue:
>             v = queue.pop(0)
>             ans.append(v)
>             visited[v] = True
>             for i in graph[v]:
>                 if not visited[i]:
>                     visited[i] = True
>                     queue.append(i)
>     
>     list1 = list(map(int, input().split()))
>     n = max(list1)
>     graph = [[]for i in range(n+1)]
>     for i in range(1, len(list1), 2):
>         v1 = list1[i-1]
>         v2 = list1[i]
>         graph[v1].append(v2)
>         graph[v2].append(v1)
>     s = 1
>     ans = []
>     BFS(graph, s)
>     print(*ans)
>     ```
>     

---