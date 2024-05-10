# Java Collection Framework and Java Generics
📁 This file, contains all possible concepts of Java Collection Frameworks and Java Generics in detail.

# 1. Java Generics: 
**i. Elimination of casts.**
<br>
**The following code snippet without generics requires casting:**
```java
List list = new ArrayList();
list.add("hello");
String s = (String) list.get(0);
```

**When re-written to use generics, the code does not require casting:**
```java
List<String> list = new ArrayList<String>();
list.add("hello");
String s = list.get(0);   // no cast
```

**ii. We can decide on the object type later**
```java
class SampleClass {
	public static void main(String[] args) {
		Test<Integer> obj1 = new Test<Integer>(10);
		System.out.println(obj1.getObject());

		Test<String> obj2 = new Test<String>("AkashChauhan");
		System.out.println(obj2.getObject());
	}
}

//We use <T> to specify Parameter type
class Test<T> {

	// An object of type T is declared
	T a;

	// constructor
	Test(T b) {
		this.a = b;
	}

	T getObject() {
		return this.a;
	}

}
```

# 2. Java Collection Framework:

## Questions to think about:
- [x] Why do we need, collection or the purpose of using collection interfaces?
- [x] why this order, Indiviual{1st level}->Arrays{2nd level}->Collection{3rd level}, is important?
- [x] What are the disadvantages of creating Individual Elements?
- [x] What are the advantages of Array?
- [x] What are the disadvantages of Array?
- [x] What are the advantages of using collection interfaces?
- [x] What are List, Set, and Queue interfaces?
- [x] What are the different types of implementation classes of the above interfaces?

## Important Concepts (Bullet Points):

> [!NOTE]
> 1. When using Individual Element {Problems-1}
  * When creating 10000 variables, it is not good practice to create 1000 different individual variables
  * So array comes into the picture {Array can represent many values using a single variable}

> [!NOTE]
> 2. When using Array {Problems-2}
  * Fix in Size -> It is compulsory to provide the size during compilation, or before using it.
  * Only Homogeneous -> Holds only homogeneous data type elements {but Can we resolved by using object array}
  * We are always responsible for making our methods {Array is not based on some standard data structure, so readymade methods support is not there}

> [!NOTE]
> 3. When using Collection {Benefits, to overcome above problems}
  * Growable in nature -> Not bound to fix the size at starting
  - Homogeneous + Hetrogeneoud {$Hetrogeneous Objects Collection}
  - Can use Readymade methods from standard DS
```java
public class SampleClass {

	@SuppressWarnings({ "unchecked", "rawtypes" })
	public static void main(String[] args) {
		ArrayList al = new ArrayList();
		al.add(1);
		al.add("abc");
		al.add(new String("def"));
		System.out.println(al);
	}

}
```

> [!important]
> 1. A Collection represents a single unit of objects.
> 2. The Collection interface (java.util.Collection) and Map interface (java.util.Map) are the two main “root” interfaces of Java collection classes.
> 3. Java Collections can achieve all the operations, you perform on data such as searching, sorting, insertion, manipulation, and deletion without writing boilerplate code.
> 4. It provides readymade architecture/Classes/methods.


## Java Collection Framework
It is a collection of collection classes and map classes. It is also called the Java Collection framework. <br>
**1. Collection Interface (Their Implementation Classes)** <br>
**2. Map Interface (Their Implementation Classes)**

![image](https://github.com/AkashChauhanSoftEngi/Java_Programming_Practice/assets/23252844/1d6b27ec-d91d-458f-b05f-98b81a906ba1)

## 1. Collection Interface
> 1. List <br>
> 2. Set <br>
> 3. Queue

![2  Collection Hierarchy](https://github.com/AkashChauhanSoftEngi/Java_Programming_Practice/assets/23252844/2cfc9741-8e19-4c31-ad23-ef08daf82ce7)

## Main Interfaces that extend Collection Interface
> 1. List\<E\>
> 2. Set\<E\>
> 3. Queue\<E\>

| S.No | Inteface  | Description |
| ---- | ------------- | ------------- |
| 1 | List\<E\>  | . It is an ordered collection of objects. <br> . In which duplicate values can be stored. <br> . Multiple Null Values are allowed. |
| 2 | Set\<E\>  | . It is an unordered collection of objects. <br> . In which duplicate values cannot be stored. <be> . At most one null value. |
| 3 | Queue\<E\>  | . Ordered, FIFO, Allows duplicates, Allows multiple null values. |

> [!important]
> 1. All these Collections, List<E>, Set<E>, and Queue<E> are interfaces.
> 2. So we can not directly make the object out of these
> 3. We have to use, implementation classes of these interfaces to access the readymade methods provided by these classes.
> 4. You can find these interfaces and classes under java.util package.

## 1.1 List\<E\> Interface and its implementation classes:
| S.No | Implementation Classes of List\<E\> Interface  | Description |
| ---- | ------------- | ------------- |
|1| ArrayList\<E\> | . The ArrayList class is a re-sizable array. <br> . In ArrayList accessing an element takes constant time O(1) {Fast random access} and adding an element takes O(n) time in the worst case(adding an item at the first position). <br> . Adding elements in between would cost more space, as shifting the rest of the elements would take place. |
|2| LinkedList\<E\> | . LinkedList adding an element takes O(n) time(at the end of the list) and accessing also takes O(n) time. <br> . LinkedList uses more memory than ArrayList because of extra overhead for the next and previous pointers for each node in the linked list. <br> . It is not synchronized. |
|3| Vector\<E\> | . The size of a {@code Vector} can grow or shrink as needed to accommodate. <br> . It is recommended to use the Vector class in the thread-safe implementation only. If you don't need to use the thread-safe implementation, you should use the ArrayList {Vector is synchronized}. |
|4| Stack\<E\> | . Stack is an ordered list. <br> . In which, insertion and deletion can be performed only at one end is called the top (LIFO). |

### 1. Code for ArrayList\<E\>
```java
public class SampleClass {

	public static void main(String[] args) {
		List<Integer> l1 = new ArrayList<Integer>();
		l1.add(0, 1); 
		l1.add(1, 2); 
		l1.add(2, 2);
		l1.add(3, null);
		l1.add(4, null);
		
		System.out.println(l1);

		// Creating another list
		List<Integer> l2 = new ArrayList<Integer>();
		l2.add(3);
		l2.add(4);
		l2.add(5);

		// Will add list l2 from 5 index
		l1.addAll(5, l2);
		System.out.println(l1);

		// Removes element from index 1
		l1.remove(2);
		System.out.println(l1);

		// Print element at index 3
		System.out.println(l1.get(3));

		// Replace 0th element with 5
		l1.set(0, 5);
		System.out.println(l1);
	}

}
```
### 2. Code for LinkedList\<E\>
```java
public class SampleClass {

	public static void main(String[] args) {
		
		// Creating a list
		List<Integer> l1 = new LinkedList<Integer>();
		l1.add(0, 1); 
		l1.add(1, 2); 
		System.out.println(l1);

		// Creating another list
		List<Integer> l2 = new LinkedList<Integer>();
		l2.add(1);
		l2.add(2);
		l2.add(3);

		// Will add list l2 from 1 index
		l1.addAll(1, l2);
		System.out.println(l1);

		// Removes element from index 1
		l1.remove(1);
		System.out.println(l1); // [1, 2, 3, 2]

		// Prints element at index 3
		System.out.println(l1.get(3));

		// Replace 0th element with 5
		l1.set(0, 5);
		System.out.println(l1);
	}
}
```

### 3. Code for Vector\<E\>
```java
public class SampleClass {

	public static void main(String[] args) {

		// Creating a list
		List<Integer> l1 = new Vector<Integer>();
		l1.add(0, 1);
		l1.add(1, 2);
		System.out.println(l1);

		// Creating another list
		List<Integer> l2 = new Vector<Integer>();
		l2.add(1);
		l2.add(2);
		l2.add(3);

		// Will add list l2 from 1 index
		l1.addAll(1, l2);
		System.out.println(l1);

		// Removes element from index 1
		l1.remove(1);
		System.out.println(l1);

		// Prints element at index 3
		System.out.println(l1.get(3));

		// Replace 0th element with 5
		l1.set(0, 5);
		System.out.println(l1);
	}
}
```

### 4. Code for Stack\<E\>
```java
public class SampleClass {

	public static void main(String[] args) {

		// Creating a list
		List<Integer> l1 = new Stack<Integer>();
		l1.add(0, 1);
		l1.add(1, 2);
		System.out.println(l1);

		// Creating another list
		List<Integer> l2 = new Stack<Integer>();
		l2.add(1);
		l2.add(2);
		l2.add(3);

		// Will add list l2 from 1 index
		l1.addAll(1, l2);
		System.out.println(l1);

		// Removes element from index 1
		l1.remove(1);
		System.out.println(l1);

		// Prints element at index 3
		System.out.println(l1.get(3));

		// Replace 0th element with 5
		l1.set(0, 5);
		System.out.println(l1);
	}

}
```

## 1.2 Set\<E\> Interface and its implementation classes:
| S.No | Implementation Classes of Set\<E\> Interface  | Description |
| ---- | ------------- | ------------- |
|1| HashSet\<E\> | . It uses HashMap. <br> . It does not guarantee that the Insertion order will remain constant over time. |
|2| LinkedShashSet\<E\> | . It uses a doubly-linked list. <br> . Preserve insertion order. |
|3| TreeSet\<E\> | . It is Sorted. <br> . No null value, not even one. |

### 1. Code for HashSet\<E\>
```java
public class SampleClass {

	public static void main(String[] args) {

		Set<String> hash_Set = new HashSet<String>();

		hash_Set.add("Amit");
		hash_Set.add("For");
		hash_Set.add("Amit");
		hash_Set.add("Example");
		hash_Set.add("Set");
		hash_Set.add(null);
		hash_Set.add(null);/* It would not make sense, as at most one null element is allowed */

		System.out.println("Set output without the duplicates");
		System.out.println(hash_Set);

		hash_Set.remove(null);

		System.out.println("\nSorted Set after passing into TreeSet");
		Set<String> tree_Set = new TreeSet<String>(hash_Set);
		System.out.println(tree_Set);
	}

}
```

### 2. Code for LinkedShashSet\<E\>
```java
public class SampleClass {

	public static void main(String[] args) {

		Set<String> hash_Set = new LinkedHashSet<String>();

		hash_Set.add("Amit");
		hash_Set.add("For");
		hash_Set.add("Amit");
		hash_Set.add("Example");
		hash_Set.add("Set");
		hash_Set.add(null);
		hash_Set.add(null);/* It would not make sense, as at most one null element is allowed */

		System.out.println("Set output without the duplicates");
		System.out.println(hash_Set);

		hash_Set.remove(null);

		System.out.println("\nSorted Set after passing into TreeSet");
		Set<String> tree_Set = new TreeSet<String>(hash_Set);
		System.out.println(tree_Set);
	}

}
```

### 3. Code for TreeSet\<E\>
```java
public class SampleClass {

	public static void main(String[] args) {

		// Set demonstration using HashSet
		Set<String> tree_Set = new TreeSet<String>();

		tree_Set.add("Amit");
		tree_Set.add("For");
		tree_Set.add("Amit");
		tree_Set.add("Example");
		tree_Set.add("Set");
		try {
			tree_Set.add(null);
		} catch (Exception e) {
			System.out.println("TreeSet would not allow to store null values, not even one!");
		}

		System.out.println("\nSet output without the duplicates");
		System.out.println(tree_Set);
	}

}
```

## 1.3 Queue\<E\> Interface and its implementation classes:
| S.No | Implementation Classes of Queue\<E\> Interface  | Description |
| ---- | ------------- | ------------- |
|1| PriorityQueue\<E\> | . order not preserved, allows duplicates, no null values, not thread safe |
|2| LinkedList\<E\> | . Not thread-safe, Allows duplicates, Allows multiple null values, preserved order |
|3| PriorityBlockingQueue\<E\> | . Thread Safety + PriorityQueue |
|4| LinkedBlockingQueue\<E\> | . Thread safe + allows duplicates, no null values, preserved order |

### 1. Code for PriorityQueue\<E\>
```java
public class SampleClass {

	public static void main(String[] args) {
		Queue<Integer> q = new PriorityQueue<Integer>();

		// Adds elements {0, 1, 2, 3, 4} to queue
		for (int i = 0; i < 5; i++)
			q.add(i);

		q.add(2);

		// Display contents of the queue.
		System.out.println("Elements of queue-" + q);

		// To remove the head of queue.
		int removedEle = q.remove();
		System.out.println("removed element-" + removedEle);

		System.out.println(q);

		// To view the head of queue
		int head = q.peek();
		System.out.println("head of queue-" + head);

		//Size of the queue
		int size = q.size();
		System.out.println("Size of queue-" + size);
	}

}
```

### 2. Code for LinkedList\<E\>
```java
public class SampleClass {

	public static void main(String[] args) {
		Queue<Integer> q = new LinkedList<Integer>();

		// Adds elements {0, 1, 2, 3, 4} to queue
		for (int i = 0; i < 5; i++)
			q.add(i);

		q.add(2);

		// Display contents of the queue.
		System.out.println("Elements of queue-" + q);

		// To remove the head of queue.
		int removedEle = q.remove();
		System.out.println("removed element-" + removedEle);

		System.out.println(q);

		// To view the head of queue
		int head = q.peek();
		System.out.println("head of queue-" + head);

		// Size of the queue
		int size = q.size();
		System.out.println("Size of queue-" + size);
	}

}
```

### 3. Code for PriorityBlockingQueue\<E\>
```java
public class SampleClass {

	public static void main(String[] args) {
		Queue<Integer> q = new PriorityBlockingQueue<Integer>();

		// Adds elements {0, 1, 2, 3, 4} to queue
		for (int i = 0; i < 5; i++)
			q.add(i);

		q.add(2);

		// Display contents of the queue.
		System.out.println("Elements of queue-" + q);

		// To remove the head of queue.
		int removedEle = q.remove();
		System.out.println("removed element-" + removedEle);

		System.out.println(q);

		// To view the head of queue
		int head = q.peek();
		System.out.println("head of queue-" + head);

		// Size of the queue
		int size = q.size();
		System.out.println("Size of queue-" + size);
	}

}
```

### 4. Code for LinkedBlockingQueue\<E\>
```java
public class SampleClass {

	public static void main(String[] args) {
		Queue<Integer> q = new LinkedBlockingQueue<Integer>();

		// Adds elements {0, 1, 2, 3, 4} to queue
		for (int i = 0; i < 5; i++)
			q.add(i);

		q.add(2);

		// Display contents of the queue.
		System.out.println("Elements of queue-" + q);

		// To remove the head of queue.
		int removedEle = q.remove();
		System.out.println("removed element-" + removedEle);

		System.out.println(q);

		// To view the head of queue
		int head = q.peek();
		System.out.println("head of queue-" + head);

		// Size of the queue
		int size = q.size();
		System.out.println("Size of queue-" + size);
	}

}
```

## 2. Map Interface
> 1. SortedMap <br>
> 2. NavigableMap

![image](https://github.com/AkashChauhanSoftEngi/Java_Programming_Practice/assets/23252844/3dd6a8e1-fe4e-42f3-8452-3bed7cd5750c)

## 2.1 Map\<E\> Interface and its implementation classes:
> 1. Map stores unique elements. If similar value will be inserted then overwritten value will be considered.
> 2. The order of elements is unpreserved by default.

| S.No | Implementation Classes of Map\<E\> Interface  | Description |
| ---- | ------------- | ------------- |
|1| HashMap\<E\> | No duplicates, overwrite with the latest value, One Null key, and Multiple null values are allowed. |
|2| LinkedHashMap\<E\> | It is the same as HashMap with an additional feature that maintains insertion order. |
|3| TreeMap\<E\> | Java TreeMap class is a red-black tree-based implementation. It provides an efficient means of storing key-value pairs in sorted order. Java TreeMap is non-synchronized and Java TreeMap maintains ascending order.|
|4| Hashtable\<E\> | Hashtable doesn’t allow any null value and null key. HashTable is synchronized and thread-safe. |

### 1. Code for HashMap\<E\>
```java
public class SampleClass {

	public static void main(String[] args) {
		Map<String, Integer> map = new HashMap<>();

		print(map);
		map.put("vishal", 10);
		map.put("sachin", 30);
		map.put("vaibhav", 20);
		map.put("vishal", 40);
		map.put("Vikash", null);
		map.put("gaurav", null);
		map.put(null, 20);// Allow one null key and multiple null values
		map.put(null, 30);// Allow one null key and multiple null values

		System.out.println("Size of map is:- " + map.size());

		print(map);
		if (map.containsKey("vishal")) {
			Integer a = map.get("vishal");
			System.out.println("value for key \"vishal\" is:- " + a);
		}
		print(map);
		map.clear();
		print(map);
	}

	public static void print(Map<String, Integer> map) {
		if (map.isEmpty()) {
			System.out.println("map is empty");
		}

		else {
			System.out.println(map);
		}
	}

}
```

### 2. Code for LinkedHashMap\<E\>
```java
public class SampleClass {

	public static void main(String[] args) {
		Map<String, Integer> map = new LinkedHashMap<>();

		print(map);
		map.put("vishal", 10);
		map.put("sachin", 30);
		map.put("vaibhav", 20);
		map.put("vishal", 40);
		map.put("Vikash", null);
		map.put("gaurav", null);
		map.put(null, 20);// Allow one null key and multiple null values
		map.put(null, 30);// Allow one null key and multiple null values

		System.out.println("Size of map is:- " + map.size());

		print(map);
		if (map.containsKey("vishal")) {
			Integer a = map.get("vishal");
			System.out.println("value for key \"vishal\" is:- " + a);
		}
		print(map);
		map.clear();
		print(map);
	}

	public static void print(Map<String, Integer> map) {
		if (map.isEmpty()) {
			System.out.println("map is empty");
		}

		else {
			System.out.println(map);
		}
	}

}
```

### 3. Code for TreeMap\<E\>
```java
public class SampleClass {
	public static void main(String[] args) {
        TreeMap<String, Integer> numbers = new TreeMap<>();

        numbers.put("One", 1);
        numbers.put("Two", 2);
        numbers.put("Three", 3);
        System.out.println("TreeMap: " + numbers);

        // Using entrySet()
        System.out.println("Key/Value mappings: " + numbers.entrySet());

        // Using keySet()
        System.out.println("Keys: " + numbers.keySet());

        // Using values()
        System.out.println("Values: " + numbers.values());
    }
}
```

### 4. Code for Hashtable\<E\>
```java
class SampleClass {
	public static void main(String[] args) {
		Map<Integer,String> map = new Hashtable<Integer,String>();
		map.put(1, "One");
		map.put(2, "Two");
		map.put(3, "Three");
		map.put(3, "Four");

		try{
			map.put(4,null);
		}
		catch(Exception e){
			System.out.println("Hashtable doesn’t allow any null value");
		}
		
		try{
			map.put(null,"Five");
		}
		catch(Exception e){
			System.out.println("Hashtable doesn’t allow any null key");
		}
		System.out.println("Hashtable: ");
		
		for(Map.Entry<Integer,String> m:map.entrySet()){
			System.out.println(m.getKey() + "-" + m.getValue());
		}
		System.out.println();
		
		Map<Integer,String> hashMap = new HashMap<Integer,String>();
		hashMap.put(3, "One");
		hashMap.put(2, "Two");
		hashMap.put(1, "Three");
		hashMap.put(4, "Three");
		hashMap.put(5,null);
		hashMap.put(null,"23");
		try{
			hashMap.put(null,"24");
			System.out.println("HashMap allows one null key and multiple null values");
		}
		catch(Exception e){
			System.out.println("Will not come here!");
		}
		
		System.out.println("HashMap: ");
		for(Map.Entry<Integer,String> m:hashMap.entrySet()){
			System.out.println(m.getKey() + "-" + m.getValue());
		}
	}
}
```

## Learn more about Collections Framework [Documents provided by ORACLE](https://docs.oracle.com/javase/8/docs/technotes/guides/collections/overview.html)
