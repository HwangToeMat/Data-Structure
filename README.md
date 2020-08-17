# Data-Structure

# [자료구조] 01. 큐 (Queue) - python

## 1. 정의

줄을 서는 거와 같이 가장 먼저 넣은 데이터를 가장 먼저 꺼낼 수 있는 구조이다.<br>
즉 **FIFO(First in First out), LILO(Last in Last out)**구조를 가지고있다.<br>
* Enqueue : 큐에 데이터를 넣는 기능 후단(rear)에서 이루어짐<br>
* Dequeue : 큐에서 데이터를 꺼내는 기능 전단(front)에서 이루어짐

## 2. 특징

* 멀티 태스킹을 위한 프로세스 스케쥴링 방식을 구현하기 위해 많이 사용됨<br>
* 데이터가 입력된 시간 순서대로 처리할때 유리하다

## 3. 종류

1.Queue(FIFO)<br>
* FIFO(First in First out), LILO(Last in Last out)구조의 일반적인 큐<br>

2.Priority Queue<br>
* index값을 데이터마다 지정하여 순서를 정하는 형태<br>

3.Circular Queue<br>
* 직선 큐에서 데이터를 제거 할때 추가적인 연산이 생기는 단점을 극복하기 위한 원 형태의 큐<br>

4.Linked Queue<br>
* 링크드 리스트와 비슷 한 형태로 노드에 후단(rear)방향의 주소값이 있고 전단(front)에서 Dequeue, 후단(rear)에서 Enqueue가 일어난다.<br>

## 4. 코드 구현

### 간단하게 라이브러리로 구현하기

* Queue


```python
import queue

queue_code = queue.Queue()
# Enqueue
queue_code.put("data_1")
queue_code.put("data_2")
queue_code.put("data_3")
queue_code.put("data_4")
queue_code.put("data_5")
queue_code.qsize()
```




    5




```python
# Dequeue
for _ in range(queue_code.qsize()):
    print(queue_code.get())
```

    data_1
    data_2
    data_3
    data_4
    data_5
    

* PriorityQueue


```python
# PriorityQueue
priority_queue = queue.PriorityQueue()
# Enqueue
priority_queue.put((5, "data_1"))
priority_queue.put((3, "data_2"))
priority_queue.put((11, "data_3"))
priority_queue.put((8, "data_4"))
priority_queue.put((1, "data_5"))
priority_queue.qsize()
```




    5




```python
# Dequeue
for _ in range(priority_queue.qsize()):
    print(priority_queue.get())
```

    (1, 'data_5')
    (3, 'data_2')
    (5, 'data_1')
    (8, 'data_4')
    (11, 'data_3')
    

### 라이브러리 안쓰고 구현하기(list 사용하여)

* queue_htm class 구현


```python
class queue_htm:
    def __init__(self):
        self.queue = list()
    
    def Enqueue(self, data):
        self.queue.append(data)
        return self.queue
    
    def Dequeue(self):
        try:
            temp = self.queue[0]
            del self.queue[0]
            return temp
        except:
            return self.queue
    
    def qsize(self):
        return len(self.queue)
```

* test


```python
HTM = queue_htm()
# Enqueue
HTM.Enqueue(1)
HTM.Enqueue(2)
HTM.Enqueue(3)
HTM.Enqueue(4)
HTM.Enqueue(5)
```




    [1, 2, 3, 4, 5]




```python
# qsize
print('==>> qsize : ',HTM.qsize())
# Dequeue
for _ in range(HTM.qsize()):
    print('==>> Dequeue : ',HTM.Dequeue())
    print('==>> qsize : ',HTM.qsize())
```

    ==>> qsize :  5
    ==>> Dequeue :  1
    ==>> qsize :  4
    ==>> Dequeue :  2
    ==>> qsize :  3
    ==>> Dequeue :  3
    ==>> qsize :  2
    ==>> Dequeue :  4
    ==>> qsize :  1
    ==>> Dequeue :  5
    ==>> qsize :  0
    

# [자료구조] 02. 스택 (Stack) - python

## 1. 정의

가장 나중에 쌓은 데이터를 가장 먼저 꺼낼 수 있는 구조를 가지고 있다.<br>
즉 **LIFO(Last in First out), FILO(First in Last out)**구조를 가지고있다.<br>
* push : 데이터를 스택에 넣는다.<br>
* pop : 데이터를 스택에서 꺼낸다.

## 2. 특징

* 컴퓨터 내부의 프로세스 구조의 함수 동작 방식에 쓰임.<br>
* 데이터를 제한적으로 접근할 수 있는 구조이다.(한쪽 끝에서만 자료를 넣거나 뺄 수 있다.)
* 단순하고 빠른 성능을 위해 사용됨.

**장점**
  - 구조가 단순해서, 구현이 쉽다.
  - 데이터 저장/읽기 속도가 빠르다.<br>
  
**단점** 
  - 데이터 최대 갯수를 미리 정해야 한다.
  - 저장 공간의 낭비가 발생할 수 있다.

## 3. 코드 구현

### list 사용하여 구현하기

* stack_htm class 구현


```python
class stack_htm:
    def __init__(self):
        self.stack = list()
    
    def push(self, data):
        self.stack.append(data)
        return self.stack
    
    def pop(self):
        try:
            temp = self.stack[-1]
            del self.stack[-1]
            return temp
        except:
            return self.stack
    
    def ssize(self):
        return len(self.stack)
```

* test


```python
HTM = stack_htm()
# push
HTM.push(1)
HTM.push(2)
HTM.push(3)
HTM.push(4)
HTM.push(5)
```




    [1, 2, 3, 4, 5]




```python
# ssize
print('==>> qsize : ',HTM.ssize())
# pop
for _ in range(HTM.ssize()):
    print('==>> Dequeue : ',HTM.pop())
    print('==>> qsize : ',HTM.ssize())
```

    ==>> qsize :  5
    ==>> Dequeue :  5
    ==>> qsize :  4
    ==>> Dequeue :  4
    ==>> qsize :  3
    ==>> Dequeue :  3
    ==>> qsize :  2
    ==>> Dequeue :  2
    ==>> qsize :  1
    ==>> Dequeue :  1
    ==>> qsize :  0
    

# [자료구조] 03. 연결 리스트 (Linked List) - python

## 1. 정의

연결 리스트는 각각 존재하는 데이터(Node)에 다른 데이터(Node)를 화살표를 연결(pointer)하여 관리하는 구조이다.<br>
* 노드(Node): 데이터 저장 단위 (데이터값, 포인터) 로 구성<br>
* 포인터(pointer): 각 노드 안에서, 다음이나 이전의 노드와의 연결 정보를 가지고 있는 공간

## 2. 특징

**장점**<br>
* 미리 데이터 공간을 할당하지 않아도 됨.<br>

**단점**<br>
* 데이터 저장 공간 외에도 연결을 위한 주소값 저장 공간이 추가적으로 필요함<br>
* 연결 정보를 찾는 시간이 추가적으로 필요하기때문에 접근 속도가 느림<br>
* 중간 데이터 추가 혹은 삭제시, 앞뒤 데이터의 연결을 재구성해야 함.

## 3. 종류

1.연결 리스트(Linked List)<br>
* 데이터(Node)에 다른 데이터(Node)를 화살표를 연결(pointer)하여 관리하는 구조를 가진 일반적인 형태<br>

2.이중 연결 리스트(Doubly Linked List)<br>
* 양방향으로 연결되어 있어 노드 탐색이 양쪽으로 모두 가능함<br>

3.원형 연결 리스트(Circular Linked List)<br>
* 일반적인 연결 리스트의 첫번째 노드와 마지막 노드를 연결시켜 원형으로 만든 구조<br>

4.이중 원형 연결 리스트(Doubly Circular Linked List)<br>
* 이중 연결 리스트의 첫번째 노드와 마지막 노드를 연결시켜 원형으로 만든 구조

## 4. 코드 구현

* 연결 리스트(Linked List)

<img src="https://www.fun-coding.org/00_Images/linkedlistadd.png" />


```python
class Node:
    def __init__(self, data, post=None):
        self.post = post # 다음 node의 주소값
        self.data = data # node의 data
        
class Linked_list:
    def __init__(self, data):
        self.head = Node(data)
        
    def add(self, data):
        node = self.head
        while node.post:
            node = node.post
        node.post = Node(data)
    
    def pop(self):
        node = self.head
        while node.post.post:
            node = node.post
        node.post = None
    
    def desc(self):
        node = self.head
        while node:
            print(node.data)
            node = node.post
            
    # 앞에서부터 검색하기
    def search(self, data):
        node = self.head
        while node.data != data:
            if node.post == None:           
                return print('찾는 값이 없습니다.')
            node = node.post
        print(node.data, '을 찾았습니다.')
```

* test


```python
htm = Linked_list('data1')
htm.desc()
```

    data1
    


```python
htm.add('data2')
htm.add('data3')
htm.add('data4')
htm.add('data5')
htm.desc()
```

    data1
    data2
    data3
    data4
    data5
    


```python
htm.pop()
htm.desc()
```

    data1
    data2
    data3
    data4
    


```python
htm.search('data1')
htm.search('data15')
```

    data1 을 찾았습니다.
    찾는 값이 없습니다.
    

* 이중 연결 리스트(Doubly Linked List)

<img src="https://www.fun-coding.org/00_Images/doublelinkedlist.png" />


```python
class Node:
    def __init__(self, data, prev=None, post=None):
        self.prev = prev
        self.data = data
        self.post = post

class DLinked_list:
    def __init__(self, data):
        self.head = Node(data)
        self.tail = self.head

    def add(self, data):
        node = self.tail
        node.post = Node(data, node, None)
        self.tail = node.post
    
    # 이중 연결 리스트를 활용하여 알고리즘 단축시키기
    def pop(self):
        node = self.tail
        node = node.prev
        node.post = None
        self.tail = node

    def desc(self):
        node = self.head
        while node:
            print (node.data)
            node = node.post
            
    # 앞에서부터 검색하기
    def search(self, data):
        node = self.head
        while node.data != data:
            if node.post == None:           
                return print('찾는 값이 없습니다.')
            node = node.post
        print(node.data, '을 찾았습니다.')
        
    # 이중 연결 리스트를 활용하여 뒤에서부터 검색하기
    def search_tail(self, data):
        node = self.tail
        while node.data != data:
            if node.prev == None:
                return print('찾는 값이 없습니다.')
            node = node.prev
        print(node.data, '을 찾았습니다.')
```

* test


```python
htm1 = DLinked_list('data1')
htm1.desc()
```

    data1
    


```python
htm1.add('data2')
htm1.add('data3')
htm1.add('data4')
htm1.add('data5')
htm1.desc()
```

    data1
    data2
    data3
    data4
    data5
    


```python
htm1.pop()
htm1.desc()
```

    data1
    data2
    data3
    data4
    


```python
htm1.search_tail('data1')
htm1.search_tail('data15')
```

    data1 을 찾았습니다.
    찾는 값이 없습니다.
    

# [자료구조] 04. Big O 표기법 (Big 0 notation) - python

<img src="https://t1.daumcdn.net/cfile/tistory/99EF1E395C7EB4B601" />

## 1. 정의

 알고리즘의 시간 복잡도(알고리즘 실행 속도)를 표기할때 쓰이며 알고리즘의 최악의 실행 시간을 표기한다. 즉 알고리즘 효율성을 **상한선 기준**으로 표기하기 때문에 가장 일반적으로 사용된다.<br>

## 2. 특징

Big O 표기법은 알고리즘에서 영향력 있는 항 이외에는 무시하고 **가장 영향력이 있는 항**을 표기한다. 예를 들어 O(8$n^2$ + 5n + 4)라고 하면 O($n^2$)으로 표기한다.<br>
그 외에도 **O(1), O($log n$), O(n), O(n$log n$), O($n^2$), O($2^n$), O(n!)등**으로 표기함

## 3. 성능비교 및 사용예시

<img src="https://t1.daumcdn.net/cfile/tistory/99929C465B55DE3A34" />

일반적으로 그림과 같이 **O(1) < O($log n$) < O(n) < O(n$log n$) < O($n^2$) < O($n^3$) < O($2^n$)** 순으로 시간이 오래 걸린다. 즉, O(1)이 가장 성능이 좋다.

### 사용예시

두 알고리즘의 성능을 비교할때 O($log n$)과 O($n^2$)가 있다면 Big O 표기법에 의해 O($log n$)의 성능이 더 좋다고 볼 수 있다

