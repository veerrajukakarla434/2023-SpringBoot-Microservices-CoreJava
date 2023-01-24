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

![image](https://user-images.githubusercontent.com/40323661/214184987-5cb7642e-96b0-483a-85cb-a024562928d4.png)


* **Types of Exceptions**

* Java defines several types of exceptions that relate to its various class libraries. Java also allows users to define their own exceptions.

![image](https://user-images.githubusercontent.com/40323661/214185265-5e82d269-51a4-4d6f-bf6a-e5f3acb9f381.png)

* **Exceptions can be categorized in two ways:**

   * Built-in Exceptions
      * Checked Exception
      * Unchecked Exception 
   * User-Defined Exceptions

* **Checked Exceptions:** Checked exceptions are called compile-time exceptions because these exceptions are checked at compile-time by the compiler.
 
* **Unchecked Exceptions:**  The unchecked exceptions are just opposite to the checked exceptions. The compiler will not check these exceptions at compile time. In simple words, if a program throws an unchecked exception, and even if we didn’t handle or declare it, the program would not give a compilation error.

* **The advantages of Exception Handling in Java are as follows:**

* Provision to Complete Program Execution
* Easy Identification of Program Code and Error-Handling Code
* Propagation of Errors
* Meaningful Error Reporting
* Identifying Error Types

* **Java Exception Keywords**

* Exception Handling in java is managed via five keywords: **try, catch, throw, throws, and finally**. Here are 5 keywords that are used in handling exceptions in Java


* **try**	This keyword is used to specify a block and this block must be followed by either catch or finally. That is, we can’t use try block alone.

* **catch**	This keyword must be preceded by a try block to handle the exception and can be followed by a final block later.

* **finally** 	This keyword is used to execute the program, whether an exception is handled or not.

* **throw**	This keyword is used to throw an exception.

* **throws**	This keyword is used to declare exceptions.

* **Java Try-Catch Block**
```java
Try-catch syntax:

try{
}
catch(Exception e){
}
```


