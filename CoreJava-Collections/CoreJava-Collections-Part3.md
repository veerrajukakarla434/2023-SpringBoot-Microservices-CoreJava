## Java Map Interface

![image](https://user-images.githubusercontent.com/40323661/216831626-f31a518e-a6eb-4a8d-ac9e-236c206b24de.png)


* In Java, elements of Map are stored in key/value pairs. Keys are unique values associated with individual Values.
* A map cannot contain duplicate keys. And, each key is associated with a single value.

![image](https://user-images.githubusercontent.com/40323661/216831491-df128579-6d0e-432a-853a-a3e26b6d7475.png)

**Note: ** The Map interface maintains 3 different sets:

  * the set of keys
  * the set of values
  * the set of key/value associations (mapping).
  * Hence we can access keys, values, and associations individually.

* Since Map is an interface you need to instantiate a concrete implementation of the Map interface in order to use it. The Java Collections API contains the following Map implementations:
    * java.util.HashMap
    * java.util.Hashtable
    * java.util.EnumMap
    * java.util.IdentityHashMap
    * java.util.LinkedHashMap
    * java.util.Properties
    * java.util.TreeMap
    * java.util.WeakHashMap

* **Map interface provides a set of methods that must be implemented**. In this section, we will discuss the most famous methods:

* **clear:** Removes all the elements from the map.
* **containsKey:** Returns true if the map contains the requested key.
* **containsValue:** Returns true if the map contains the requested value.
* **equals:** Compares an Object with the map for equality.
* **get:** Retrieve the value of the requested key.
* **entrySet:** Returns a Set view of the mappings contained in this map.
* **keySet:** Returns a Set that contains all keys of the map.
* **put:** Adds the requested key-value pair in the map.
* **remove:** Removes the requested key and its value from the map, if the key exists.
* **size:** Returns the number of key-value pairs currently in the map.

* **HashMap** is the implementation of Map, but it doesn't maintain any order.
* **LinkedHashMap**	 is the implementation of Map. It inherits HashMap class. It maintains insertion order.
* **TreeMap**  is the implementation of Map and SortedMap. It maintains ascending order.

![image](https://user-images.githubusercontent.com/40323661/216832666-293b560e-7e38-4bae-ad6a-6ce0c5c141e4.png)

#### HashMapExample.java:

```java
public class HashMapExample {
 
    public static void main(String[] args) {
        Map<String, Integer> vehicles = new HashMap<>();
 
        // Add some vehicles.
        vehicles.put("BMW", 5);
        vehicles.put("Mercedes", 3);
        vehicles.put("Audi", 4);
        vehicles.put("Ford", 10);
 
        System.out.println("Total vehicles: " + vehicles.size());
 
        // Iterate over all vehicles, using the keySet method.
        for (String key : vehicles.keySet())
            System.out.println(key + " - " + vehicles.get(key));
        System.out.println();
 
        String searchKey = "Audi";
        if (vehicles.containsKey(searchKey))
            System.out.println("Found total " + vehicles.get(searchKey) + " " + searchKey + " cars!\n");
 
        // Clear all values.
        vehicles.clear();
 
        // Equals to zero.
        System.out.println("After clear operation, size: " + vehicles.size());
    }
}

```

* OUTPUT:

```java
Total vehicles: 4
Audi - 4
Ford - 10
BMW - 5
Mercedes - 3
Found total 4 Audi cars!
After clear operation, size: 0
```

```java
import java.util.*;  
class MapExample2{  
 public static void main(String args[]){  
  Map<Integer,String> map=new HashMap<Integer,String>();  
  map.put(100,"Amit");  
  map.put(101,"Vijay");  
  map.put(102,"Rahul");  
  //Elements can traverse in any order  
  for(Map.Entry m:map.entrySet()){  
   System.out.println(m.getKey()+" "+m.getValue());  
  }  
 }  
}  

```
* OUTPUT:

```java
102 Rahul
100 Amit
101 Vijay
```

```java
import java.util.LinkedHashMap;

class Main {
    public static void main(String[] args) {
        // Creating a LinkedHashMap of even numbers
        LinkedHashMap<String, Integer> evenNumbers = new LinkedHashMap<>();
        evenNumbers.put("Two", 2);
        evenNumbers.put("Four", 4);
        System.out.println("LinkedHashMap1: " + evenNumbers);

        // Creating a LinkedHashMap from other LinkedHashMap
        LinkedHashMap<String, Integer> numbers = new LinkedHashMap<>(evenNumbers);
        numbers.put("Three", 3);
        System.out.println("LinkedHashMap2: " + numbers);
    }
}

```
* OUTPUT:

```java
LinkedHashMap1: {Two=2, Four=4}
LinkedHashMap2: {Two=2, Four=4, Three=3}
```

#### Access LinkedHashMap Elements
* 1. Using entrySet(), keySet() and values()

* **entrySet()** - returns a set of all the key/value mapping of the map
* **keySet()** - returns a set of all the keys of the map
* **values()** - returns a set of all the values of the map

```java
import java.util.LinkedHashMap;

class Main {
    public static void main(String[] args) {
        LinkedHashMap<String, Integer> numbers = new LinkedHashMap<>();

        numbers.put("One", 1);
        numbers.put("Two", 2);
        numbers.put("Three", 3);
        System.out.println("LinkedHashMap: " + numbers);

        // Using entrySet()
        System.out.println("Key/Value mappings: " + numbers.entrySet());

        // Using keySet()
        System.out.println("Keys: " + numbers.keySet());

        // Using values()
        System.out.println("Values: " + numbers.values());
    }
}

```
* OUTPUT:
```java
LinkedHashMap: {One=1, Two=2, Three=3}
Key/Value mappings: [One=1, Two=2, Three=3]
Keys: [One, Two, Three]
Values: [1, 2, 3]
```


* **Treemap Example**

```java
import java.util.TreeMap;

class Main {
    public static void main(String[] args) {
        // Creating TreeMap of even numbers
        TreeMap<String, Integer> evenNumbers = new TreeMap<>();

        // Using put()
        evenNumbers.put("Two", 2);
        evenNumbers.put("Four", 4);

        // Using putIfAbsent()
        evenNumbers.putIfAbsent("Six", 6);
        System.out.println("TreeMap of even numbers: " + evenNumbers);

        //Creating TreeMap of numbers
        TreeMap<String, Integer> numbers = new TreeMap<>();
        numbers.put("One", 1);

        // Using putAll()
        numbers.putAll(evenNumbers);
        System.out.println("TreeMap of numbers: " + numbers);
    }
}

```
* OUTPUT:
```java
TreeMap of even numbers: {Four=4, Six=6, Two=2}
TreeMap of numbers: {Four=4, One=1, Six=6, Two=2}
```

#### Difference between TreeMap, HashMap, and LinkedHashMap in Java

* **HashMap**
   * HashMap has complexity of O(1) for insertion and lookup.
   * HashMap allows one null key and multiple null values.
   * HashMap does not maintain any order.

* **LinkedHashMap**
  * LinkedHashMap has complexity of O(1) for insertion and lookup.
  * LinkedHashMap allows one null key and multiple null values.
  * LinkedHashMap maintains order in which key-value pairs are inserted.

* **TreeMap**
  * TreeMap has complexity of O(logN) for insertion and lookup.
  * TreeMap does not allow null key but allow multiple null values.
  * TreeMap maintains order. It stores keys in sorted and ascending order.

#### ConcurrentModificationException in Java

* **For Example** - It is not permissible for a thread to modify a Collection when some other thread is iterating over it. This is because the result of the iteration becomes undefined with it. Some implementation of the Iterator class throws this exception, including all those general-purpose implementations of Iterator which are provided by the JRE. Iterators which do this are called fail-fast as they throw the exception quickly as soon as they encounter such situation rather than facing undetermined behavior of the collection any time in the future.


```java
import java.awt.List;  
import java.util.*;  
  
public class Concurrentmodificationexception {  
  
    public static void main(String[] args) {  
        ArrayList<Integer> list = new ArrayList<>();  
  
        list.add(1);  
        list.add(2);  
        list.add(3);  
        list.add(4);  
        list.add(5);  
  
        Iterator<Integer> it = list.iterator();  
        while (it.hasNext()) {                   
Integer value = it.next();              
            System.out.println("List Value:" + value);  
            if (value.equals(3))  
                list.remove(value);  
        }  
  
    }  
  
}  

```


```java
import java.awt.List;  
import java.util.*;  
  
public class concurrentmodificationexception {  
  
    public static void main(String[] args) {  
          
        HashMap<Integer, Integer> map = new HashMap<>();  
        map.put(1, 1);  
        map.put(2, 2);  
        map.put(3,3);  
          
        Iterator<Integer> it = map.keySet().iterator();  
        while(it.hasNext()) {  
            Integer key = it.next();  
            System.out.println("Map Value:" + map.get(key));  
            if (key.equals(2)) {  
                map.put(1, 4);  
            }  
        }     
    }  
}  
```

