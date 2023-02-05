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

