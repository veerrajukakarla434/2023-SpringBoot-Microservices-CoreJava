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

