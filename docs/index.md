# Data Structure

Is is a particular way of organising data in a computer so that it can be used effectively.
The idea is to reduce the space and time complexity of different tasks.

## Linear Data Structures

### Array

It is a data structure used to store homogeneous elements at contiguous locations, size of an array must be provided before storing data.

$$Insertion \rightarrow O(n)$$
$$Deletion \rightarrow O(n)$$
$$Access \rightarrow O(1)$$
$$Search \rightarrow O(n)$$

### LinkedList

- SinglyLinkedList
- DoublyLinkedList
Random access in not allowed.

$$Insertion \rightarrow O(1)$$
$$Deletion \rightarrow O(1)$$
$$Access \rightarrow O(n)$$

### Stack (LIFO)

$$Insertion \rightarrow O(1)$$
$$Deletion \rightarrow O(1)$$
$$Access \rightarrow O(n)$$

eg:

- DFS
- Reverse a word
- Undo
- Back/Forward on browsers
- Matching braces

### Queue (FIFO)

$$Insertion \rightarrow O(1)$$
$$Deletion \rightarrow O(1)$$
$$Access \rightarrow O(n)$$

eg:

- CPU scheduling
- BFS
- When data is transferred asynchronously between two processes i.e IO Buffers, pipes, file IO

## Hierarchical Data Structure

### Binary Tree

A binary tree has each node having at most two children, which are referred to as the left child and the right child.

A tree is represented by a pointer to the topmost node in tree.

A node contains:

- Data
- Pointer to left child
- Pointer to right child

A Binary Tree can be traversed in two ways:

1. Depth First Traversal
2. Breadth First Traversal

Properties:

- The maximum number of nodes at level
$$l = 2^(l-1)$$
- Maximum number of nodes, where h $\to$ height of the tree
$$2^h-1$$

eg: They are useful in File Structures where each file is located in a particular directory and there is a specific hierarchy associated with file and directories.

### Binary Search Tree

A tree with following additional properties:

- The left subtree of a node contains only nodes with keys less than the node's key.
- The right subtree of a node contains only nodes with keys greater than the node's key.
- The left and right subtree each must also be a binary search tree.

Time Complexity of BST:

$$Search \rightarrow O(h)$$
$$Insertion \rightarrow O(h)$$
$$Deletion \rightarrow O(h)$$

h -> O(log n) if height balanced

- Access/Search quicker than LinkedList and slower than Array.
- Insertion/Deletion quicker than Arrays and slower than LinkedList.

### Graph

It consists of following two components:

1. A finite set of vertices also called as nodes
2. A finite set of ordered pair of the form (u,v) called as edge.

The pair is ordered because (u,v) is not same as (v,u) in case of directed graph.

The pair of the form (u,v) indicates that there is an edge vertex u to vertex v. The edges may contain weight/value/cost.

V -> number of vertices

E -> number of Edges

Direction:

- Undirected Graph
- Directed Graph

Weight:

- Weighted Graph
- Unweighted Graph

eg: The graph is used to find shortest path in any network.

### TRIE (Digital Tree or Radix Tree or Prefix Tree)

It is the efficient information retrieval data structure. If we store keys in BST, a well balanced BST will need time proportional to M * log N where M is max string length and N is number of keys in tree, using TRIE search will take O(M).

## Time Complexity

It is the computational complexity that measures or estimates the time taken for running an algorithm.

It is commonly estimated by counting the number of elementary operations performed by the algorithm, supposing that an elementary operation takes a fixed amount of time to perform. Thus, the amount of time taken and the number of elementary operations performed by the algorithm differ by at most a constant factor.

Since an algorightm's running time may vary with different inputs of the same size, one commonly considers the worst-case time complexity, which is the maximum amount of time taken on inputs of a given size.

Time complexity is generally expressed as a function of the size of the input. One commonly focuses on the behavior of the complexity when the input size increases. i.e on the asympototic behavior of the complexity.

## Sorting

| Algorithm | Worst |
| --------- | ----- |
| Selection Sort | O(n^2) |
| Bubble Sort | O(n^2) |
| Insertion Sort | O(n^2) |
| Merge Sort | O(n log n) |
| Quick Sort | O(n^2) |
| Heap Sort | O(n log n) |

### In-place Sorting

The input is usually overwritten by the output as the algorithm executes (through replacement or swapping of elements). Space Complexity is O(log n).

eg: Selection Sort, Bubble Sort, Insertion Sort, Heap Sort

Heap Sort is a comparison based sorting technique based on  Binary Heap data structure.

### External Sorting

Used when all data that needs to be sorted cannot be placed in memory at a time, it is used for massive amount of data.

eg: Merge Sort and its variations

## Searching

1. **Linear Search**: A sequential search is made over all items one by one. The Time Complexity is O(n1).
2. **Binary Search**: The data should be in the sorted form. Search a sorted array by repeatedly dividing the search interval in half. Begin with an interval covering the whole array. If the value of search key is less than the item in the middle of the interval, narrow the interval to the lower half. Otherwise narrow it to the upper half. Repeatedly check until the value is found or the interval is empty. Time Complexity is O(log n).
