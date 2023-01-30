## Java - Multithreading

#### Java Threads

* Threads allows a program to operate more efficiently by doing multiple things at the same time.

#### Creating a Thread

* There are two ways to create a thread:
    * By extending Thread class
    * By implementing Runnable interface.

#### Thread class:
* Thread class provide constructors and methods to create and perform operations on a thread.Thread class extends Object class and implements Runnable interface.
   * Commonly used Constructors of Thread class:
      * Thread()
      * Thread(String name)
      * Thread(Runnable r)
      * Thread(Runnable r,String name)

#### It can be created by extending the Thread class and overriding its run() method: 

```java

public class Main extends Thread {
  public static void main(String[] args) {
    Main thread = new Main();
    thread.start();
    System.out.println("This code is outside of the thread");
  }
  public void run() {
    System.out.println("This code is running in a thread");
  }
}


Output: 
This code is outside of the thread
This code is running in a thread
```
####  Java Thread Example by implementing Runnable interface

```java
public class Main implements Runnable {
  public static void main(String[] args) {
    Main obj = new Main();
    Thread thread = new Thread(obj);
    thread.start();
    System.out.println("This code is outside of the thread");
  }
  public void run() {
    System.out.println("This code is running in a thread");
  }
}

Output: 
This code is outside of the thread
This code is running in a thread
```

#### Differences between "extending" and "implementing" Threads

* The major difference is that when a class extends the Thread class, you cannot extend any other class, but by implementing the Runnable interface, it is possible to extend from another class as well, like: class **MyClass extends OtherClass implements Runnable**.

#### Life Cycle of a Thread

* A thread goes through various stages in its life cycle. For example, a thread is born, started, runs, and then dies. The following diagram shows the complete life cycle of a thread.

![image](https://user-images.githubusercontent.com/40323661/215364308-83b2ddf6-4d98-4bfb-911a-1c15fe58e87f.png)

* Following are the stages of the life cycle −

* **New** − A new thread begins its life cycle in the new state. It remains in this state until the program starts the thread. It is also referred to as a **born thread.**

* **Runnable** − After a newly born thread is started, the thread becomes runnable. A thread in this state is considered to be executing its task.

* **Waiting** − Sometimes, a thread transitions to the waiting state while the thread waits for another thread to perform a task. A thread transitions back to the runnable state only when another thread signals the waiting thread to continue executing.

* **Timed Waiting** − A runnable thread can enter the timed waiting state for a specified interval of time. A thread in this state transitions back to the runnable state when that time interval expires or when the event it is waiting for occurs.

* **Terminated (Dead)** − A runnable thread enters the terminated state when it completes its task or otherwise terminates.

#### Multithreading in Java

* Multithreading in Java is a process of executing multiple threads simultaneously.

* Java Multithreading is mostly used in games, animation, etc.

#### Advantages of Java Multithreading
         * 1) It doesn't block the user because threads are independent and you can perform multiple operations at the same time.

         * 2) You can perform many operations together, so it saves time.

         * 3) Threads are independent, so it doesn't affect other threads if an exception occurs in a single thread.
#### Create a Thread by Implementing a Runnable Interface

* If your class is intended to be executed as a thread then you can achieve this by implementing a Runnable interface. You will need to follow three basic steps −

* **Step 1**
* As a first step, you need to implement a run() method provided by a Runnable interface. This method provides an entry point for the thread and you will put your complete business logic inside this method. Following is a simple syntax of the run() method −
```java
public void run( )
```
* **Step 2**
* As a second step, you will instantiate a Thread object using the following constructor −
```java
Thread(Runnable threadObj, String threadName);
```
* Where, threadObj is an instance of a class that implements the Runnable interface and threadName is the name given to the new thread.

* **Step 3**
* Once a Thread object is created, you can start it by calling start() method, which executes a call to run( ) method. Following is a simple syntax of start() method −
```java
void start();
```
