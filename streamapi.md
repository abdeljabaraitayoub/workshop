The **Stream API** in Java (introduced in Java 8) provides a modern and efficient way to process sequences of data (like collections, arrays, or I/O channels) in a functional programming style. It allows for performing operations on data in a declarative and concise manner, and it also supports parallel processing, enabling more efficient use of multi-core processors.

### Key Features of the Stream API:

1. **Stream Operations**:

- **Intermediate Operations**: These are operations that transform a stream into another stream. They are lazy, meaning they are not executed until a terminal operation is invoked. Examples include:
- `filter()`: Filters elements based on a condition.
- `map()`: Transforms each element.
- `distinct()`: Removes duplicates.
- `sorted()`: Sorts elements.
- **Terminal Operations**: These operations produce a result or a side-effect and trigger the processing of the stream. Examples include:
- `collect()`: Collects the elements into a collection.
- `forEach()`: Iterates over each element.
- `reduce()`: Combines elements to produce a single result.
- `count()`: Returns the number of elements.
- `anyMatch()`, `allMatch()`, `noneMatch()`: Test whether any/all/no elements satisfy a condition.

3. **Parallel Streams**:

- Streams can be processed in parallel by calling `.parallelStream()` on a collection. This splits the stream into multiple chunks and processes them concurrently, using available CPU cores.

4. **Laziness**:

- Most operations are lazy, meaning they are not performed until a terminal operation is invoked. This allows for efficient processing, especially when chaining operations.

5. **Functional Programming**:

- The Stream API encourages functional programming techniques, such as immutability and lambda expressions. It allows operations like filtering, mapping, and reducing data in a clean and readable way.

---

### Example Usage:

```java
import java.util.*;
import java.util.stream.*;

public class StreamExample {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

        List<Integer> evenSquares = numbers.stream()
                                           .filter(n -> n % 2 == 0)
                                           .map(n -> n * n)
                                           .collect(Collectors.toList());
        System.out.println("Even squares: " + evenSquares);

        int sum = numbers.stream()
                         .filter(n -> n % 2 != 0)
                         .map(n -> n * n)
                         .reduce(0, Integer::sum);
        System.out.println("Sum of squares of odd numbers: " + sum);

        long count = numbers.parallelStream()
                             .filter(n -> n % 2 == 0)
                             .count();
        System.out.println("Count of even numbers (parallel): " + count);
    }
}
```

https://www.geeksforgeeks.org/java-8-interview-questions-and-answers/

### Benefits of the Stream API:

- **Concise and Readable Code**: Operations are chained in a clear, functional style.
- **Parallelism**: Streams can be easily processed in parallel, making them suitable for large datasets.
- **Lazy Evaluation**: Intermediate operations are lazily evaluated, which can optimize performance.
- **Functional Style**: The Stream API embraces immutability and pure functions, making it easier to reason about the code.
