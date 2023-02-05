## Java Queue Interface

* The **Queue interface** of the Java collections framework provides the functionality of the queue data structure. It extends the **Collection** interface.

#### Classes that Implement Queue

* Since the **Queue is an interface**, we cannot provide the direct implementation of it.

* In order to use the functionalities of Queue, we need to use classes that implement it:
   *  **ArrayDeque**
   *  **LinkedList**
   *  **PriorityQueue**

![image](https://user-images.githubusercontent.com/40323661/216822318-1a2eab6f-7d5c-4c74-9cbf-a2044024a589.png)

#### Interfaces that extend Queue

* The **Queue** interface is also extended by various subinterfaces:

    * **Deque**
    * **BlockingQueue**
    * **BlockingDeque**

![image](https://user-images.githubusercontent.com/40323661/216822521-a0bee6f5-b91b-4051-af76-5b1e84843702.png)

#### Working of Queue Data Structure

* In queues, elements are stored and accessed in First In, First Out manner. That is, elements are added from the behind and removed from the front.
