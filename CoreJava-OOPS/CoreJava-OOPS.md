# CoreJava-OOPS


* OOP stands for Object-Oriented Programming.

![image](https://user-images.githubusercontent.com/40323661/213327737-2eac1b5f-5f5a-4f8c-9741-3a63dda6d56d.png)


* **OOPS is about developing an application around its data, i.e. objects which provides the access to their properties and the possible operations in their own way.**

* Procedural programming is about writing procedures or methods that perform operations on the data, while object-oriented programming is about creating objects that contain both data and methods.

* Object-oriented programming has several advantages over procedural programming:

   *  OOP is faster and easier to execute
   *  OOP provides a clear structure for the programs
   *  OOP helps to keep the Java code DRY "Don't Repeat Yourself", and makes the code easier to maintain, modify and debug
   *  OOP makes it possible to create full reusable applications with less code and shorter development time


*  **Encapsulation**
*  **Abstraction**
*  **Inheritance**
*  **Polymorphism**

#### What is a Constructor ?

* Constructor looks like a method but it is in fact not a method. It’s name is same as class name and it does not return any value. You must have seen this statement in almost all the programs I have shared above:
```java
MyClass obj = new MyClass();
```
* If you look at the right side of this statement, we are calling the default constructor of class myClass to create a new object (or instance).

* We can also have parameters in the constructor, such constructors are known as parametrized constructors.

* Example of constructor
```java
public class ConstructorExample {

   int age;
   String name;
	
   //Default constructor
   ConstructorExample(){
	this.name="Chaitanya";
	this.age=30;
   }
	
   //Parameterized constructor
   ConstructorExample(String n,int a){
	this.name=n;
	this.age=a;
   }
   public static void main(String args[]){
	ConstructorExample obj1 = new ConstructorExample();
	ConstructorExample obj2 = 
		       new ConstructorExample("Steve", 56);
	System.out.println(obj1.name+" "+obj1.age);
	System.out.println(obj2.name+" "+obj2.age);
   }
}
```
**Output:**
```java
Chaitanya 30
Steve 56
```

### Encapsulation
* Encapsulation allows us to protect the data stored in a class from system-wide access. As its name suggests, it safeguards the internal contents of a class like a real-life capsule. You can implement encapsulation in Java by keeping the fields (class variables) private and providing public getter and setter methods to each of them. Java Beans are examples of fully encapsulated classes.

![Encapsulation](https://media.geeksforgeeks.org/wp-content/uploads/Encapsulation.jpg "Encapsulation")

* Encapsulation in Java:
  * Restricts direct access to data members (fields) of a class.
  * Fields are set to private
  * Each field has a getter and setter method
  * Getter methods return the field
  * Setter methods let us change the value of the field

* With encapsulation, you can protect the fields of a class. To do so, declare the fields as private and providing access to them with getter and setter methods.

* The Animal class below is fully encapsulated. It has three private fields and each of them has its own set of getter and setter methods.

```Java
class Animal {
	private String name;
	private double averageWeight;
	private int numberOfLegs;

	// Getter methods
	public String getName() {
		return name;
	}
	public double getAverageWeight() {
		return averageWeight;
	}
	public int getNumberOfLegs() {
		return numberOfLegs;
	}

	// Setter methods
	public void setName(String name) {
		this.name = name;
	}
	public void setAverageWeight(double averageWeight) {
		this.averageWeight = averageWeight;
	}
	public void setNumberOfLegs(int numberOfLegs) {
		this.numberOfLegs = numberOfLegs;
	}
}
```
* The TestAnimal class first sets a value for each field with the setter methods, then prints out the values using the getter methods.
```Java
public class TestAnimal {
	public static void main(String[] args) {
		Animal myAnimal = new Animal();

		myAnimal.setName("Eagle");
		myAnimal.setAverageWeight(1.5);
		myAnimal.setNumberOfLegs(2);

		System.out.println("Name: " + myAnimal.getName());
		System.out.println("Average weight: " + myAnimal.getAverageWeight() + "kg");
		System.out.println("Number of legs: " + myAnimal.getNumberOfLegs());
	}
}
```
* As you can see below, the Java console returns properly all the values you set with the setter methods:
```Console
[Console output of TestAnimal]
Name: Eagle
Average weight: 1.5kg
Number of legs: 2
```

##### 1) Abstraction

* Abstraction is a process where you show only “relevant” data and “hide” unnecessary details of an object from the user. 
* For example, when you login to your bank account online, you enter your user_id and password and press login, what happens when you press login, how the input data sent to server, how it gets verified is all abstracted away from the you. 

* Another example of abstraction: A car in itself is a well-defined object, which is composed of several other smaller objects like a gearing system, steering mechanism, engine, which are again have their own subsystems. But for humans car is a one single object, which can be managed by the help of its subsystems, even if their inner details are unknown.

Example:
```java
// An example abstract class in Java 
abstract class Shape { 
    int color; 
  
    abstract void draw();  
} 
```

#### Abstract Class 

* **Points to Remember**

* A class which contains the abstract keyword in its declaration is known as abstract class.
* Abstract classes may or may not contain abstract methods, i.e., methods without body ( public void get(); )
* But, if a class has at least one abstract method, then the class must be declared abstract.
* If a class is declared abstract, it cannot be instantiated.
* To use an abstract class, you have to inherit it from another class, provide implementations to the abstract methods in it.
* If you inherit an abstract class, you have to provide implementations to all the abstract methods in it.
* It can have constructors and static methods also.
* It can have final methods which will force the subclass not to change the body of the method.

#### Ways to achieve Abstraction
* There are two ways to achieve abstraction in java
  * 1.Abstract class (0 to 100%)
  * 2.Interface (100%)

* Abstract class in Java

A class which is declared as abstract is known as an abstract class. It can have abstract and non-abstract methods. It needs to be extended and its method implemented. It cannot be instantiated.

#### 1) Example of Abstract class that has an abstract method

* In this example, Bike is an abstract class that contains only one abstract method run. Its implementation is provided by the Honda class.

```java
abstract class Bike{  
	abstract void run();  
} 

class Honda4 extends Bike { 
  void run()
  {
  System.out.println("running safely");
  }  

public static void main(String args[]){  
  Bike obj = new Honda4();  
  obj.run();  
 }  
}  
```
OutPut
```Console
running safely
```
#### 2) Understanding the real scenario of Abstract class

* In this example, Shape is the abstract class, and its implementation is provided by the Rectangle and Circle classes.

* In this example, if you create the instance of Rectangle class, draw() method of Rectangle class will be invoked.

```java

abstract class Shape{  
 abstract void draw();  
 }  
 
 //In real scenario, implementation is provided by others i.e. unknown by end user  
 class Rectangle extends Shape{  
 void draw(){
 System.out.println("drawing rectangle");
 }  
 }


class Circle1 extends Shape{  
void draw(){
System.out.println("drawing circle");
}  
}  
//In real scenario, method is called by programmer or user  
class TestAbstraction1{  
public static void main(String args[]){  
Shape s=new Circle1();//In a real scenario, object is provided through method, e.g., getShape() method  
s.draw();  
}  
}
```
```Console
drawing circle
```
#### 3) Another example of Abstract class in java

```java
abstract class Bank{    
abstract int getRateOfInterest();    
} 

class SBI extends Bank{    
int getRateOfInterest(){return 7;}    
}   

class PNB extends Bank{    
int getRateOfInterest(){return 8;}    
}    

    
class TestBank{    
public static void main(String args[]){    
Bank b;  
b=new SBI();  
System.out.println("Rate of Interest is: "+b.getRateOfInterest()+" %");    
b=new PNB();  
System.out.println("Rate of Interest is: "+b.getRateOfInterest()+" %");    
}}    
```
```Console
Rate of Interest is: 7 %
Rate of Interest is: 8 %
```
#### 4) Abstract class having constructor, data member and methods

```java
//Example of an abstract class that has abstract and non-abstract methods  
abstract class Bike{  
   Bike(){System.out.println("bike is created");}  
   abstract void run();  
   void changeGear(){System.out.println("gear changed");}  
 }  
//Creating a Child class which inherits Abstract class  
 class Honda extends Bike{  
 void run(){System.out.println("running safely..");}  
 }  

//Creating a Test class which calls abstract and non-abstract methods  
class TestAbstraction2{  
 public static void main(String args[]){  
 Bike obj = new Honda();  
obj.run();  
 obj.changeGear();  
 }  
}  

```
Output
```Console
 bike is created
 running safely..
 gear changed
```
##### 2) Interface

* Interface looks like a class but it is not a class. 
* An interface can have methods and variables just like the class but the methods declared in interface are by default abstract.
* The variables declared in an interface are public, static & final by default. 

* The interface in Java is a mechanism to achieve abstraction. There can be only abstract methods in the Java interface, not method body. It is used to achieve abstraction and multiple inheritance in Java.

* It cannot be instantiated just like the abstract class.
* **Since Java 8, we can have default and static methods in an interface.**
* **Since Java 9, we can have private methods in an interface.**

##### Why use Java interface?

* There are mainly three reasons to use interface. They are given below.
  * It is used to achieve abstraction.
  * By interface, we can support the functionality of multiple inheritance.
  * It can be used to achieve loose coupling.
  
* **What is the difference between abstract class and interface ?**

**Abstract class** | **Interface**
------------ | -------------
Abstract class can have abstract and non-abstract methods | Interface can have only abstract methods. Since Java 8, it can have default and static methods also.
Abstract class doesn't support multiple inheritance	| Interface supports multiple inheritance.
Abstract class can have final, non-final, static and non-static variables.	| Interface has only static and final variables.
Abstract class can provide the implementation of interface.	| Interface can't provide the implementation of abstract class.
The abstract keyword is used to declare abstract class.	| The interface keyword is used to declare interface.
An abstract class can extend another Java class and implement multiple Java interfaces.	| An interface can extend another Java interface only.
An abstract class can be extended using keyword "extends".	| An interface can be implemented using keyword "implements".
A Java abstract class can have class members like private, protected, etc.	| Members of a Java interface are public by default.
public abstract class Shape{ public abstract void draw(); }	| public interface Drawable{ void draw(); }

### Interfaces

* An interface is a 100% abstract class. It can have only static, final, and public fields and abstract methods. It’s frequently referred to as a blueprint of a class as well. Java interfaces allow us to implement multiple inheritance in our code, as a class can implement any number of interfaces. Classes can access an interface using the implements keyword.

* In the example, define two interfaces, Animal and Bird. Animal has two abstract methods, while Bird has two static fields and an abstract method.

```Java
interface Animal {
	public void eat();
	public void sound();
}

interface Bird {
	int numberOfLegs = 2;
	String outerCovering = "feather";

	public void fly();
}
```
The class Eagle implements both interfaces. It defines its own functionality for the three abstract methods. The eat() and sound() methods come from the Animal class, while fly() comes from Bird.
```Java
class Eagle implements Animal, Bird {
	public void eat() {
		System.out.println("Eats reptiles and amphibians.");
	}
	public void sound() {
		System.out.println("Has a high-pitched whistling sound.");
	}
	public void fly() {
		System.out.println("Flies up to 10,000 feet.");
	}
}
```
* In the TestEagle test class, instantiate a new Eagle object (called myEagle) and print out all the fields and methods to the console.
* As static fields don’t belong to a specific object but to a whole class, you need to access them from the Bird interface instead of the myEagle object.
```Java
class TestEagle {
	public static void main(String[] args) {
		Eagle myEagle = new Eagle();

		myEagle.eat();
		myEagle.sound();
		myEagle.fly();

		System.out.println("Number of legs: " + Bird.numberOfLegs);
		System.out.println("Outer covering: " + Bird.outerCovering);
	}
}
```
The Java console returns all the information you wanted to access:
```Console
[Console output of TestEagle]
Eats reptiles and amphibians.
Has a high-pitched whistling sound.
Flies up to 10,000 feet.
Number of legs: 2
Outer covering: feather
```

### Inheritance

* Inheritance allows us to extend a class with child classes that inherit the fields and methods of the parent class. It’s an excellent way to achieve code reusability. In Java, we need to use the extends keyword to create a child class.

* In the example, the Eagle class extends the Bird parent class. It inherits all of its fields and methods, plus defines two extra fields that belong only to Eagle.
```Java
class Bird {
	public String reproduction = "egg";
	public String outerCovering = "feather";

	public void flyUp() {
		System.out.println("Flying up...");
	}
	public void flyDown() {
		System.out.println("Flying down...");
	}
}

class Eagle extends Bird {
	public String name = "eagle";
	public int lifespan = 15;
}
```
* The TestEagle class instantiates a new Eagle object and prints out all the information (both the inherited fields and methods and the two extra fields defined in the Eagle class).
```Java
class TestEagle {
	public static void main(String[] args) {		
		Eagle myEagle = new Eagle();

		System.out.println("Name: " + myEagle.name); 			
		System.out.println("Reproduction: " + myEagle.reproduction);
		System.out.println("Outer covering: " + myEagle.outerCovering);
		System.out.println("Lifespan: " + myEagle.lifespan); 		
		myEagle.flyUp();
		myEagle.flyDown(); 		
	}
}
```
* You can see the console output below:
```Console
[Console output of TestEagle]
Reproduction: another egg
Outer covering: feather
Lifespan: 15
Flying up...
Flying down...
```

### Polymorphism

* Polymorphism makes it possible to use the same entity in different forms. In Java, this means that you can declare several methods with the same name until they are different in certain characteristics. Java provides us with two ways to implement polymorphism: method overloading and method overriding.

**Static polymorphism:**

* Method overloading means that you can have several methods with the same name within a class. However, the number, names, or types of their parameters need to be different.

* For example, the Bird() class below has three fly() methods. The first one doesn’t have any parameters, the second one has one parameter (height), and the third one has two parameters (name and height).
```Java
class Bird {
	public void fly() {
		System.out.println("The bird is flying.");
	}
	public void fly(int height) {
		System.out.println("The bird is flying " + height + " feet high.");
	}
	public void fly(String name, int height) {
		System.out.println("The " + name + " is flying " + height + " feet high.");
	}
}
```
* The test class instantiates a new Bird object and calls the fly() method three times. Firstly, without parameters, secondly, with one integer parameter for height, and thirdly, with two parameters for name and height.
```Java
class TestBird {
	public static void main(String[] args) {
		Bird myBird = new Bird();

		myBird.fly();
		myBird.fly(10000);
		myBird.fly("eagle", 10000);
	}
}
```
* In the console, we can see that Java could have differentiated the three polymorphic fly() methods:
```Java
[Console output of TestBird]
The bird is flying.
The bird is flying 10000 feet high.
The eagle is flying 10000 feet high.
```

**Dynamic polymorphism:**

* By using the method overriding feature of Java, you can override the methods of a parent class from its child class.

* The Bird class extends the Animal class in the example below. Both have an eat() method. By default, Bird inherits its parent’s eat() method. However, as it also defines its own eat() method, Java will override the original method and call eat() from the child class.

```Java
class Animal {
	public void eat() {
		System.out.println("This animal eats insects.");
	}
}

class Bird extends Animal {

	public void eat() {
		System.out.println("This bird eats seeds.");
	}

}
```
* The TestBird class first instantiates a new Animal object and calls its eat() method. Then, it also creates a Bird object and calls the polymorphic eat() method again.
```Java
class TestBird {
	public static void main(String[] args) {
		Animal myAnimal = new Animal();
		myAnimal.eat();

		Bird myBird = new Bird();
		myBird.eat();
	}
}
```
* The console returns the values of the relevant methods properly. Therefore Java could have differentiated the two eat() methods indeed.
```Console
[Console output of TestBird]
This animal eats insects.
This bird eats seeds.
```

