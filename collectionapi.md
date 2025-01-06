The **Collection API** in Java is a part of the Java Standard Library (`java.util` package) and provides a framework for working with groups of objects. It includes interfaces and classes to represent and manipulate collections, such as lists, sets, and maps, offering powerful tools for handling data structures efficiently.

### Key Features of the Collection API:

1. **Interfaces**:

- The API defines several core interfaces that represent various types of collections:
- **`Collection`**: The root interface for most collection classes.
- **`List`**: An ordered collection (e.g., `ArrayList`, `LinkedList`).
- **`Set`**: A collection that does not allow duplicate elements (e.g., `HashSet`, `TreeSet`).
- **`Queue`**: A collection used to hold elements before processing (e.g., `PriorityQueue`, `Deque`).
- **`Map`**: An interface for key-value pairs (e.g., `HashMap`, `TreeMap`).
  ![[Pasted image 20250106134132.png]]

1. **Classes**:

- The framework provides concrete implementations for these interfaces:
- **`ArrayList`**: A resizable array implementation of `List`.
- **`LinkedList`**: A doubly-linked list implementation of `List` and `Deque`.
- **`HashSet`**: A hash table-backed implementation of `Set`.
- **`HashMap`**: A hash table-backed implementation of `Map`.

2. **Utilities**:

- The `Collections` class provides utility methods to manipulate collections, such as:
- Sorting (`Collections.sort`)
- Searching (`Collections.binarySearch`)
- Shuffling (`Collections.shuffle`)

3. **Iterators**:

- The API provides mechanisms like **Iterator** and **ListIterator** to traverse through elements in a collection.

4. **Stream API** (introduced in Java 8):

- Supports functional-style operations for processing collections, like `filter`, `map`, and `reduce`.

---

### Example Usage:

```java
import java.util.*;

public class CollectionExample {
    public static void main(String[] args) {

        List<String> list = new ArrayList<>();
        list.add("Apple");
        list.add("Banana");
        list.add("Orange");
        System.out.println("List: " + list);

        Set<String> set = new HashSet<>(list);
        set.add("Apple");
        System.out.println("Set: " + set);

        Map<Integer, String> map = new HashMap<>();
        map.put(1, "One");
        map.put(2, "Two");
        map.put(3, "Three");
        System.out.println("Map: " + map);
    }
}
```

### Benefits:

- Reduces development effort with reusable data structures.
- Simplifies data management by providing well-tested classes and methods.
- Improves code readability and maintainability.

  https://www.javatpoint.com/java-collections-interview-questions
