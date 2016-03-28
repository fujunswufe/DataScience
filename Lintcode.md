## [lintcode](lintcode.com)

### 03/27/2016
1. Top K Frequent Words
2. 

*Summary*
1. how to write Comparator and use Comparator in PriorityQueue
```java
        Comparator<Node> NodeComparator = new Comparator<Node>() {
            public int compare (Node left, Node right) {
                if (left.count != right.count) {
                    return left.count - right.count;
                }
                return right.word.compareTo(left.word);
            }
        };
```
