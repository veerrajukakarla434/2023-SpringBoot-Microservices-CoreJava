## CoreJava-Collections

#### Introduction to Collections

* A collection — sometimes called a container — is simply an object that groups multiple elements into a single unit. Collections are used to store, retrieve, manipulate, and communicate aggregate data.

* What are **Java collections?** Java collections refer to a collection of individual objects that are represented as a single unit. You can perform all operations such as searching, sorting, insertion, manipulation, deletion, etc., on Java collections just like you do it on data.

#### What is a Java Collection Framework?

* A Java collection framework provides an architecture to store and manipulate a group of objects. A Java collection framework includes the following:

      * Interfaces
      * Classes
      * Algorithm
* Let’s learn about them in detail:

* **Interfaces:** Interface in Java refers to the abstract data types. They allow Java collections to be manipulated independently from the details of their representation. Also, they form a hierarchy in object-oriented programming languages.

* **Classes:** Classes in Java are the implementation of the collection interface. It basically refers to the data structures that are used again and again.

* **Algorithm:** Algorithm refers to the methods which are used to perform operations such as searching and sorting, on objects that implement collection interfaces. Algorithms are polymorphic in nature as the same method can be used to take many forms or you can say perform different implementations of the Java collection interface.


#### Why use Java collection?
* There are several benefits of using Java collections such as:
   
      * Reducing the effort required to write the code by providing useful data structures and algorithms
      * Java collections provide high-performance and high-quality data structures and algorithms thereby increasing the speed and quality
      * Unrelated APIs can pass collection interfaces back and forth
      * Decreases extra effort required to learn, use, and design new API’s
      * Supports reusability of standard data structures and algorithms

#### Java Collection Framework Hierarchy

![image](https://user-images.githubusercontent.com/40323661/215625747-b3ab3679-387d-4770-9f89-8d88e415ca8b.png)


* Including Map Hierachy

![image](https://user-images.githubusercontent.com/40323661/215626100-da2d75d8-1309-4c97-b970-a00d9c1ec9c8.png)


* **Collection Interface Class Diagram**

![image](https://user-images.githubusercontent.com/40323661/215902349-a8f0dc1e-61b1-460a-a836-ce2e0d43a3ad.png)

* From the above class diagram, the Collection interface extends the Iterable interface which is a member of the java.lang package.  Implementing the Iterable interface allows an object to be the target of the "for-each loop" statement.

#### Collection Interface Example

* The following example demonstrates the usage of important Collection interface methods:

```java

package com.java.collections.interfaces;

import java.util.ArrayList;
import java.util.Collection;

public class CollectionDemo {

    public static void main(String[] args) {

        Collection < String > fruitCollection = new ArrayList < > ();
        fruitCollection.add("banana");
        fruitCollection.add("apple");
        fruitCollection.add("mango");
        System.out.println(fruitCollection);

        fruitCollection.remove("banana");
        System.out.println(fruitCollection);

        System.out.println(fruitCollection.contains("apple"));

        fruitCollection.forEach((element) -> {
            System.out.println(element);
        });

        fruitCollection.clear();

        System.out.println(fruitCollection);
    }
}
```
* OUTPUT:

```java
[banana, apple, mango]
[apple, mango]
true
apple
mango
[]
```

* In JDK 8 and later, the Collection interface also exposes methods Stream stream() and Stream parallelStream(), for obtaining sequential or parallel streams from the underlying collection. 

* Let's take the example of List sorting using Collection class. We can sort any Collection using “Collections” utility class. i.e.; ArrayList of Strings can be sorted alphabetically using this utility class. ArrayList class itself is not providing any methods to sort. We use Collections class static methods to do this. Below program shows use of **reverse(), shuffle(), frequency()** methods as well.

* Example2 

```java
public class CollectionsDemo {

	public static void main(String[] args) {
		List<String>student<String>List = new ArrayList();
		studentList.add("Neeraj");
		studentList.add("Mahesh");
		studentList.add("Armaan");
		studentList.add("Preeti");
		studentList.add("Sanjay");
		studentList.add("Neeraj");
		studentList.add("Zahir");

		System.out.println("Original List " + studentList);

		Collections.sort(studentList);
		System.out.println("Sorted alphabetically List " + studentList);

		Collections.reverse(studentList);
		System.out.println("Reverse List " + studentList);
		Collections.shuffle(studentList);
		System.out.println("Shuffled List " + studentList);
		System.out.println("Checking occurance of Neeraj: "
				+ Collections.frequency(studentList, "Neeraj"));
	}
}

```
![image](https://user-images.githubusercontent.com/40323661/215904938-d3c337b5-6724-4529-a5fe-c1b4d8c77c3f.png)

#### List Interface Overview

* List interface is a child interface of the Collection interface.

* If we want to represent a group of individual objects where duplicates are allowed and insertion order preserved then we should go for List.

* We can preserve insertion order and we can differentiate duplicate objects by using Index hence index will play a very important role in List.

* The user of this interface has precise control over where in the list each element is inserted.

* A list may contain multiple null elements.

* List interface can contain duplicate elements. 

* List interface implementations classes:

          * ArrayList 
          * LinkedList 
          * Vector
          * Stack

#### List Interface with It's ArrayList Implementation Class Example

* Here is a simple **List interface** example using the **ArrayList implementation class**. 
* This example demonstrates that **List allows to store duplicate elements, null values, and maintains the insertion order:**

```java
package com.java.collections.interfaces;

import java.util.ArrayList;
import java.util.List;

public class ListDemo {
    public static void main(String[] args) {
        List < String > list = new ArrayList < > ();
        // List allows you to add duplicate elements
        list.add("element1");
        list.add("element1");
        list.add("element2");
        list.add("element2");
        System.out.println(list);

        // List allows you to have ‘null’ elements.
        list.add(null);
        list.add(null);
        System.out.println(list);

        // insertion order
        list.add("element1"); // 0
        list.add("element2"); // 1
        list.add("element4"); // 2
        list.add("element3"); // 3
        list.add("element5"); // 4

        System.out.println(list);

        // access elements from list

        System.out.println(list.get(0));
        System.out.println(list.get(4));

    }
}
```
![image](https://user-images.githubusercontent.com/40323661/215906291-875d106d-888c-4a2f-bed6-a91d4ef3f49b.png)


#### List Interface with It's LinkedList Implementation Class Example

* The following example shows how to create a LinkedList and add new elements to it. 

```java
package com.javaguides.collections.linkedlistexamples;

import java.util.ArrayList;
import java.util.LinkedList;
import java.util.List;

public class CreateLinkedListExample {
     public static void main(String[] args) {
	        // Creating a LinkedList
	        LinkedList<String> fruits = new LinkedList<>();
	        
	        // Adding new elements to the end of the LinkedList using add() method.
	        fruits.add("Banana");
	        fruits.add("Apple");
	        fruits.add("mango");
	        
	        System.out.println("Initial LinkedList : " + fruits);

	        // Adding an element at the specified position in the LinkedList
	        fruits.add(2, "Watermelon");
	     
	        System.out.println("After add(2, \"Watermelon\"); : " + fruits);

	        // Adding an element at the beginning of the LinkedList
	        fruits.addFirst("Strawberry");
	        System.out.println("After addFirst(\"Strawberry\") : " + fruits);

	        // Adding an element at the end of the LinkedList 
	        // (This method is equivalent to the add() method)
	        fruits.addLast("Orange");
	        System.out.println("After addLast(\"Orange\"); : " + fruits);

	        // Adding all the elements from an existing collection to 
	        // the end of the LinkedList
	        List<String> moreFruits = new ArrayList<>();
	        moreFruits.add("Grapes");
	        moreFruits.add("Pyrus");

	        fruits.addAll(moreFruits);
	        System.out.println("After addAll(moreFruits) : " + fruits);
	    }
	}
```
* OUTPUT:

```java
Initial LinkedList : [Banana, Apple, mango]
After add(2, "Watermelon"); : [Banana, Apple, Watermelon, mango]
After addFirst("Strawberry") : [Strawberry, Banana, Apple, Watermelon, mango]
After addLast("Orange"); : [Strawberry, Banana, Apple, Watermelon, mango, Orange]
After addAll(moreFruits) : [Strawberry, Banana, Apple, Watermelon, mango, Orange, Grapes, Pyrus]
```
#### Difference Between ArrayList and LinkedList

* ArrayList and LinkedList both implement the List interface and maintain insertion order. **Both are non-synchronized classes.**

* However, there are many differences between the ArrayList and LinkedList classes that are given below.

**ArrayList** | **LinkedList**
----------|--------------
ArrayList internally uses a dynamic array to store the elements. | LinkedList internally uses a doubly linked list to store the elements.
Manipulation with ArrayList is slow because it internally uses an array. If any element is removed from the array, all the other elements are shifted in memory. | Manipulation with LinkedList is faster than ArrayList because it uses a doubly linked list, so no bit shifting is required in memory.
An ArrayList class can act as a list only because it implements List only. |LinkedList class can act as a list and queue both because it implements List and Deque interfaces.
ArrayList is better for storing and accessing data. | LinkedList is better for manipulating data.
The memory location for the elements of an ArrayList is contiguous. |The location for the elements of a linked list is not contagious. 
Generally, when an ArrayList is initialized, a default capacity of 10 is assigned to the ArrayList. |There is no case of default capacity in a LinkedList. In LinkedList, an empty list is created when a LinkedList is initialized.
To be precise, an ArrayList is a resizable array. |LinkedList implements the doubly linked list of the list interface.


#### Vector

```java
import java.util.*;
public class JavaExample{
  public static void main(String args[]){
    Vector<String> v=new Vector<>();
    v.add("item1"); //["item1"]
    v.add("item2"); //["item1", "item2"]
    v.add("item3"); //["item1", "item2", "item3"]

    //removing an element
    v.remove("item2"); //["item1", "item3"]

    System.out.println("Vector Elements: ");
    //iterating Vector using iterator
    Iterator<String> it=v.iterator();
    while(it.hasNext()){
      System.out.println(it.next());
    }
  }
}

```

![image](https://user-images.githubusercontent.com/40323661/215909222-cb375079-e383-4f02-a117-7536b1247679.png)

#### Stack

* Stack class extends Vector class, which means it is a subclass of Vector. Stack works on the concept of Last In First Out (LIFO). The elements are inserted using push() method at the end of the stack, the pop() method removes the element which was inserted last in the Stack.

```java
import java.util.*;
public class JavaExample{
  public static void main(String args[]){
    Stack<String> stack = new Stack<>();

    //push() method adds the element in the stack
    //and pop() method removes the element from the stack
    stack.push("Chaitanya"); //["Chaitanya"]
    stack.push("Ajeet"); //["Chaitanya", Ajeet]
    stack.push("Hari"); //["Chaitanya", "Ajeet", "Hari"]
    stack.pop(); //removes the last element
    stack.push("Steve"); //["Chaitanya", "Ajeet", "Steve"]
    stack.push("Carl"); //["Chaitanya", "Ajeet", "Steve", "Carl"]
    stack.pop(); //removes the last element

    System.out.println("Stack elements: ");
    for(String str: stack){
      System.out.println(str);
    }
  }
}
```
![image](https://user-images.githubusercontent.com/40323661/215909487-09059ad1-99d0-4216-a21e-cd557c75cc97.png)

## Set Interface



* A Set is a Collection that **cannot contain duplicate elements**. 
* There are three main implementations of Set interface: 
     * HashSet, 
     * TreeSet, and 
     * LinkedHashSet.

#### HashSet

* The important points about Java HashSet class are:
	* HashSet stores the elements by using a mechanism called hashing.
	* HashSet contains unique elements only.
	* HashSet allows null value.
	* HashSet class is non synchronized.
	* HashSet doesn't maintain the insertion order. Here, elements are inserted on the basis of their hashcode.
	* HashSet is the best approach for search operations.
	* The initial default capacity of HashSet is 16, and the load factor is 0.75.

```java
public static void main(String args[]){  
  HashSet<String> set=new HashSet<String>();  
           set.add("Ravi");  
           set.add("Vijay");  
           set.add("Arun");  
           set.add("Sumit");  
           System.out.println("An initial list of elements: "+set);  
           //Removing specific element from HashSet  
           set.remove("Ravi");  
           System.out.println("After invoking remove(object) method: "+set);  
           HashSet<String> set1=new HashSet<String>();  
           set1.add("Ajay");  
           set1.add("Gaurav");  
           set.addAll(set1);  
           System.out.println("Updated List: "+set);  
           //Removing all the new elements from HashSet  
           set.removeAll(set1);  
           System.out.println("After invoking removeAll() method: "+set);  
           //Removing elements on the basis of specified condition  
           set.removeIf(str->str.contains("Vijay"));    
           System.out.println("After invoking removeIf() method: "+set);  
           //Removing all the elements available in the set  
           set.clear();  
           System.out.println("After invoking clear() method: "+set);  
 }  
}  

```

#### LinkedHashSet

* Java LinkedHashSet class is a Hashtable and Linked list implementation of the Set interface. It inherits the HashSet class and implements the Set interface.

* The important points about the Java LinkedHashSet class are:

* Java LinkedHashSet class contains unique elements only like HashSet.
* Java LinkedHashSet class provides all optional set operations and permits null elements.
* Java LinkedHashSet class is non-synchronized.
* Java LinkedHashSet class maintains insertion order.

![image](https://user-images.githubusercontent.com/40323661/215910882-21f4dfb2-9b15-4aa6-af72-c1847020b345.png)

* Example

```java
import java.util.*;
public class JavaExample{
  public static void main(String args[]){
    LinkedHashSet<String> set=new LinkedHashSet<>();
    set.add("Paul");
    set.add("Ram");
    set.add("Aaron");
    set.add("Leo");
    set.add("Becky");

    Iterator<String> it=set.iterator();
    while(it.hasNext()){
      System.out.println(it.next());
    }
  }
}
```
![image](https://user-images.githubusercontent.com/40323661/215911724-07c521a2-6350-4ffa-9680-7c3961228263.png)

#### TreeSet 

* The important points about the Java TreeSet class are:
	* Java TreeSet class contains unique elements only like HashSet.
	* Java TreeSet class access and retrieval times are quiet fast.
	* Java TreeSet class doesn't allow null element.
	* Java TreeSet class is non synchronized.
	* Java TreeSet class maintains ascending order.
	* Java TreeSet class contains unique elements only like HashSet.
	* Java TreeSet class access and retrieval times are quite fast.
	* Java TreeSet class doesn't allow null elements.
	* Java TreeSet class is non-synchronized.
	* Java TreeSet class maintains ascending order.
	* The TreeSet can only allow those generic types that are comparable. For example The Comparable interface is being implemented by the StringBuffer class.

```java
import java.util.*;
public class JavaExample{
  public static void main(String args[]){
    TreeSet<String> set=new TreeSet<>();
    set.add("Paul");
    set.add("Ram");
    set.add("Aaron");
    set.add("Leo");
    set.add("Becky");

    Iterator<String> it=set.iterator();
    while(it.hasNext()){
      System.out.println(it.next());
    }
  }
}

```

![image](https://user-images.githubusercontent.com/40323661/215912784-f49b9eae-1dcf-4b99-944e-63483a35c90a.png)


#### When to use HashSet, LinkedHashSet, and TreeSet:

* **Use HashSet:** When there is no need to keep any order in elements but group of unique objects is needed.
* **Use LinkedHashSet:** When group of unique elements is needed and insertion order of elements is also required.
* **Use TreeSet:** When group of unique items/elements/objects is needed and sorting of the elements is required according to some Comparator.

#### Differences Between HashSet, LinkedHashSet and TreeSet In Java :

 usyecase    HashSet	LinkedHashSet	TreeSet

**Considering-Points** | **HashSet** | **LinkedHashSet** | **TreeSet**
--------------|----------------|----------------|---------------
How they work internally? |HashSet uses HashMap internally to store it’s elements. | LinkedHashSet uses  LinkedHashMap internally to store it’s elements. | TreeSet uses TreeMap internally to store it’s elements.
Order Of Elements |HashSet doesn’t maintain any order of elements. |LinkedHashSet maintains insertion order of elements. i.e elements are placed as they are inserted.| TreeSet orders the elements according to supplied Comparator. If no comparator is supplied, elements will be placed in their natural ascending order.
Performance |HashSet gives better performance than the LinkedHashSet and TreeSet.| The performance of LinkedHashSet is between HashSet and TreeSet. It’s performance is almost similar to HashSet. But slightly in the slower side as it also maintains LinkedList internally to maintain the insertion order of elements. | TreeSet gives less performance than the HashSet and LinkedHashSet as it has to sort the elements after each insertion and removal operations.
How they work internally? |HashSet uses HashMap internally to store it’s elements. | LinkedHashSet uses  LinkedHashMap internally to store it’s elements. | TreeSet uses TreeMap internally to store it’s elements.















