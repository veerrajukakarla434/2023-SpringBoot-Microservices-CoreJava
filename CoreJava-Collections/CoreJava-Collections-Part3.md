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


