## LintCode

### 03/27/2016
1. [Rehashing](http://www.lintcode.com/en/problem/rehashing/#) (_*LinkedList*_)
    1. Open Hashing using linkedlist
    2. Rehashing for twice the length of the original array
2. [LRU Cache](http://www.lintcode.com/en/problem/lru-cache/#) (_*LinkedList*_, _*HashMap*_)
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
1. [Hash Function](http://www.lintcode.com/en/problem/hash-function/)
```java
long ans = 0;
for(int i = 0; i < key.length;i++) {
    ans = (ans * 33 + (int)(key[i])) % HASH_SIZE; 
} // a little confused
```
2. [Stack Sorting](http://www.lintcode.com/en/problem/stack-sorting/)
    1. additional 单调递减栈
    


