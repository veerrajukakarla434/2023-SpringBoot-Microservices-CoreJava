# CoreJava-Strings

#### Java Strings
* In Java, string is basically an object that represents sequence of char values. An array of characters works same as Java string.
* Strings are used for storing text.
* A String variable contains a collection of characters surrounded by double quotes:

* **What is String in java**
* Generally, String is a sequence of characters. But in Java, string is an object that represents a sequence of characters. The java.lang.String class is used to create a string object.

* Java String class provides a lot of methods to perform operations on strings such as **compare(), concat(), equals(), split(), length(), replace(), compareTo(), intern(), substring()** etc.

* The java.lang.String class implements Serializable, Comparable and CharSequence interfaces.

![string-implements](https://static.javatpoint.com/images/core/string-implements.png "string-implements")

#### CharSequence Interface
* The CharSequence interface is used to represent the sequence of characters. String, StringBuffer and StringBuilder classes implement it. It means, we can create strings in java by using these three classes.

![charsequence](https://static.javatpoint.com/images/core/charsequence.png "charsequence")

* The Java String is immutable which means it cannot be changed. Whenever we change any string, a new instance is created. For mutable strings, you can use StringBuffer and StringBuilder classes.

* We will discuss immutable string later. Let's first understand what is String in Java and how to create the String object.

* **How to create a string object?**
* There are two ways to create String object:
  * By string literal
  * By new keyword

* **1) String Literal**
* Java String literal is created by using double quotes. For Example:
```java
String s="welcome"; 
```
* Each time you create a string literal, the JVM checks the "string constant pool" first. If the string already exists in the pool, a reference to the pooled instance is returned. If the string doesn't exist in the pool, a new string instance is created and placed in the pool. For example:
```java
String s1="Welcome";  
String s2="Welcome";//It doesn't create a new instance  
```
![string](https://static.javatpoint.com/images/string.JPG "")

* In the above example, only one object will be created. Firstly, JVM will not find any string object with the value "Welcome" in string constant pool, that is why it will create a new object. After that it will find the string with the value "Welcome" in the pool, it will not create a new object but will return the reference to the same instance.

```Console
Note: String objects are stored in a special memory area known as the "string constant pool".
```
#### Why Java uses the concept of String literal?
* To make Java more memory efficient (because no new objects are created if it exists already in the string constant pool).

* **2) By new keyword**
```java
String s=new String("Welcome");//creates two objects and one reference variable  
```
* In such case, JVM will create a new string object in normal (non-pool) heap memory, and the literal "Welcome" will be placed in the string constant pool. The variable s will refer to the object in a heap (non-pool).

```java
Java String Example
public class StringExample{  
public static void main(String args[]){  
String s1="java";//creating string by java string literal  
char ch[]={'s','t','r','i','n','g','s'};  
String s2=new String(ch);//converting char array to string  
String s3=new String("example");//creating java string by new keyword  
System.out.println(s1);  
System.out.println(s2);  
System.out.println(s3);  
}}  

out Put :
java
strings
example
```
#### Why String is Immutable or Final in Java ?

* String pool is possible only because String is immutable in Java. This way Java Runtime saves a lot of heap space because different String variables can refer to the same String variable in the pool. If String would not have been immutable, then String interning would not have been possible because if any variable would have changed the value, it would have been reflected in the other variables too.

* If String is not immutable then it would cause a severe security threat to the application. For example, database username, password are passed as String to get database connection and in socket programming host and port details passed as String. Since String is immutable, its value can’t be changed otherwise any hacker could change the referenced value to cause security issues in the application.

* Since String is immutable, it is safe for multithreading. A single String instance can be shared across different threads. This avoids the use of synchronization for thread safety. Strings are implicitly thread-safe.

* Strings are used in java classloader and immutability provides security that correct class is getting loaded by Classloader. For example, think of an instance where you are trying to load java.sql.Connection class but the referenced value is changed to myhacked.Connection class that can do unwanted things to your database.

* Since String is immutable, its hashcode is cached at the time of creation and it doesn’t need to be calculated again. This makes it a great candidate for the key in a Map and its processing is faster than other HashMap key objects. This is why String is the most widely used as HashMap keys.

#### What is String Pool in Java ?

* As the name suggests, String Pool in java is a pool of Strings stored in Java Heap Memory. We know that String is special class in java and we can create String object using new operator as well as providing values in double quotes.

* Here is a diagram which clearly explains how String Pool is maintained in java heap space and what happens when we use different ways to create Strings.

![String-Pool-Java1](https://cdn.journaldev.com/wp-content/uploads/2012/11/String-Pool-Java1.png "String-Pool-Java1")

* String Pool is possible only because String is immutable in Java and its implementation of String interning concept. String pool is also example of Flyweight design pattern.

* However using new operator, we force String class to create a new String object in heap space. We can use intern() method to put it into the pool or refer to another String object from the string pool having the same value.

![image](https://user-images.githubusercontent.com/40323661/213749118-3dc1549e-f640-4c83-9961-adf77922ef38.png)


```Java
package com.journaldev.util;

public class StringPool {

    /**
     * Java String Pool example
     * @param args
     */
    public static void main(String[] args) {
        String s1 = "Cat";
        String s2 = "Cat";
        String s3 = new String("Cat");
        
        System.out.println("s1 == s2 :"+(s1==s2));
        System.out.println("s1 == s3 :"+(s1==s3));
        System.out.println("s1.equals(s3) :"+(s1.equals(s3)));
        System.out.println("s1.equals(s2) :"+(s1.equals(s2)));
    }

}
```

Output of the above program is:

```Console
s1 == s2 :true
s1 == s3 :false
s1.equals(s3) :true
s1.equals(s2) :true
```

#### How many Strings are getting Created in the String Pool?

* Sometimes in java interview, you will be asked a question around String pool. For example, how many strings are getting created in the below statement;

```Java
String str = new String("Cat");
```

* In the above statement, either 1 or 2 string will be created. If there is already a string literal “Cat” in the pool, then only one string “str” will be created in the pool. If there is no string literal “Cat” in the pool, then it will be first created in the pool and then in the heap space, so a total of 2 string objects will be created.

#### final vs Immutability in Java

* **final :** In Java, final is a modifier which is used for class, method and variable also. When a variable is declared with final keyword, it’s value can’t be modified, essentially, a constant.

* **Immutability :** In simple terms, immutability means unchanging over time or unable to be changed. In Java, we know that String objects are immutable means we cant change anything to the existing String objects.

* final means that you can’t change the object’s reference to point to another reference or another object, but you can still mutate its state (using setter methods e.g). Whereas immutable means that the object’s actual value can’t be changed, but you can change its reference to another one.
* final modifier is applicable for variable but not for objects, Whereas immutability applicable for an object but not for variables.
* By declaring a reference variable as final, we won’t get any immutability nature, Even though reference variable is final. We can perform any type of change in the corresponding Object. But we cant perform reassignment for that variable.
* final ensures that the address of the object remains the same whereas the Immutable suggests that we can’t change the state of the object once created.

```Java
// Java program to illustrate 
// difference between final 
// and immutability 
  
class Geeks { 
    public static void main(String[] args) 
    { 
        final StringBuffer sb = new StringBuffer("Hello"); 
  
        // Even though reference varibale sb is final 
        // We can perform any changes 
        sb.append("GFG"); 
  
        System.out.println(sb); 
  
        // Here we will get Compile time error 
        // Because reassignment is not possible for final variable 
        sb = new StringBuffer("Hello World"); 
  
        System.out.println(sb); 
    } 
} 
```
Output:

```Console
Geeks.java:14: error: cannot assign a value to final variable sb
        sb = new StringBuffer("Hello World");
        ^
1 error

```
* **Pictorial Representation of the above Program**
![Untitled-32](https://media.geeksforgeeks.org/wp-content/uploads/Untitled-32.png "Untitled-32")

* **Explanation:** In the above picture, we can see that we are creating an object of StringBuffer class by making reference final.

* Declaring reference variable as final, does not mean that the object is immutable.
* In the next line we are performing append() operation on the created object and it is successfully changed.
* If the object is immutable, then the above append operation can’t be done.
* But it is executed successfully as we declare reference variable as final. final means we can’t reassign anything to that reference variable again.
* Therefore when we try to create a new object of BufferedReader then it wont created any object by throwing an error to the console.

#### Java String Oerations:

#### Java String intern()

* Let’s try to understand intern() method with a simple program.

```Java
package com.journaldev.string;

public class StringIntern {

	public static void main(String args[]) {

		String s1 = new String("abc"); // goes to Heap Memory, like other objects
		String s2 = "abc"; // goes to String Pool
		String s3 = "abc"; // again, goes to String Pool

		// Let's check out above theories by checking references
		System.out.println("s1==s2? " + (s1 == s2)); // should be false
		System.out.println("s2==s3? " + (s2 == s3)); // should be true

		// Let's call intern() method on s1 now
		s1 = s1.intern(); // this should return the String with same value, BUT from String Pool

		// Let's run the test again
		System.out.println("s1==s2? " + (s1 == s2)); // should be true now

	}
}
```

Output:

```Console
s1==s2? false
s2==s3? true
s1==s2? true
```
**String intern() Example Explanation**
* When we are using new operator, the String is created in the heap space. So “s1” object is created in the heap memory with value “abc”.
* When we create string literal, it’s created in the string pool. So “s2” and “s3” are referring to string object in the pool having value “abc”.
* In the first print statement, s1 and s2 are referring to different objects. Hence s1==s2 is returning false.
* In the second print statement, s2 and s3 are referring to the same object in the pool. Hence s2==s3 is returning true.
* Now, when we are calling s1.intern(), JVM checks if there is any string in the pool with value “abc” is present? Since there is a string object in the pool with value “abc”, its reference is returned.
* Notice that we are calling s1 = s1.intern(), so the s1 is now referring to the string pool object having value “abc”.
* At this point, all the three string objects are referring to the same object in the string pool. Hence s1==s2 is returning true now.

#### Get Length of a String
* To find the length of a string, we use the length() method of the String. For example,
```java
class Main {
  public static void main(String[] args) {

    // create a string
    String greet = "Hello! World";
    System.out.println("String: " + greet);

    // get the length of greet
    int length = greet.length();
    System.out.println("Length: " + length);
  }
}
Output

String: Hello! World
Length: 12
```
##### Join two Strings
* We can join two strings in Java using the concat() method. For example,
```java
class Main {
  public static void main(String[] args) {

    // create first string
    String first = "Java ";
    System.out.println("First String: " + first);

    // create second
    String second = "Programming";
    System.out.println("Second String: " + second);

    // join two strings
    String joinedString = first.concat(second);
    System.out.println("Joined String: " + joinedString);
  }
}
Output

First String: Java 
Second String: Programming     
Joined String: Java Programming
```
#### Compare two Strings
* In Java, we can make comparisons between two strings using the equals() method. For example,
```java
class Main {
  public static void main(String[] args) {

    // create 3 strings
    String first = "java programming";
    String second = "java programming";
    String third = "python programming";

    // compare first and second strings
    boolean result1 = first.equals(second);
    System.out.println("Strings first and second are equal: " + result1);

    // compare first and third strings
    boolean result2 = first.equals(third);
    System.out.println("Strings first and third are equal: " + result2);
  }
}
Output

Strings first and second are equal: true
Strings first and third are equal: false
```
* In the above example, we have created 3 strings named first, second, and third. Here, we are using the equal() method to check if one string is equal to another.

* The equals() method checks the content of strings while comparing them. 

#### Java String compare
* we can compare string in java on the basis of content and reference.

* It is used in authentication (by equals() method), sorting (by compareTo() method), reference matching (by == operator) etc.

* There are three ways to compare string in java:

  * By equals() method
  * By = = operator
  * By compareTo() method
#### 1) String compare by equals() method
* The String equals() method compares the original content of the string. It compares values of string for equality. String class provides two methods:

  * **public boolean equals(Object another)*  compares this string to the specified object.
  * **public boolean equalsIgnoreCase(String another)** compares this String to another string, ignoring case.
```java
class Teststringcomparison1{  
 public static void main(String args[]){  
   String s1="Sachin";  
   String s2="Sachin";  
   String s3=new String("Sachin");  
   String s4="Saurav";  
   System.out.println(s1.equals(s2));//true  
   System.out.println(s1.equals(s3));//true  
   System.out.println(s1.equals(s4));//false  
 }  
}  

Output:true
       true
       false
 ************************************************      
class Teststringcomparison2{  
 public static void main(String args[]){  
   String s1="Sachin";  
   String s2="SACHIN";  
  
   System.out.println(s1.equals(s2));//false  
   System.out.println(s1.equalsIgnoreCase(s2));//true  
 }  
}  

Output:

false
true
```
