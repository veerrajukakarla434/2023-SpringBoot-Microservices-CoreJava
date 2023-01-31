## Java - Threads & Multithreading

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
#### Example
* Here is an example that creates a new thread and starts running it −
```java
class RunnableDemo implements Runnable {
   private Thread t;
   private String threadName;
   
   RunnableDemo( String name) {
      threadName = name;
      System.out.println("Creating " +  threadName );
   }
   
   public void run() {
      System.out.println("Running " +  threadName );
      try {
         for(int i = 4; i > 0; i--) {
            System.out.println("Thread: " + threadName + ", " + i);
            // Let the thread sleep for a while.
            Thread.sleep(50);
         }
      } catch (InterruptedException e) {
         System.out.println("Thread " +  threadName + " interrupted.");
      }
      System.out.println("Thread " +  threadName + " exiting.");
   }
   
   public void start () {
      System.out.println("Starting " +  threadName );
      if (t == null) {
         t = new Thread (this, threadName);
         t.start ();
      }
   }
}

public class TestThread {

   public static void main(String args[]) {
      RunnableDemo R1 = new RunnableDemo( "Thread-1");
      R1.start();
      
      RunnableDemo R2 = new RunnableDemo( "Thread-2");
      R2.start();
   }   
}
This will produce the following result −

Output
Creating Thread-1
Starting Thread-1
Creating Thread-2
Starting Thread-2
Running Thread-1
Thread: Thread-1, 4
Running Thread-2
Thread: Thread-2, 4
Thread: Thread-1, 3
Thread: Thread-2, 3
Thread: Thread-1, 2
Thread: Thread-2, 2
Thread: Thread-1, 1
Thread: Thread-2, 1
Thread Thread-1 exiting.
Thread Thread-2 exiting.
```

#### Synchronization in Java

* Synchronization in Java is the capability to control the access of multiple threads to any shared resource.
* Java Synchronization is better option where we want to allow only one thread to access the shared resource.

* **Why use Synchronization?**
* The synchronization is mainly used to
      * To prevent thread interference.
      * To prevent consistency problem.

#### Thread Synchronization
* There are two types of thread synchronization mutual exclusive and inter-thread communication.

* **Mutual Exclusive**
      * Synchronized method.
      * Synchronized block.
      * Static synchronization.
* **Cooperation (Inter-thread communication in java)**

#### Mutual Exclusive
* Mutual Exclusive helps keep threads from interfering with one another while sharing data. It can be achieved by using the following three ways:

      * By Using Synchronized Method
      * By Using Synchronized Block
      * By Using Static Synchronization
#### Concept of Lock in Java
* Synchronization is built around an internal entity known as the lock or monitor. Every object has a lock associated with it. By convention, a thread that needs consistent access to an object's fields has to acquire the object's lock before accessing them, and then release the lock when it's done with them.

* **From Java 5 the package java.util.concurrent.locks contains several lock implementations.**

#### Understanding the problem without Synchronization
* In this example, there is no synchronization, so output is inconsistent. Let's see the example:

```java
class Table{  
void printTable(int n){//method not synchronized  
   for(int i=1;i<=5;i++){  
     System.out.println(n*i);  
     try{  
      Thread.sleep(400);  
     }catch(Exception e){System.out.println(e);}  
   }  
  
 }  
}  
  
class MyThread1 extends Thread{  
Table t;  
MyThread1(Table t){  
this.t=t;  
}  
public void run(){  
t.printTable(5);  
}  
  
}  
class MyThread2 extends Thread{  
Table t;  
MyThread2(Table t){  
this.t=t;  
}  
public void run(){  
t.printTable(100);  
}  
}  
  
class TestSynchronization1{  
public static void main(String args[]){  
Table obj = new Table();//only one object  
MyThread1 t1=new MyThread1(obj);  
MyThread2 t2=new MyThread2(obj);  
t1.start();  
t2.start();  
}  
}  

```

OutPut:
```java
       5
       100
       10
       200
       15
       300
       20
       400
       25
       500
```       

#### Java Synchronized Method
* If you declare any method as synchronized, it is known as synchronized method.

* Synchronized method is used to lock an object for any shared resource.

* When a thread invokes a synchronized method, it automatically acquires the lock for that object and releases it when the thread completes its task.

```java
class Table{  
 synchronized void printTable(int n){//synchronized method  
   for(int i=1;i<=5;i++){  
     System.out.println(n*i);  
     try{  
      Thread.sleep(400);  
     }catch(Exception e){System.out.println(e);}  
   }  
  
 }  
}  
  
class MyThread1 extends Thread{  
Table t;  
MyThread1(Table t){  
this.t=t;  
}  
public void run(){  
t.printTable(5);  
}  
  
}  
class MyThread2 extends Thread{  
Table t;  
MyThread2(Table t){  
this.t=t;  
}  
public void run(){  
t.printTable(100);  
}  
}  
  
public class TestSynchronization2{  
public static void main(String args[]){  
Table obj = new Table();//only one object  
MyThread1 t1=new MyThread1(obj);  
MyThread2 t2=new MyThread2(obj);  
t1.start();  
t2.start();  
}  
}  

```
* Output:
```java
5
       10
       15
       20
       25
       100
       200
       300
       400
       500
```
#### Deadlock in Java

* **Deadlock in Java is a part of multithreading. Deadlock can occur in a situation when a thread is waiting for an object lock, that is acquired by another thread and second thread is waiting for an object lock that is acquired by first thread. Since, both threads are waiting for each other to release the lock, the condition is called deadlock.**

![image](https://user-images.githubusercontent.com/40323661/215368264-9245bdd5-76c4-42b7-81a0-74c9e431513b.png)

* **Example of Deadlock in Java**

```java
public class TestDeadlockExample1 {  
  public static void main(String[] args) {  
    final String resource1 = "ratan jaiswal";  
    final String resource2 = "vimal jaiswal";  
    // t1 tries to lock resource1 then resource2  
    Thread t1 = new Thread() {  
      public void run() {  
          synchronized (resource1) {  
           System.out.println("Thread 1: locked resource 1");  
  
           try { Thread.sleep(100);} catch (Exception e) {}  
  
           synchronized (resource2) {  
            System.out.println("Thread 1: locked resource 2");  
           }  
         }  
      }  
    };  
  
    // t2 tries to lock resource2 then resource1  
    Thread t2 = new Thread() {  
      public void run() {  
        synchronized (resource2) {  
          System.out.println("Thread 2: locked resource 2");  
  
          try { Thread.sleep(100);} catch (Exception e) {}  
  
          synchronized (resource1) {  
            System.out.println("Thread 2: locked resource 1");  
          }  
        }  
      }  
    };  
  
      
    t1.start();  
    t2.start();  
  }  
}       
Output:

Thread 1: locked resource 1
        Thread 2: locked resource 2
```

#### How to avoid deadlock?
* A solution for a problem is found at its roots. In deadlock it is the pattern of accessing the resources A and B, is the main issue. To solve the issue we will have to simply re-order the statements where the code is accessing shared resources.

```java
public class DeadlockSolved {  
   
    public static void main(String ar[]) {  
        DeadlockSolved test = new DeadlockSolved();  
   
        final resource1 a = test.new resource1();  
        final resource2 b = test.new resource2();  
   
   // Thread-1  
Runnable b1 = new Runnable() {  
    public void run() {  
        synchronized (b) {  
            try {  
                /* Adding delay so that both threads can start trying to lock resources */  
                Thread.sleep(100);  
            } catch (InterruptedException e) {  
                e.printStackTrace();  
            }  
            // Thread-1 have resource1 but need resource2 also  
            synchronized (a) {  
                System.out.println("In block 1");  
            }  
        }  
    }  
};  
   
// Thread-2  
Runnable b2 = new Runnable() {  
    public void run() {  
        synchronized (b) {  
            // Thread-2 have resource2 but need resource1 also  
            synchronized (a) {  
                System.out.println("In block 2");  
            }  
        }  
    }  
};  
  
   
        new Thread(b1).start();  
        new Thread(b2).start();  
    }  
   
    // resource1  
    private class resource1 {  
        private int i = 10;  
   
        public int getI() {  
            return i;  
        }  
   
        public void setI(int i) {  
            this.i = i;  
        }  
    }  
   
    // resource2  
    private class resource2 {  
        private int i = 20;  
   
        public int getI() {  
            return i;  
        }  
   
        public void setI(int i) {  
            this.i = i;  
        }  
    }  
}  
Output:

In block 1
In block 2

```




        
