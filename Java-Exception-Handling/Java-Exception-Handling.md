# Java-Exception-Handling

* **Exception** is an unwanted or unexpected event, which occurs during the execution of a program, i.e. at run time, that disrupts the normal flow of the program’s instructions. 

* Exceptions can be caught and handled by the program. When an exception occurs within a method, it creates an object. This object is called the **exception object**.

*  It contains information about the exception, such as the name and description of the exception and the state of the program when the exception occurred.

* Developers can explicitly write the implementation for handling the exception. Once an exception is handled, the normal execution of code will continue.

* Preferable: handle exceptions to ensure your code gets executed normally.

* **Major reasons why an exception Occurs**

* Invalid user input
* Device failure
* Loss of network connection
* Physical limitations (out of disk memory)
* Code errors
* Opening an unavailable file

* Errors represent irrecoverable conditions such as Java virtual machine (JVM) running out of memory, memory leaks, stack overflow errors, library incompatibility, infinite recursion, etc. Errors are usually beyond the control of the programmer, and we should not try to handle errors.

* Let us discuss the most important part which is the **differences between Error and Exception** that is as follows: 

* **Error**: An Error indicates a serious problem that a reasonable application should not try to catch.
* **Exception**: Exception indicates conditions that a reasonable application might try to catch.

#### Exception Hierarchy

* All exception and error types are subclasses of class Throwable, which is the base class of the hierarchy. One branch is headed by Exception. This class is used for exceptional conditions that user programs should catch. NullPointerException is an example of such an exception. Another branch, Error is used by the Java run-time system(JVM) to indicate errors having to do with the run-time environment itself(JRE). StackOverflowError is an example of such an error.

![image](https://user-images.githubusercontent.com/40323661/214184894-c25fabab-afdb-484f-894b-525095c30c17.png)









