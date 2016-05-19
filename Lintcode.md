## LintCode

### 03/27/2016
1. [Rehashing](http://www.lintcode.com/en/problem/rehashing/#) (_*LinkedList*_)
    1. Open Hashing using linkedlist
    2. Rehashing for twice the length of the original array
2. **_[LRU Cache](http://www.lintcode.com/en/problem/lru-cache/#)_** (_*LinkedList*_, _*HashMap*_)
    1. Double Linked List to store cache, using one Dummy head and one Dummy Tail
    2. O(1) 从中间拿出一个数，挪到尾巴上
    3. O(1) 的时间，在尾巴上放一个新的数
    4. O(1) 的时间删除最老的节点 when insert a new node and the capacity is full
    5. creating a helper function call "moveToTail"
3. [Longest Consecutive Sequence](http://www.lintcode.com/en/problem/longest-consecutive-sequence/) (*HashMap*)
    1. Using HashMap to store array elements, value is the key
    2. Time complexity, each array element add and remove from map once, O(2*n)
    3. Iterate Array, find left and right elements 
    ```java
    int max = 1
    for (int i : num) {
        int count = 1;
        int temp = i - 1;
        while (map.containsKey(temp)) {
            map.remove(temp);
            temp--;
            count++;
        }
        temp = i + 1;
        while (map.containsKey(temp)) {
            map.remove(temp);
            temp++;
            count++;
        }
        map.remove(i);
        max = Math.max(max, count);
    }
    ```
4. [Top K Frequent Words](http://www.lintcode.com/en/problem/top-k-frequent-words/#) (*HashMap*, *PriorityQueue*)
    1. PriorityQueue Comparator (notice: do not miss ";" in Comparator)
    2. lowest count of word on head of PriorityQueue

###### *Summary*#######
1. how to write Comparator and use Comparator in PriorityQueue
```java
PriorityQueue<Node> queue = new PriorityQueue<Node>(NodeComparator);

Comparator<Node> NodeComparator = new Comparator<Node>() {
    public int compare (Node left, Node right) {
        if (left.count != right.count) {
            return left.count - right.count;
        }
        return right.word.compareTo(left.word);
    }
};

// this the class Node
class Node {
    int count;
    String word;
    public Node(int count, String word) {
        this.count = count;
        this.word = word;
    }
}
```
2. HashTable is thread safe. When two functionals share the same variable, visit a HashTable at the same time, this HashTable has a lock.

### 03/28/2016
1. **[Java Sorting: Comparator vs Comparable Tutorial](http://www.digizol.com/2008/07/java-sorting-comparator-vs-comparable.html)**
1. [Ugly Number](http://www.lintcode.com/en/problem/ugly-number/#)
    1. check *num <= 0* 
    2. while loop for 2, 3, 5 separately
    ```java
    while (num % 2 == 0) {
        num = num / 2;
    }
    while (num % 3 == 0) {
        num = num / 3;
    }
    while (num % 5 == 0) {
        num = num / 5;
    }
    return num == 1;
    ```
2. [Ugly Number II](http://www.lintcode.com/en/problem/ugly-number-ii/)
    1. The naive approach is to call isUgly for every number until you reach the nth one. Most numbers are not ugly. Try to focus your effort on generating only the ugly ones.
    2. An ugly number must be multiplied by either 2, 3, or 5 from a smaller ugly number.
    3. The key is how to maintain the order of the ugly numbers. Try a similar approach of merging from three sorted lists: L1, L2, and L3.
    4. Assume you have Uk, the kth ugly number. Then Uk+1 must be Min(L1 * 2, L2 * 3, L3 * 5).
    5. Each time update the index of L1, or L2, or L3
    ```java
    int i2 = 0; int i3 = 0; int i5 = 0;
    while (list.size() < n) {
        int m2 = list.get(i2) * 2;
        int m3 = list.get(i3) * 3;
        int m5 = list.get(i5) * 5;
        
        int temp = Math.min(Math.min(m2, m3), m5);
        
        if (temp == m2) {
            i2++;
        }
        if (temp == m3) {
            i3++;
        }
        if (temp == m5) {
            i5++;
        }
        list.add(temp);
    }
    ```
3. [Merge k Sorted Arrays](http://www.lintcode.com/en/problem/merge-k-sorted-arrays/#) (*Heap*, *Priority Queue*)
    1. create a new class called _"Element"_ to store row, column and its corresponding value in arrays
    2. create a priority queue with a new **Comparator** (notice for semicolon after the Comparator)
    3. each time poll the head of queue and add next arrays element if it has.

4. [Merge k Sorted Lists](http://www.lintcode.com/en/problem/merge-k-sorted-lists/#) (*Priority Queue*, *Divide&Conquer*)
    1. much similarity with *Merge k Sorted Arrays*
    1. Using a dummy node 
    2. writing **a new Comparator** (corner case: one of nodes is null)

###03/29/2016
1. [Implement Stack](http://www.lintcode.com/en/problem/implement-stack/#)
    1. use an ArrayList to implement a stack
    2. the newest element add to tail
2. [Implement Stack by Two Queues](http://www.lintcode.com/en/problem/implement-stack-by-two-queues/)
    1. **initialization of a Queue in Java**
    2. Two functions, one is *"moveItems()"* and the other is *swapQueues()*
    3. when pop(), pop the last element of q1
3. [Implement Queue by Linked List](http://www.lintcode.com/en/problem/implement-queue-by-linked-list/)
    1. Using a java built LinkedList or create a new one
    2. enqueue: add the element at the end
    3. dequeue: remove the head
4. [Implement Queue by Linked List II](http://www.lintcode.com/en/problem/implement-queue-by-linked-list-ii/)
    1. double linkedlist, using one dummy head and one dummy tail
    2. In initialization
    ```java
    head.next = tail;
    tail.prev = head;
    ```
    
### 04/02/2016
1. [Hash Function](http://www.lintcode.com/en/problem/hash-function/) (*Hash*)
    1. answer
    ```java
    long ans = 0;
    for(int i = 0; i < key.length;i++) {
        ans = (ans * 33 + (int)(key[i])) % HASH_SIZE; 
    } // a little confused
    ```
2. [Stack Sorting](http://www.lintcode.com/en/problem/stack-sorting/) (*Stack*)
    1. additional 单调递减栈
3. [Heapify](http://www.lintcode.com/en/problem/heapify/#) (*Binary Heap*)
    1. [Summary](http://www.cnblogs.com/EdwardLiu/p/4279641.html) on this problem
    2. [Heaps & Other Trees](https://www.cs.cmu.edu/~tcortina/15-121sp10/Unit06B.pdf) and [Heaps](http://courses.cs.vt.edu/cs2604/spring02/Notes/C07.Heaps.pdf)
    3. [Heapify Demo](https://www.cs.princeton.edu/~wayne/kleinberg-tardos/pdf/DemoHeapify.pdf) and [Java implementation on Binary Heap](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Binary%20Heaps/heaps.html)
    4. Given an array of N values, a heap containing those values can be built by simply “sifting” each internal node down to its proper location
        * start with the last internal node
        * swap the current internal node with its smaller child, if necessary
        * then follow the swapped node down
        * continue until all internal nodes are done
4. [Animal Shelter](http://www.lintcode.com/en/problem/animal-shelter/#) (*LinkedList*)
    1. a new class called "Animal"
    2. Use two LinkedList to store *cats* and *dogs* separately 
    3. Use a global variable *index* to store the time
5. Summary on heap
    1. Heap can be implemented using _*complete binary tree*_. Suppose there are N nodes in this binary tree.
    2. Levels: Log2(N+1). Delete root or add a new node: time complexity O(logN)
    3. Using an array size n. Only have *(n / 2 - 1)* internal nodes. The children of *i* is (2\*i + 1) and (2\*i + 2) and parent of *i* is (i/2 - 1). (Notice: all integer division)

### 04/03/2016
1. [Clone Graph](http://www.lintcode.com/en/problem/clone-graph/#) (_BFS_, _HashMap_, _Queue_)
    1. [BFS Template in Binary Tree](http://www.jiuzhang.com/solutions/bfs-template/)
    2. 能用BFS的就用BFS，能不递归就尽量不递归
    3. node -> graph (BFS)
    4. Copy nodes, using a **_HashMap_**. The HashMap stores the mapping relationship between the original node and new node. It can remove and check duplicated nodes. And using a **_Queue_** to store the original nodes, and this queue can be implemented by a _ArrayList_.
    5. Copy edges, iterate the _Queue_ for orignal nodes, copy edges for new nodes
2. [Topological Sorting](http://www.lintcode.com/en/problem/topological-sorting/) (_BFS_, _HashMap_, _Queue_)
    1. Definition of Topological Sorting: 
    2. Iterate the graph, use **HashMap** to store internal nodes and its priority(how many times this node is in neighbors)
    3. Iterate the graph, using HashMap to find nodes with no nodes direct to it, add to a **Queue**
    4. Pop the queue and changes the priority on HashMap. And add qualified nodes to queue

######*Summary*
1. Iterator, [Binary Search Tree Iterator](http://www.lintcode.com/en/problem/binary-search-tree-iterator/#)
2. Tree is a kind of special graph. \# N nodes and \# N - 1 edges and connected all nodes. 
3. [Flood fill](https://zh.wikipedia.org/wiki/Flood_fill): using BFS
4. Search: DFS + BFS
5. DFS : recursion 

### 04/04/2016
1. [Subsets](http://www.lintcode.com/en/problem/subsets/) (_DFS_, _BackTrack_)
    1. Use recursion. Actually a DFS search. Draw a **Search Tree**
    2. Use an index _pos_ to transfer the search position.
    3. Could write a non-recursion method
2. [Subsets II](http://www.lintcode.com/en/problem/subsets-ii/) (_DFS_, _BackTrack_)
    1. Already the same with [Subsets](http://www.lintcode.com/en/problem/subsets/). However, we have to check duplicate subset situations.
    2. _Checking Conditions_. Suppose this is an array {1, 2(1), 2(2)}. There are two duplicate subsets for {1, 2(1)} and {1, 2(2)}. We only want the first one. 
    ```java
    if (i != pos && nums[i] == nums[i - 1]) { // take the duplicate numbers in order
        continue; // store elements in order. We cannot store 2(2) when not store 2(1) first
    }
    ```
3. [Permutations](http://www.lintcode.com/en/problem/permutations/) (_DFS_, _BackTrack_)
    1. Prepare for a non-recursive solution
    2. Almost same as [Subsets](http://www.lintcode.com/en/problem/subsets/)
    3. Two checking conditions. One is if the _size of list_ equals to the _length of array_ num, and the other is whether list.contains(nums[i])
    ```java
    if (list.size() == nums.length) {
        result.add(new ArrayList<Integer>(list));
        return;
    }
    if (list.contains(nums[i])) {
        continue;
    }
    ```
4. [Permutations II](http://www.lintcode.com/en/problem/permutations-ii/) (_DFS_, _BackTrack_)
    1. Same as [Permutations](http://www.lintcode.com/en/problem/permutations/) 
    2. Use a boolean[] array to store whether each element has been visited or not
    3. If we haved changed something before recursion, we have to return to the original after recursion


### 04/05/2016
1. **_[N-Queens](http://www.lintcode.com/en/problem/n-queens/)_** (_DFS_)
    1. Use _recursion_ and _depth first search_
    2. Use an _ArrayList_ to store the column position, and the index is row position
    3. _isValid_ function. check if same column, top-left-to-bottom-right diagonal and top-right-to-bottom-left diagonal
2. [N-Queens II](http://www.lintcode.com/en/problem/n-queens/#) (_DFS_)
    1. First, try to use dynamic programming. However, we canot not find recursion function among n, n - 1 and n - 2. Could only use search. 

### 04/06/2016
7. [Palindrome Partitioning](http://www.lintcode.com/en/problem/palindrome-partitioning/)
8. [Combination Sum](http://www.lintcode.com/en/problem/combination-sum/#)
9. [Combination Sum II](http://www.lintcode.com/en/problem/combination-sum-ii/)


### 19/05/2016
1. balanced binary search tree and heap(priority queue): log(n)
    1. One tree is *balanced* and BST, so it is *TreeMap*(找比某个点小的一个点，找比某个点大的一个点)
2. Iterator(迭代器)：Binary search tree iterator(设计遍历器)
```java
boolean next() {
}

boolean hasNext() {
} 

int value() {
}
```
