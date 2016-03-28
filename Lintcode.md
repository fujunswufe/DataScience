## [lintcode](lintcode.com)

### 03/27/2016
1. [Rehashing](http://www.lintcode.com/en/problem/rehashing/#) (_*LinkedList*_)
    1. Open Hashing using linkedlist
    2. Rehashing for twice the original array
2. [LRU Cache](http://www.lintcode.com/en/problem/lru-cache/#) (_*LinkedList*_, _*HashMap*_)
    1. Double Linked List to store cache, using one Dummy head and one Dummy Tail
    2. O(1) 从中间拿出一个数，挪到尾巴上
    3. O(1) 的时间，在尾巴上放一个新的数
    4. O(1) 的时间删除最老的节点 when insert a new node and the capacity is full
    5. creating a helper function call "moveToTail"
3. [Longest Consecutive Sequence](http://www.lintcode.com/en/problem/longest-consecutive-sequence/) (*HashMap*)
    1. Using HashMap to store array elements, value is the key
    2. Iterate Array
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
4. Top K Frequent Words

######*Summary*
1. how to write Comparator and use Comparator in PriorityQueue
```java
PriorityQueue<Node> queue = new PriorityQueue<Node>(NodeComparator)();

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
