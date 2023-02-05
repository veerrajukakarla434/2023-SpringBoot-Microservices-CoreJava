
## Java Queue Interface

#### Java Collection Framework Hierarchy

![image](https://user-images.githubusercontent.com/40323661/215625747-b3ab3679-387d-4770-9f89-8d88e415ca8b.png)


* The **Queue interface** of the Java collections framework provides the functionality of the queue data structure. It extends the **Collection** interface.

#### Classes that Implement Queue

* Since the **Queue is an interface**, we cannot provide the direct implementation of it.

* In order to use the functionalities of Queue, we need to use classes that implement it:
   *  **ArrayDeque**
   *  **LinkedList**
   *  **PriorityQueue**

![image](https://user-images.githubusercontent.com/40323661/216822318-1a2eab6f-7d5c-4c74-9cbf-a2044024a589.png)

```java
// LinkedList implementation of Queue
Queue<String> animal1 = new LinkedList<>();

// Array implementation of Queue
Queue<String> animal2 = new ArrayDeque<>();

// Priority Queue implementation of Queue
Queue<String> animal 3 = new PriorityQueue<>();

```


#### Interfaces that extend Queue

* The **Queue** interface is also extended by various subinterfaces:

    * **Deque**
    * **BlockingQueue**
    * **BlockingDeque**

![image](https://user-images.githubusercontent.com/40323661/216822521-a0bee6f5-b91b-4051-af76-5b1e84843702.png)

#### Working of Queue Data Structure

* In queues, elements are stored and accessed in **First In, First Out** manner. That is, elements are **added from the behind** and **removed from the front**.
* **OR**
* The Java Queue interface, java.util.Queue represents a data structure designed to have elements **inserted at the end of the queue**, and **elements removed from the beginning of the queue**. This is similar to how a queue in a supermarket works.

![image](https://user-images.githubusercontent.com/40323661/216822962-94ef6318-6dd5-4cf5-8f2e-d459bf027bd9.png)

#### Classes that implement Deque

* In order to use the functionalities of the Deque interface, we need to use classes that implement it:
   * **ArrayDeque**
   * **LinkedList**
![image](https://user-images.githubusercontent.com/40323661/216823891-a7135710-6f8b-4a16-bdaf-fbd5e165b566.png)

```java
// Array implementation of Deque
Deque<String> animal1 = new ArrayDeque<>();

// LinkedList implementation of Deque
Deque<String> animal2 = new LinkedList<>();
```

#### Methods of Deque

* Since **Deque extends the Queue interface**, it inherits all the methods of the Queue interface.
* Besides methods available in the Queue interface, the **Deque interface also includes the following methods**:

* **Add Element to Deque**
    * add()
    * addLast()
    * addFirst()
    * offer()
    * offerLast()
    * offerFirst()
    * push()
* **Peek at Element in Deque**
    * peek()
    * peekFirst()
    * peekLast()
    * getFirst()
    * getLast()
* **Remove Element From Deque**
    * remove()
    * removeFirst()
    * removeLast()
    * poll()
    * pollFirst()
    * pollLast()
    * pop()


