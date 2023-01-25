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
* Try-catch syntax:

```java
try{
}
catch(Exception e){
}
```
* **Try-catch Example:**
```java
public class ExceptionDemo {
	public static void main (String[] args) {
		int a=10;
		for(int i=3;i>=0;i--)
		   try{
		     System.out.println(a/i);  
		   }catch(ArithmeticException e){
		       System.out.println(e);
		   }
	}
}

```
* Output:
```java
3
5
10
java.lang.ArithmeticException: / by zero 
```
* **try** block contains the code that might throw an exception. Don’t write anything extra in try as statements after the exception will not get executed if the exception occurred. Try must be immediately followed by catch or finally block.

```java
public class ExceptionDemo {
	public static void main (String[] args) {
		int a=10;
		for(int i=3;i>=0;i--)
		   try{
		     System.out.println(a/i);  
		   }
	}
}
```
* Compile-time error:
```java
prog.java:5: error: 'try' without 'catch', 'finally' or resource declarations
    try{
    ^
1 error 
```
* The catch block is used to catch the exception thrown by statements in the try block. The catch must follow try else it will give a compile-time error.
```java
public class ExceptionDemo {
	public static void main (String[] args) {
		int a=10;
		for(int i=3;i>=0;i--)
		   try{
		     System.out.println(a/i);  
		   }
		   System.out.println("between try and catch");
		   catch(ArithmeticException e){
		       System.out.println(e);
		   }
	}
}
```
* Compile Time Error:
```java
prog.java:5: error: 'try' without 'catch', 'finally' or resource declarations
    try{
    ^
prog.java:9: error: 'catch' without 'try'
    catch(ArithmeticException e){
    ^
2 errors
```
* **Things to Remember:**
* Do not keep any code after the statement which is prone to exception. Because if an exception occurred, it will straight away jump to the catch or finally block, ignoring all other statements in the try block.

```java
class Main {
	public static void main (String[] args) {
         try
       {
             System.out.println(4/0);
	 //will not get printed
             System.out.println("end of try!");
        }
catch(ArithmeticException e)
        {
            System.out.println("divide by 0");
        }
    }
}
```
* Output:
```java
divide by 0
```
* While catching the exception in the catch block, either you can have directly the class of exception or its superclass.

* Example: Exact Exception
```java
class Main {
	public static void main (String[] args) {
        try{
            System.out.println(4/0);
           }
      
        //ArithmeticException 
        catch(ArithmeticException e){
            System.out.println("divide by 0");
        }
    }
}
```
* Output:
```java
divide by 0
```

* Example: Superclass of Exact Exception
```java
class Main {
	public static void main (String[] args) {
        try{
            System.out.println(4/0);
           }
      
        //superclass of ArithmeticException 
        catch(Exception e){
            System.out.println("divide by 0");
        }
     }
}
```
* Output:
```java
divide by 0
```
* **Java Multiple Catch Block**

* If you have multiple catches, you have to maintain the hierarchy from subclass to superclass.

* **Incorrect:**
```java
class Main {
	public static void main (String[] args) {
        try{
            System.out.println(4/0);
        }catch(Exception e)
        {
            System.out.println("Exception : divide by 0");
        }catch(ArithmeticException e)
        {
            System.out.println("ArithmeticException :divide by 0");
        }
	}
}

Compile-time error:

 prog.java:11: error: exception ArithmeticException has already been caught
        }catch(ArithmeticException e)
         ^
1 error 
```

* **Correct:**
```java
class Main {
	public static void main (String[] args) {
        try{
            System.out.println(4/0);
        }catch(ArithmeticException e)
        {
            System.out.println("ArithmeticException : divide by 0");
        }catch(Exception e)
        {
            System.out.println("Exception : divide by 0");
        }
   }
}
Output:

ArithmeticException: Divide by 0
```

* **Java Finally Block**

* Contains code that must be executed no matter if an exception is thrown or not. It contains code of file release, closing connections, etc.

* Example:

```java
class Main {
	public static void main (String[] args) {
        try{
            System.out.println(4/0);
        }catch(Exception e)
        {
            System.out.println(e);       
        }
        finally
        {
            System.out.println("finally executed");
        }
        
       	        System.out.println("end");
	}
}
Output:

java.lang.ArithmeticException: / by zero
finally executed
end 
```

* Finally, will execute even when we do not handle exceptions. Before halting the program, JVM checks if there is a “finally” block.
```java
class Main {
	public static void main (String[] args) {
        try{
            System.out.println(4/0);
            
        }finally
        {
            System.out.println("cleaning.......");
        }
	}
}

Runtime Error:

 Exception in thread "main" java.lang.ArithmeticException: / by zero
 at Main.main(File.java:4) 
Output:

cleaning.......
```

* **Java Final vs Finally vs Finalize**

**Final** | **Finally**  | **Finalize**
----------|--------------|---------------
Final is used to apply restrictions on class, method, and variable      |  Finally is used in coding, it will be executed whether an exception is handled or not.      |      Finalize is used to perform clean-up processing before garbage is collected. 
Final is a keyword in java    |   Finally is a block in java      |    Finalize is a method in java 
Final is executed upon its call.    |   Finally executes after”try-catch” block.     |   finalize executes just before the destruction of the object.

#### Java Throw Keyword

* It is a keyword that is used to explicitly throw an exception.
* We can use throw where according to our logic an exception should occur.

* **Example:** 

```java
public class ExceptionDemo {
	static void canVote(int age){
		if(age<18)
            try{
                throw new Exception();
            }catch(Exception e){
                System.out.println("you are not an adult!");
            }
		else
		   System.out.println("you can vote!");
	}
	public static void main (String[] args) {
		canVote(20);
		canVote(10);
	}
}
```
* Output:
```console
you can vote!
you are not an adult! 
```

#### Java Throws Keyword

* Throws is a keyword in Java which is used in the signature of method to indicate that this method might throw one of the listed type exceptions. 
* The caller to these methods has to handle the exception using a try-catch block. 

* **Example:**
```java
public class ExceptionDemo {
	static void func(int a) throws Exception{
		   System.out.println(10/a);  
	}
	public static void main (String[] args) {
		try{
		    func(10);
		    func(0);
		}catch(Exception e){
		   System.out.println("can't divide by zero");
		}
	
	}
}
```
* Output:
```console
1
can't divide by zero 
```
* If callee can throw multiple exceptions, then all will be thrown simultaneously.
```java
import java.util.*;

public class ExceptionDemo {
	static void func(int a,int b) throws ArithmeticException, ArrayIndexOutOfBoundsException{
		   System.out.println(10/a); 
		   int[] arr={1,2,3};
		   System.out.println(arr[b]);
	}
	public static void main (String[] args) {
		Scanner in=new Scanner(System.in);
		for(int i=0;i<3;i++){
		try{
		    func(in.nextInt(),in.nextInt());
    		}catch(ArithmeticException e){
    		   System.out.println("can't divide by zero");
    		}catch(ArrayIndexOutOfBoundsException e){
    		   System.out.println("Out of bounds!");
    		}
		     }
		
	}
   }
```
```console
Input:

2 1
0 1
2 3 
Output:

5
2
can't divide by zero
5
Out of bounds! 
```
#### Java Throw vs Throws


**Throw** | **Throws**
----------|--------------
This keyword is used to explicitly throw an exception.   |  This keyword is used to declare an exception.   
A checked exception cannot be propagated with throw only.  |  A checked exception can be propagated with throws.
The throw is followed by an instance and used with a method	 |  Throws are followed by class and used with the method signature. 
You cannot throw multiple exceptions.	 |  You can declare multiple exceptions

#### Java Custom Exception
* You can create your own exception and give implementation as to how it should behave. Your exception will behave like a child’s class of Exception.
* Syntax:
```java
class YourException extends Exception{}
```

* **Why use custom exceptions?**
Java exceptions cover almost all the general types of exceptions that may occur in the programming. However, we sometimes need to create custom exceptions.

* **Following are a few of the reasons to use custom exceptions:**

* To catch and provide specific treatment to a subset of existing Java exceptions.
* Business logic exceptions: These are the exceptions related to business logic and workflow. It is useful for the application users or the developers to understand the exact problem.
* In order to create a custom exception, we need to extend the Exception class that belongs to **java.lang package.**

* Example: We pass the string to the constructor of the superclass- Exception which is obtained using the “getMessage()” function on the object created.

```java

// A Class that represents use-defined exception
 
class MyException extends Exception {
    public MyException(String s)
    {
        // Call constructor of parent Exception
        super(s);
    }
}
 
// A Class that uses above MyException
public class Main {
    // Driver Program
    public static void main(String args[])
    {
        try {
            // Throw an object of user defined exception
            throw new MyException("GeeksGeeks");
        }
        catch (MyException ex) {
            System.out.println("Caught");
 
            // Print the message from MyException object
            System.out.println(ex.getMessage());
        }
    }
}

```
* Output

```console
Caught
GeeksGeeks
```
* In the above code, the constructor of MyException requires a string as its argument. The string is passed to the parent class Exception’s constructor using super(). The constructor of the Exception class can also be called without a parameter and the call to super is not mandatory. 

#### Exception Handling with Method Overriding in Java

* Some of the rules are listed below:
* **If the superclass method does not declare an exception**
   * If the superclass method does not declare an exception, subclass overridden method cannot declare the checked exception but it can declare unchecked exception.
* **If the superclass method declares an exception**
   * If the superclass method declares an exception, subclass overridden method can declare same, subclass exception or no exception but cannot declare parent exception.







