## Java8-Features

![image](https://user-images.githubusercontent.com/40323661/217402004-f14d35e9-80b8-4ebf-8c08-6b344a065850.png)

* Here are the newly added features of Java 8:

**Feature Name** | **Description**
--------------------|--------------
Lambda expression | A function that can be shared or referred to as an object.
Functional Interfaces | Functional Interfaces are the types of interfaces that can contain only a single abstract method. These interfaces are additionally recognized as Single abstract method interfaces.
Method References | Method references are the references that use a function as a parameter to request a method.
Default Method | The default method is a method that provides an implementation of methods within interfaces allowing the Interface development facilities.
Stream API | The Java Stream API is an abstract layer that implements the pipeline processing of the data.
Date Time API |In Java SE 8, the latest, updated Joda-time stimulated APIs are introduced to overcome the disadvantages of the previous versions.
Optional | Optional is a wrapper class included in Java SE 8 that is used to control the imaginary (null) values and assists in additional processing based upon the value.


#### What is lambda expression?

* Lambda expression is anonymous function which have set of parameters and a lambda (->) and a function body .You can call it function without name.

* Lambda expression is a new and important feature of Java which was included in Java SE 8. It provides a clear and concise way to represent one method interface using an expression. It is very useful in collection library. It helps to iterate, filter and extract data from collection.

* The Lambda expression is used to provide the implementation of an interface which has functional interface. It saves a lot of code. In case of lambda expression, we don't need to define the method again for providing the implementation. Here, we just write the implementation code.

* Java lambda expression is treated as a function, so compiler does not create .class file.

#### Why use Lambda Expression
 * To provide the implementation of Functional interface.
 * Less coding.

* Refer below examplese about this (#### 1) Java 8 Lambda Expressions with examples)

#### What is method reference in java 8?

* Method reference is used refer method of functional interface. It is nothing but compact way of lambda expression.You can simply replace lambda expression with method reference.

Syntax:
class::methodname

#### What is Optional? Why and how can you use it?

* Java 8 has introduced new class Called Optional. This class is basically introduced to avoid NullPointerException in java.

* Optional is a container object used to contain not-null objects. Optional object is used to represent null with absent value.

* Optional class encapsulates optional value which is either present or not.
* It is a wrapper around object and can be use to avoid NullPointerExceptions.

#### What is the difference between PermGenSpace and MetaSpace?

* In jdk 8 onwards PermGenSpace is removed. Earlier PermGenSpace is used for storing the metadata. Metadata means storing the information about classes like bytecodes, names and JIT information.

* Java classes metadata now stored in native heap and this space is called MetaSpace. Metaspace grows automatically by default and will be garbage collected.

* So the major difference between PermGenSpace and MetaSpace is that PermGenSpace was fixed in size and did not grow automatically, but MetaSpace does not have any size constraints.


**JVM** | **Default maximum PermGen size (MB)** | **Default maximum Metaspace size**
------------------ | -------------------------- | -----------------------------
32-bit client JVM| 64| unlimited
32-bit server JVM| 64| unlimited
64-bit JVM |82	| unlimited

![java14_1](https://www.javainuse.com/java14_1.jpg "java14_1")

* For Detailed description please refer : https://www.javainuse.com/java/metaspace https://dzone.com/articles/permgen-and-metaspace

####  What is the difference between Predicate and Function?

* Both are functional interfaces.
* Predicate<T> is single argument function and either it returns true or false.This can be used as the assignment target for a lambda expression or method reference.

* Function<T,R> is also single argument function but it returns an Object.Here T denotes type of input to the function and R denotes type of Result.

* This can also be used as the assignment target for a lambda expression or method reference.


#### Are you aware of Date and Time API introduced in Java 8? What the issues with Old Date and time API?


* Issues with old Date and TIme API:

* **Thread Safety:** You might be already aware that java.util.Date is mutable and not thread safe. Even java.text.SimpleDateFormat is also not Thread-Safe. New Java 8 date and time APIs are thread safe.

* **Performance:** Java 8 ‘s new APIs are better in performance than old Java APIs.

* **More Readable:**  Old APIs such Calendar and Date are poorly designed and hard to understand. Java 8 Date and Time APIs are easy to understand and comply with ISO standards.


#### What is the difference between Collection API and Stream API?

* Differences between Collection API and Stream API are as follow :

* 1. Collection API was introduced in jdk 1.2 while Stream API is introduced in jdk 1.8
* 2. Collection objects are created eagerly while Stream API objects are created lazily.
* 3. Iterate and Consume elements at any number of times for Collection object while iterate and consume elements only one time for Stream object.


### What is a default method in Java 8 ? When to use it ? 

* Default method is also known as defender methods or virtual extension methods. It is a  non abstract method i.e have body, which can be declared inside interface.

* Default method is introduced in Java 8 for backward compatibility. That is if you add a new abstract method to the interface, all the implementing classes shall break. Implementing classes need to implement the added abstract method. This problem is solved by default method of java 8.

#### What is the difference between Iterator and Spliterator ?

* Difference between Iterator and Spliterator  are as follow:

* 1. Introduction : Iterator was introduced in jdk 1.2 while Spliterator  is introduced in jdk 1.8
* 2. Use in API  : Iterator is used for Collection API while Spliterator is used for Stream API
* 3. Parallel programming : Iterator can be used for iterating the elements in Collection in sequential order while  Spliterator can be used for iterating the Stream elements in parallel or sequential order.
* 4. Universal Iterator : Iteartor is universal iterator while Spliterator is not a universal iterator.

#### What is the difference and similarities between Function and Predicate in java 8?

* **Difference:**

* 1. Return Type : Function returns an Object and it is a single argument function.
* Predicate return type is boolean (i.e true or false) and it is also a single argument function.

* **Similarities:**

* 1. Both are functional interfaces i.e both contain single abstract method.


#### Java 8-Internal vs. External Iteration

* Before we understand forEach statement, let us first look at the concept of Internal Iterators vs External Iterators.

* **External Iterators-** This Iterator is also known as active iterator or explicit iterator. For this type of iterator the control over iteration of elements is with the programmer. Which means that the programmer define when and how the next element of iteration is called.

```java
List<String> items = new ArrayList<>();
		items.add("test1");
		items.add("test2");
		items.add("test3");
		items.add("test4");
		items.add("test5");
		
		//Traditional java for-each iterator which is an External Iterator.
		for (String item : items) {
			System.out.println(item);
		}
```

```java
	
	Map<String, String> map = new HashMap<>();
		map.put("1", "test1");
		map.put("2", "test2");
		map.put("3", "test3");
		map.put("4", "test4");
		map.put("5", "test5");
		map.put("6", "test6");

		//Traditional way of iterating map elements using external iterator.
		 for(Map.Entry<String, String> entry :map.entrySet()) {
		  System.out.println(entry.getKey());
		  System.out.println(entry.getValue()); }
```
* **Internal Iterators-** This Iterator is also known as passive iterator, implicit iterator or callback iterator. For this type of iterator the control over the iteration of elements lies with the iterator itself. The programmer only tells the iterator "What operation is to be performed on the elements of the collection". Thus the programmer only declares what is to be done and does not manage and control how the iteration of individual elements take place.

```java

	List<String> items = new ArrayList<>();
		items.add("test1");
		items.add("test2");
		items.add("test3");
		items.add("test4");
		items.add("test5");
		
		//iterate over list items
		//Java 8 forEach iterator which is an Internal Iterator.
		items.forEach(item -> System.out.println(item));
```
```java	
	Map<String, String> map = new HashMap<>();
		map.put("1", "test1");
		map.put("2", "test2");
		map.put("3", "test3");
		map.put("4", "test4");
		map.put("5", "test5");
		map.put("6", "test6");

		  //iterate over map items
		  //Java 8 forEach iterator which is an Internal Iterator.
		 map.forEach((key,value)->{ 
		  System.out.println(key);
		  System.out.println(value);
		  
		  });
```

#### Java Stream Distinct Examples

* 1. Find All Distinct Elements

* In this example, we have list of strings and we will find all distinct strings, collect them into another list using collect() which is java stream terminal operations. After collecting the distinct elements, we will verify it by printing them to console.

```Java
Collection<String> list = Arrays.asList("A", "B", "C", "D", "A", "B", "C");
 
// Get collection without duplicate i.e. distinct only
List<String> distinctElements = list.stream().distinct().collect(Collectors.toList());
 
//Let's verify distinct elements
System.out.println(distinctElements);
```
Output is:

```Console
[A, B, C, D]
```
Example 2 :

```java
public static void main(String[] args) 
    { 
  
        // Creating a list of integers 
        List<Integer> list = Arrays.asList(1, 1, 2, 3, 3, 4, 5, 5); 
  
        System.out.println("The distinct elements are :"); 
  
        // Displaying the distinct elements in the list 
        // using Stream.distinct() method 
        list.stream().distinct().forEach(System.out::println); 
    } 
```
Output :

```Console
The distinct elements are :
1
2
3
4
5
```
Example 3:

```java
// Driver code 
    public static void main(String[] args) 
    { 
  
        // Creating a list of strings 
        List<String> list = Arrays.asList("Geeks", "for", "Geeks", 
                                          "GeeksQuiz", "for", "GeeksforGeeks"); 
  
        System.out.println("The distinct elements are :"); 
  
        // Displaying the distinct elements in the list 
        // using Stream.distinct() method 
        list.stream().distinct().forEach(System.out::println); 
    } 
```
Output:

```Console
The distinct elements are :
Geeks
for
GeeksQuiz
GeeksforGeeks
```
Example 4:

```java
public static void main(String[] args) 
    { 
  
        // Creating a list of strings 
        List<String> list = Arrays.asList("Geeks", "for", "Geeks", 
                                          "GeeksQuiz", "for", "GeeksforGeeks"); 
  
        // Storing the count of distinct elements 
        // in the list using Stream.distinct() method 
        long Count = list.stream().distinct().count(); 
  
        // Displaying the count of distinct elements 
        System.out.println("The count of distinct elements is : " + Count); 
    } 
 ```
 Ourput :
 
 ```Console
 The count of distinct elements is : 4
 ```
 
 #### Stream In Java
 
 * Introduced in Java 8, the Stream API is used to process collections of objects. A stream is a sequence of objects that supports various methods which can be pipelined to produce the desired result.
* The features of Java stream are –

* A stream is not a data structure instead it takes input from the Collections, Arrays or I/O channels.
* Streams don’t change the original data structure, they only provide the result as per the pipelined methods.
* Each intermediate operation is lazily executed and returns a stream as a result, hence various intermediate operations can be pipelined. Terminal operations mark the end of the stream and return the result.
    
        
* Different Operations On Streams-
* **Intermediate Operations:**

* **map:** The map method is used to returns a stream consisting of the results of applying the given function to the elements of this stream.
List number = Arrays.asList(2,3,4,5);
List square = number.stream().map(x->x*x).collect(Collectors.toList());
* **filter:** The filter method is used to select elements as per the Predicate passed as argument.
List names = Arrays.asList("Reflection","Collection","Stream");
List result = names.stream().filter(s->s.startsWith("S")).collect(Collectors.toList());
* **sorted:** The sorted method is used to sort the stream.
List names = Arrays.asList("Reflection","Collection","Stream");
List result = names.stream().sorted().collect(Collectors.toList());

* **Terminal Operations:**
* **collect:** The collect method is used to return the result of the intermediate operations performed on the stream.
List number = Arrays.asList(2,3,4,5,3);
Set square = number.stream().map(x->x*x).collect(Collectors.toSet());
* **forEach:** The forEach method is used to iterate through every element of the stream.
List number = Arrays.asList(2,3,4,5);
number.stream().map(x->x*x).forEach(y->System.out.println(y));
* **reduce:** The reduce method is used to reduce the elements of a stream to a single value.
The reduce method takes a BinaryOperator as a parameter.
List number = Arrays.asList(2,3,4,5);
int even = number.stream().filter(x->x%2==0).reduce(0,(ans,i)-> ans+i);

* Program to demonstrate the use of Stream

```java
public static void main(String args[]) 
  { 
  
    // create a list of integers 
    List<Integer> number = Arrays.asList(2,3,4,5); 
  
    // demonstration of map method 
    List<Integer> square = number.stream().map(x -> x*x). 
                           collect(Collectors.toList()); 
    System.out.println(square); 
  
    // create a list of String 
    List<String> names = 
                Arrays.asList("Reflection","Collection","Stream"); 
  
    // demonstration of filter method 
    List<String> result = names.stream().filter(s->s.startsWith("S")). 
                          collect(Collectors.toList()); 
    System.out.println(result); 
  
    // demonstration of sorted method 
    List<String> show = 
            names.stream().sorted().collect(Collectors.toList()); 
    System.out.println(show); 
  
    // create a list of integers 
    List<Integer> numbers = Arrays.asList(2,3,4,5,2); 
  
    // collect method returns a set 
    Set<Integer> squareSet = 
         numbers.stream().map(x->x*x).collect(Collectors.toSet()); 
    System.out.println(squareSet); 
  
    // demonstration of forEach method 
    number.stream().map(x->x*x).forEach(y->System.out.println(y)); 
  
    // demonstration of reduce method 
    int even = 
       number.stream().filter(x->x%2==0).reduce(0,(ans,i)-> ans+i); 
  
    System.out.println(even); 
  }
```
Output:

```Console
[4, 9, 16, 25]
[Stream]
[Collection, Reflection, Stream]
[16, 4, 9, 25]
4
9
16
25
6
```

