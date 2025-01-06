Read first [[Big O Annotations]]

## Table of Contents

1. [Arrays](#arrays)
2. [Linked Lists](#linked-lists)
3. [HashMaps](#hashmaps)
4. [Sets](#sets)
5. [Stacks](#stacks)
6. [Queues](#queues)

### introduction

==A data structure== is a specific format for organizing, storing, and processing data within a computer system

![[Pasted image 20241016105308.png]]

## Arrays

Arrays are ordered collections of data, typically of similar types.

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 500 120">
  <rect width="100%" height="100%" fill="#1a2636"/>
  <rect x="10" y="10" width="80" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="50" y="35" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="middle" dominant-baseline="middle">12</text>
  <rect x="110" y="10" width="80" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="150" y="35" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="middle" dominant-baseline="middle">54</text>
  <rect x="210" y="10" width="80" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="250" y="35" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="middle" dominant-baseline="middle">37</text>
  <rect x="310" y="10" width="80" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="350" y="35" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="middle" dominant-baseline="middle">20</text>
  <rect x="410" y="10" width="80" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="450" y="35" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="middle" dominant-baseline="middle">96</text>
  <text x="10" y="70" font-family="Arial" font-size="14" fill="#ffffff" text-anchor="start">Memory Address:</text>
  <text x="50" y="90" font-family="Arial" font-size="14" fill="#03a9f4" text-anchor="middle">1000</text>
  <text x="150" y="90" font-family="Arial" font-size="14" fill="#03a9f4" text-anchor="middle">1004</text>
  <text x="250" y="90" font-family="Arial" font-size="14" fill="#03a9f4" text-anchor="middle">1008</text>
  <text x="350" y="90" font-family="Arial" font-size="14" fill="#03a9f4" text-anchor="middle">1012</text>
  <text x="450" y="90" font-family="Arial" font-size="14" fill="#03a9f4" text-anchor="middle">1016</text>
</svg>

### Key Characteristics:

- Uses zero-based indexing
- Stored in contiguous memory

### Operations and Time Complexities:

- Reading: O(1)
- Insertion/Deletion: O(n)

### Memory Storage:

Arrays are stored in contiguous blocks of memory. Each element occupies a fixed amount of space (e.g., 4 bytes for integers), and the memory address of each element can be calculated using its index.

```
[1,2,3,4,5,6,7,8,9]
```

## Linked Lists

Linked lists are ordered lists of data elements, where each element points to the next.

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 500 180">
  <rect width="100%" height="100%" fill="#1a2636"/>
  <rect x="10" y="10" width="80" height="80" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="50" y="35" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="middle" dominant-baseline="middle">12</text>
  <text x="50" y="75" font-family="Arial" font-size="14" fill="#03a9f4" text-anchor="middle" dominant-baseline="middle">→ 2000</text>
  <rect x="110" y="10" width="80" height="80" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="150" y="35" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="middle" dominant-baseline="middle">54</text>
  <text x="150" y="75" font-family="Arial" font-size="14" fill="#03a9f4" text-anchor="middle" dominant-baseline="middle">→ 3000</text>
  <rect x="210" y="10" width="80" height="80" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="250" y="35" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="middle" dominant-baseline="middle">37</text>
  <text x="250" y="75" font-family="Arial" font-size="14" fill="#03a9f4" text-anchor="middle" dominant-baseline="middle">→ 4000</text>
  <rect x="310" y="10" width="80" height="80" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="350" y="35" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="middle" dominant-baseline="middle">20</text>
  <text x="350" y="75" font-family="Arial" font-size="14" fill="#03a9f4" text-anchor="middle" dominant-baseline="middle">→ 5000</text>
  <rect x="410" y="10" width="80" height="80" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="450" y="35" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="middle" dominant-baseline="middle">96</text>
  <text x="450" y="75" font-family="Arial" font-size="14" fill="#03a9f4" text-anchor="middle" dominant-baseline="middle">→ NULL</text>
  <text x="10" y="110" font-family="Arial" font-size="14" fill="#ffffff" text-anchor="start">Memory Address:</text>
  <text x="50" y="130" font-family="Arial" font-size="14" fill="#03a9f4" text-anchor="middle">1000</text>
  <text x="150" y="130" font-family="Arial" font-size="14" fill="#03a9f4" text-anchor="middle">2000</text>
  <text x="250" y="130" font-family="Arial" font-size="14" fill="#03a9f4" text-anchor="middle">3000</text>
  <text x="350" y="130" font-family="Arial" font-size="14" fill="#03a9f4" text-anchor="middle">4000</text>
  <text x="450" y="130" font-family="Arial" font-size="14" fill="#03a9f4" text-anchor="middle">5000</text>
  <line x1="90" y1="50" x2="110" y2="50" stroke="#03a9f4" stroke-width="2" marker-end="url(#arrowhead)"/>
  <line x1="190" y1="50" x2="210" y2="50" stroke="#03a9f4" stroke-width="2" marker-end="url(#arrowhead)"/>
  <line x1="290" y1="50" x2="310" y2="50" stroke="#03a9f4" stroke-width="2" marker-end="url(#arrowhead)"/>
  <line x1="390" y1="50" x2="410" y2="50" stroke="#03a9f4" stroke-width="2" marker-end="url(#arrowhead)"/>
  <defs>
    <marker id="arrowhead" markerWidth="10" markerHeight="7" refX="0" refY="3.5" orient="auto">
      <polygon points="0 0, 10 3.5, 0 7" fill="#03a9f4"/>
    </marker>
  </defs>
</svg>

### Key Characteristics:

- Elements not stored in contiguous memory
- Each element has a pointer to the next element

### Operations and Time Complexities:

- Reading: O(n)
- Insertion/Deletion: O(1) (if position is known)

### Memory Storage:

In a linked list, each node contains the data and a pointer to the next node. Nodes can be stored anywhere in memory, with the pointer keeping track of the next element's location.

## HashMaps

HashMaps (also called Hash Tables or Dictionaries) are unordered collections of key-value pairs.

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 500 300">
  <rect width="100%" height="100%" fill="#1a2636"/>
  <rect x="10" y="10" width="480" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="30" y="35" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="start" dominant-baseline="middle">0: "Apple" → 54</text>
  <rect x="10" y="60" width="480" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="30" y="85" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="start" dominant-baseline="middle">1: "Banana" → 37</text>
  <rect x="10" y="110" width="480" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="30" y="135" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="start" dominant-baseline="middle">2: "Cherry" → 20</text>
  <rect x="10" y="160" width="480" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="30" y="185" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="start" dominant-baseline="middle">3: "Date" → 96</text>
  <rect x="10" y="210" width="480" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="30" y="235" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="start" dominant-baseline="middle">4: "Elderberry" → 12</text>
  <text x="10" y="270" font-family="Arial" font-size="14" fill="#ffffff" text-anchor="start">Hash Function: h(key) = sum of ASCII values % 5</text>
</svg>

### Key Characteristics:

- Unordered
- Uses custom keys for indexing

### Operations and Time Complexities:

- Insertion: O(1) average
- Deletion: O(1) average
- Search: O(1) average

### Memory Storage:

HashMaps use an array of buckets to store data. Each key is hashed to determine which bucket its corresponding value should be stored in. In case of collisions, methods like chaining or open addressing are used.

### Hash Function and Collisions

The hash function used in this example is:

h(key) = sum of ASCII values % 5

This function sums the ASCII values of each character in the key and then takes the remainder when divided by 5. While simple and fast, this function has limitations:

1. It only produces 5 possible hash values (0-4), which can lead to many collisions.
2. Different keys can easily produce the same hash value.

#### Example of a Collision:

- "Cat" → 280 % 5 = 0
- "Egg" → 300 % 5 = 0

Both "Cat" and "Egg" hash to the same value (0), creating a collision.

### Collision Resolution Strategies

To handle collisions, HashMaps employ various strategies:

#### 1. Chaining

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 500 200">
  <rect width="100%" height="100%" fill="#1a2636"/>
  <rect x="10" y="10" width="480" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="30" y="35" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="start" dominant-baseline="middle">0: Cat → 5 → Egg → 7</text>
  <rect x="10" y="60" width="480" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="30" y="85" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="start" dominant-baseline="middle">1: Bird → 3</text>
  <rect x="10" y="110" width="480" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="30" y="135" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="start" dominant-baseline="middle">2: </text>
  <rect x="10" y="160" width="480" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="30" y="185" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="start" dominant-baseline="middle">3: Dog → 4</text>
</svg>

In chaining, each bucket contains a linked list of key-value pairs. When a collision occurs, the new key-value pair is appended to the list in the appropriate bucket.

#### 2. Open Addressing (Linear Probing)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 500 200">
  <rect width="100%" height="100%" fill="#1a2636"/>
  <rect x="10" y="10" width="480" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="30" y="35" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="start" dominant-baseline="middle">0: Cat → 5</text>
  <rect x="10" y="60" width="480" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="30" y="85" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="start" dominant-baseline="middle">1: Egg → 7</text>
  <rect x="10" y="110" width="480" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="30" y="135" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="start" dominant-baseline="middle">2: Bird → 3</text>
  <rect x="10" y="160" width="480" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="30" y="185" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="start" dominant-baseline="middle">3: Dog → 4</text>
</svg>

In open addressing, when a collision occurs, we search for the next open slot in the array. In linear probing, we simply move to the next bucket until we find an empty one.

### Use Cases:

1. Implementing caches in web browsers and databases
2. Managing sessions in web applications
3. Storing configuration settings in software applications
4. Creating dictionaries or language translation tools
5. Counting word frequencies in text analysis

## Stacks

Stacks are LIFO (Last In, First Out) data structures.

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 300 300">
  <rect width="100%" height="100%" fill="#1a2636"/>
  <rect x="100" y="10" width="100" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="150" y="35" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="middle" dominant-baseline="middle">96 (Top)</text>
  <rect x="100" y="60" width="100" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="150" y="85" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="middle" dominant-baseline="middle">20</text>
  <rect x="100" y="110" width="100" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="150" y="135" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="middle" dominant-baseline="middle">37</text>
  <rect x="100" y="160" width="100" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="150" y="185" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="middle" dominant-baseline="middle">54</text>
  <rect x="100" y="210" width="100" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="150" y="235" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="middle" dominant-baseline="middle">12</text>
  <text x="10" y="270" font-family="Arial" font-size="14" fill="#ffffff" text-anchor="start">Top Pointer: 1000 (Memory address of 96)</text>
  <line x1="80" y1="30" x2="100" y2="30" stroke="#03a9f4" stroke-width="2" marker-end="url(#arrowhead)"/>
  <text x="70" y="25" font-family="Arial" font-size="14" fill="#03a9f4" text-anchor="end">Top</text>
</svg>

### Key Operations:

- Push: Add an element to the top
- Pop: Remove the top element
- Peek: View the top element without removing it

### Time Complexity:

All operations are O(1)

### Memory Storage:

Stacks can be implemented using arrays or linked lists. In this representation, we show an array-based implementation where elements are pushed and popped from one end.

### Use Cases:

1. Implementing undo/redo functionality in applications
2. Managing back button functionality in web browsers

## Queues

Queues are FIFO (First In, First Out) data structures.

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 500 120">
  <rect width="100%" height="100%" fill="#1a2636"/>
  <rect x="10" y="10" width="80" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="50" y="35" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="middle" dominant-baseline="middle">12 (Front)</text>
  <rect x="110" y="10" width="80" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="150" y="35" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="middle" dominant-baseline="middle">54</text>
  <rect x="210" y="10" width="80" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="250" y="35" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="middle" dominant-baseline="middle">37</text>
  <rect x="310" y="10" width="80" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="350" y="35" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="middle" dominant-baseline="middle">20</text>
  <rect x="410" y="10" width="80" height="40" fill="#1a2636" stroke="#ffffff" stroke-width="2"/>
  <text x="450" y="35" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="middle" dominant-baseline="middle">96 (Rear)</text>
  <text x="10" y="70" font-family="Arial" font-size="14" fill="#ffffff" text-anchor="start">Front Pointer: 1000 (Memory address of 12)</text>
  <text x="10" y="90" font-family="Arial" font-size="14" fill="#ffffff" text-anchor="start">Rear Pointer: 1016 (Memory address of 96)</text>
  <line x1="0" y1="30" x2="10" y2="30" stroke="#03a9f4" stroke-width="2" marker-end="url(#arrowhead)"/>
  <text x="0" y="25" font-family="Arial" font-size="14" fill="#03a9f4" text-anchor="start">Front</text>
  <line x1="490" y1="30" x2="500" y2="30" stroke="#03a9f4" stroke-width="2" marker-start="url(#arrowhead)"/>
  <text x="500" y="25" font-family="Arial" font-size="14" fill="#03a9f4" text-anchor="end">Rear</text>
</svg>

### Key Operations:

- Enqueue: Add an element to the back
- Dequeue: Remove the front element
- Front: View the front element without removing it

### Time Complexity:

All operations are O(1)

### Memory Storage:

Queues can be implemented using arrays or linked lists. In this representation, we show an array-based implementation with front and rear pointers to keep track of the queue's boundaries.

### Use Cases:

1. Simulating waiting lines in various applications (e.g., customer service systems)

## Sets

Sets are collections that store unique elements with no duplicate values.

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 500 250">
  <rect width="100%" height="100%" fill="#1a2636"/>
  <circle cx="250" cy="125" r="100" fill="none" stroke="#ffffff" stroke-width="2"/>
  <text x="250" y="80" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="middle">Apple</text>
  <text x="200" y="120" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="middle">Banana</text>
  <text x="300" y="120" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="middle">Cherry</text>
  <text x="220" y="160" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="middle">Date</text>
  <text x="280" y="160" font-family="Arial" font-size="16" fill="#4caf50" text-anchor="middle">Elderberry</text>
  <text x="250" y="230" font-family="Arial" font-size="14" fill="#ffffff" text-anchor="middle">Set of Fruits</text>
</svg>

### Key Characteristics:

- No duplicate elements
- Unordered (in most implementations)
- Membership testing is typically fast

### Operations and Time Complexities:

- Insertion: O(1) average
- Deletion: O(1) average
- Search (membership testing): O(1) average

### Memory Storage:

Sets are often implemented using hash tables internally, similar to HashMaps, but without associated values for the elements.

### Use Cases:

1. Membership testing (checking if an item exists in a collection)
2. Tracking unique visitors to a website
3. Spell checking (dictionary of valid words)

### Comparison with HashMap:

- Sets only store keys (elements), while HashMaps store key-value pairs
- Sets are used when you only care about the presence or absence of an item
- HashMaps are used when you need to associate additional data with each key
