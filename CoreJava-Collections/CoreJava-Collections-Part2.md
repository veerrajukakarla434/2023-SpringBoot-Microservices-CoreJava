
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

* **Queue is an interface so we cannot instantiate it**, rather we create instance of LinkedList or PriorityQueue and assign it to the Queue like this:

```java
Queue q1 = new LinkedList();
Queue q2 = new PriorityQueue();
```

#### Queue Operations
#### Add Element to Queue

* The Java Queue interface contains **two methods** you can use to add elements to a Queue. These methods are the **add()** method and the **offer()** method. 
* These two methods add an element to the end of the Queue. 
* The **add() and offer() methods differ in how the behave if the Queue is full**, so no more elements can be added. **The add() method throws an exception in that case**, whereas the **offer() method just returns false**. Here are two examples of adding elements to a Java Queue via its add() and offer() methods:

```java
Queue<String> queue = new LinkedList<>();

queue.add("element 1");
queue.offer("element 2");

```
#### Take Element From Queue

* To take an element from a Java Queue you can call either its **poll() or remove()** method. 
* The **poll() and remove() both removes the first element in the Queue**. They **differ in how they behave if the Queue is empty**. 
* The **poll() method returns null if the Queue is empty**. **The remove() method throws an exception if the Queue is empty**. Here are two examples of taking an element from a Java Queue using its poll() and remove() methods:

```java
Queue<String> queue = new LinkedList<>();
queue.add("element 1");
queue.add("element 2");
String element1 = queue.poll();
String element2 = queue.remove();
```

#### Methods Descriptions of Queue interface
* boolean add(E e): This method adds the specified element at the end of Queue. Returns true if the the element is added successfully or false if the element is not added that basically happens when the Queue is at its max capacity and cannot take any more elements.

* **E element():** This method returns the head (the first element) of the Queue.

* boolean **offer(object)**: This is same as **add()** method.

* **E remove():** This method removes the head(first element) of the Queue and returns its value.

* **E poll():** This method is almost same as remove() method. The only difference between poll() and remove() is that poll() method returns null if the Queue is empty.

* **E peek():** This method is almost same as element() method. The only difference between peek() and element() is that peek() method returns null if the Queue is empty.

#### Java Queue Example
```java
import java.util.*;
public class QueueExample1 {
	 
   public static void main(String[] args) {
	  
      /*
       * We cannot create instance of a Queue as it is an
       * interface, we can create instance of LinkedList or
       * PriorityQueue and assign it to Queue
       */
      Queue<String> q = new LinkedList<String>();
	    
      //Adding elements to the Queue
      q.add("Rick");
      q.add("Maggie"); 
      q.add("Glenn");
      q.add("Negan");
      q.add("Daryl");
	    
      System.out.println("Elements in Queue:"+q);

      /*
       * We can remove element from Queue using remove() method,
       * this would remove the first element from the Queue 
       */
      System.out.println("Removed element: "+q.remove());
	    
      /*
       * element() method - this returns the head of the
       * Queue. Head is the first element of Queue
       */
      System.out.println("Head: "+q.element());
	    
      /*
       * poll() method - this removes and returns the 
       * head of the Queue. Returns null if the Queue is empty
       */
      System.out.println("poll(): "+q.poll());
	    
      /*
       * peek() method - it works same as element() method,
       * however it returns null if the Queue is empty
       */
      System.out.println("peek(): "+q.peek());
	    
      //Again displaying the elements of Queue
      System.out.println("Elements in Queue:"+q);
   }
}
```
* OUTPUT:

```java
Elements in Queue:[Rick, Maggie, Glenn, Negan, Daryl]
Removed element: Rick
Head: Maggie
poll(): Maggie
peek(): Glenn
Elements in Queue:[Glenn, Negan, Daryl]
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

#### Working of Deque

* In a regular queue, elements are added from the rear and removed from the front. However, in a deque, we can **insert and remove elements from both front and rear**.

![image](https://user-images.githubusercontent.com/40323661/216825272-8a100fe2-7a7b-43a8-b3d7-8c9580bc7ce4.png)


#### Methods of Deque

* Since **Deque extends the Queue interface**, it inherits all the methods of the Queue interface.
* Besides methods available in the Queue interface, the **Deque interface also includes the following methods**:

#### Method Descriptions of Deque

* **addFirst()** - Adds the specified element at the beginning of the deque. Throws an exception if the deque is full.
* **addLast()** - Adds the specified element at the end of the deque. Throws an exception if the deque is full.
* **offerFirst()** - Adds the specified element at the beginning of the deque. Returns false if the deque is full.
* **offerLast()** - Adds the specified element at the end of the deque. Returns false if the deque is full.
* **getFirst()** - Returns the first element of the deque. Throws an exception if the deque is empty.
* **getLast()** - Returns the last element of the deque. Throws an exception if the deque is empty.
* **peekFirst()** - Returns the first element of the deque. Returns null if the deque is empty.
* **peekLast()** - Returns the last element of the deque. Returns null if the deque is empty.
* **removeFirst()** - Returns and removes the first element of the deque. Throws an exception if the deque is empty.
* **removeLast()** - Returns and removes the last element of the deque. Throws an exception if the deque is empty.
* **pollFirst()** - Returns and removes the first element of the deque. Returns null if the deque is empty.
* **pollLast()** - Returns and removes the last element of the deque. Returns null if the deque is empty.


