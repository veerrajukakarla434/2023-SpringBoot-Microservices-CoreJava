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

