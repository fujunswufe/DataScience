## [lintcode](lintcode.com)

### 03/27/2016
1. Top K Frequent Words
2. 

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

