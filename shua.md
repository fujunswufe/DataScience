
###07/19
1. [Palindrome Linked List](http://www.lintcode.com/en/problem/palindrome-linked-list/)
2. [Convert Binary Search Tree to Doubly Linked List](http://www.lintcode.com/en/problem/convert-binary-search-tree-to-doubly-linked-list/)
3. [Reverse Nodes in k-Group](http://www.lintcode.com/en/problem/reverse-nodes-in-k-group/)
1. [Merge Sorted Array](http://www.lintcode.com/en/problem/merge-sorted-array/#)
2. [Merge Two Sorted Arrays](http://www.lintcode.com/en/problem/merge-two-sorted-arrays/)
3. __[Median](http://www.lintcode.com/en/problem/median/#)__
   * [instructions](http://algorithm.yuanbin.me/zh-hans/integer_array/median.html)
   * [Quick Sort](http://algorithm.yuanbin.me/zh-hans/basics_sorting/quick_sort.html)
4. [Kth Largest Element](http://www.lintcode.com/en/problem/kth-largest-element/#)
   * quick select based on quick sort
5. [Median of two Sorted Arrays](http://www.lintcode.com/en/problem/median-of-two-sorted-arrays/#)
   * 二分法，每次扔掉k的一半

###07/20
1. [Maximum Subarray](http://www.lintcode.com/en/problem/maximum-subarray/#)
    * [globalMax and localMax解法](http://hehejun.blogspot.com/2015/01/leetcodemaximum-subarray.html)
2. [Maximum Subarray II](http://www.lintcode.com/en/problem/maximum-subarray-ii/)
    * [dp解法](http://hehejun.blogspot.com/2015/01/lintcodemaximum-subarray-ii.html)
3. [Maximum Subarray III](http://www.lintcode.com/en/problem/maximum-subarray-iii/#)
    * [区间型动态规划](http://www.jiuzhang.com/solutions/maximum-subarray-iii/)
4. [Best Time to Buy and Sell Stock](http://www.lintcode.com/en/problem/best-time-to-buy-and-sell-stock/#)
    * greedy, prices[index] - min
5. [Best Time to Buy and Sell Stock II](http://www.lintcode.com/en/problem/best-time-to-buy-and-sell-stock-ii/#)
    * greedy
6. [Best Time to Buy and Sell Stock III](http://www.lintcode.com/en/problem/best-time-to-buy-and-sell-stock-iii/#)
    * two for loop, dp

###07/21
1. [Best Time to Buy and Sell Stock IV](http://www.lintcode.com/en/problem/best-time-to-buy-and-sell-stock-iv/#)
    1. 最多允许 k 次交易，由于一次增加收益的交易至少需要两天，故当 k >= n/2时，此题退化为卖股票的第二道题，即允许任意多次交易
    2. 当 k < n/2 时，使用动规来求解
2. [Minimum Subarray](http://www.lintcode.com/en/problem/minimum-subarray/#)
    * localMin, GlobalMin (和Maximum Subarray同理)
3. [Maximum Subarray Difference](http://www.lintcode.com/en/problem/maximum-subarray-difference/)
    * Math.max(Math.abs(leftMax - rightMin), Math.asb(rightMax - leftMin))
4. [Subarray Sum](http://www.lintcode.com/en/problem/subarray-sum/)
    * HashMap
    * key = prefix Sum, value = index
    * i ~ j 区间和为0，条件是 preSum[j] - preSum[i - 1] == 0
5. [Subarray Sum Closest](http://www.lintcode.com/en/problem/subarray-sum-closest/#)
    * 排序前缀和







##Linked List
#####Tips
1. dummy node
2. two pointers: prev and head


#####Questions
1. [Reverse Linked List](http://www.lintcode.com/en/problem/reverse-linked-list/)
    * use prev and head, everytime move prev and head
    * use a temporary node to store head.next
2. [Reverse Linked List II](http://www.lintcode.com/en/problem/reverse-linked-list-ii/)
    * premNode, mNode
    * nNode, postnNpde
3. [Remove Duplicates from Sorted List](http://www.lintcode.com/en/problem/remove-duplicates-from-sorted-list/)
4. [Remove Duplicates from Sorted List II](http://www.lintcode.com/en/problem/remove-duplicates-from-sorted-list-ii/#)
    * use a dummy node
5. [Middle of Linked List](http://www.lintcode.com/en/problem/middle-of-linked-list/#)
    * two pointers: slow and fast
    * Be careful of _NullPointerExeception_
6. [Merge Two Sorted Lists](http://www.lintcode.com/en/problem/merge-two-sorted-lists/#)
    * dummy node
    * link rest of l1 or l2
7. [Sort List](http://www.lintcode.com/en/problem/sort-list/)
    * find middle node
    * recursion on function itself
    * merge two sorted lists
8. [Reorder List](http://www.lintcode.com/en/problem/reorder-list/#)
    * find middle node
    * reverse the second linked list
    * merge two list: one is first hald and the other is reversed second half
9. [Partition List](http://www.lintcode.com/en/problem/partition-list/#)
    * two dummy nodes
10. [Linked List Cycle](http://www.lintcode.com/en/problem/linked-list-cycle/#)
    * slow and fast pointer 
11. [Linked List Cycle II](http://www.lintcode.com/en/problem/linked-list-cycle-ii/#)
    * [tutorial on csdn](http://blog.csdn.net/kenden23/article/details/13871699)
12. [Rotate List](http://www.lintcode.com/en/problem/rotate-list/#)
    * findLength
    * four ListNode: previous node of new head(the node rotate first), new head, tail, original head
14. [Merge k Sorted Lists](http://www.lintcode.com/en/problem/merge-k-sorted-lists/#)
    * __Heap(Priority Queue)__
        - [Comparable vs. Comparator in Java](http://www.programcreek.com/2011/12/examples-to-demonstrate-comparable-vs-comparator-in-java/)
        - rewrite comparator, minHeap
        - size of heap is k
        - time complexity: O(Nlogk). heap插入删除的时间复杂度是O(logk), N:所有node的个数
    * _Divide and Conquer_
        - from top to bottom
        - the bottom is about *merging two lists*
    * _merge two by two
15. [Copy List with Random Pointer](http://www.lintcode.com/en/problem/copy-list-with-random-pointer/#)
    * iterate once, using hashmap
    * O(1) space, 1 -> 1' -> 2 -> 2' -> 3 -> 3' -> null, head.next.random = head.random.next
16. [Convert Sorted List to Balanced BST](http://www.lintcode.com/en/problem/convert-sorted-list-to-balanced-bst/#)
    * using one class variable
    * recursion
    * 把current开头的，长度为size的点，变成BST，并且顺便把current这个点，挪到size + 1的那个点

##Dynamic Programming
#####QA
1. [动态规划十问十答](http://chuansong.me/n/1543583)
2. [yuanbin Dynamic Programming](http://algorithm.yuanbin.me/zh-hans/dynamic_programming/)

#####Questions
1. [Palindrome Partitioning II](http://www.lintcode.com/en/problem/palindrome-partitioning-ii/)
2. [Word Break](http://www.lintcode.com/en/problem/word-break/)


##Binary Tree & Divide Conquer
1. [some binary tree solutions](http://ihuafan.com/%E7%AE%97%E6%B3%95/lintcode-binary-tree-summary#lintcode-467-complete-binary-tree-%E5%AE%8C%E5%85%A8%E4%BA%8C%E5%8F%89%E6%A0%91)

#####DFS: preorder, inorder, postorder. ([二叉树的非递归遍历](http://www.cnblogs.com/dolphin0520/archive/2011/08/25/2153720.html))
1. [Binary Tree Preorder Traversal](http://www.lintcode.com/en/problem/binary-tree-preorder-traversal/#)
2. [Binary Tree Inorder Traversal](http://www.lintcode.com/en/problem/binary-tree-inorder-traversal/#)
  * recursion: using one *helper* function
  * [iterate using one stack](http://algorithm.yuanbin.me/zh-hans/binary_tree/binary_tree_inorder_traversal.html)
    - 首先需要一直对左子树迭代并将非空节点入栈
    - 节点指针为空后不再入栈
    - 当前节点为空时进行出栈操作，并访问栈顶节点
    - 将当前指针p用其右子节点替代
3. [Binary Tree Postorder Traversal](http://www.lintcode.com/en/problem/binary-tree-postorder-traversal/)
    * 维护 currentNode, preNode
    * if (currentNode 没有左右孩子，或者左右孩子已经被访问过)，才能访问这个节点，并且pop
    * else (push当前节点的左右孩子)

####Binary Tree
2. [Maximum Depth of Binary Tree](http://www.lintcode.com/en/problem/maximum-depth-of-binary-tree/#)
3. [Balanced Binary Tree](http://www.lintcode.com/en/problem/balanced-binary-tree/)
4. [Lowest Common Ancestor](http://www.lintcode.com/en/problem/lowest-common-ancestor/#): **[自底向上](http://algorithm.yuanbin.me/zh-hans/binary_tree/lowest_common_ancestor.html)**
    ```Java
    // children node has pointer to parent node
    public class Solution {
    private ArrayList<TreeNode> getPath2Root(TreeNode node) {
            ArrayList<TreeNode> list = new ArrayList<TreeNode>();
            while (node != null) {
                list.add(node);
                node = node.parent;
            }
            return list;
        }
        public TreeNode lowestCommonAncestor(TreeNode node1, TreeNode node2) {
            ArrayList<TreeNode> list1 = getPath2Root(node1);
            ArrayList<TreeNode> list2 = getPath2Root(node2);
            
            int i, j;
            for (i = list1.size() - 1, j = list2.size() - 1; i >= 0 && j >= 0; i--, j--) {
                if (list1.get(i) != list2.get(j)) {
                    return list1.get(i).parent;
                }
            }
            return list1.get(i+1);
        }
    }
    ```
5. [Lowest Common Ancestor of a Binary Search Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/), same as above
4. [Binary Tree Maximum Path Sum](http://www.lintcode.com/en/problem/binary-tree-maximum-path-sum/)
5. [Binary Tree Maximum Path Sum II](http://www.lintcode.com/en/problem/binary-tree-maximum-path-sum-ii/#)
6. [Binary Tree Path Sum](http://www.lintcode.com/en/problem/binary-tree-path-sum/)
7. [Binary Tree Paths](http://www.lintcode.com/en/problem/binary-tree-paths/#)
8. [Tweaked Identical Binary Tree](http://www.lintcode.com/en/problem/tweaked-identical-binary-tree/#)
9. [Identical Binary Tree](http://www.lintcode.com/en/problem/identical-binary-tree/#)
10. [Symmetric Binary Tree](http://www.lintcode.com/en/problem/symmetric-binary-tree/#)
    * recursion
    * traversal
11. [Complete Binary Tree](http://www.lintcode.com/en/problem/complete-binary-tree/#)
    * _full binary tree_: 每个节点都有0个或者2个孩子
    * _complete binary tree_: 所有的叶子都拥有同的深度，所有的内部节点拥有 2个孩子
    * BFS: 广度优先搜索，对于一棵树，层层遍历，把每层的节点从左向右依此加入Stack，然后把Stack上层的None弹出，最后检查如果Stack中还有None说明不是Complete Tree
12. [Minimum Depth of Binary Tree](http://www.lintcode.com/en/problem/minimum-depth-of-binary-tree/#)
    * check root.left == null or root.right == null
13. [Insert Node in a Binary Search Tree](http://www.lintcode.com/en/problem/insert-node-in-a-binary-search-tree/)

####BFS
6. [Binary Tree Level Order Traversal](http://www.lintcode.com/en/problem/binary-tree-level-order-traversal/#)
7. [Binary Tree Level Order Traversal II](http://www.lintcode.com/en/problem/binary-tree-level-order-traversal-ii/#)
7. [Binary Tree Zigzag Level Order Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)

####Binary Search Tree
8. [Validate Binary Search Tree](http://www.lintcode.com/en/problem/validate-binary-search-tree/#)
  1. [Online Solution](http://algorithm.yuanbin.me/zh-hans/binary_search_tree/validate_binary_search_tree.html)
10. [Inorder Successor in Binary Search Tree](http://www.lintcode.com/en/problem/inorder-successor-in-binary-search-tree/)
    * (1) If right subtree of node is not NULL, then succ lies in right subtree. Do following. Go to right subtree and return the left most node
    * (2) If right sbtree of node is NULL, then start from root and us search like technique. Do following. Travel down the tree, if a node’s data is greater than root’s data then go right side, otherwise go to left side.
    * Follow up: a TreeNode has parent pointer
11. [Binary Search Tree Iterator](http://www.lintcode.com/en/problem/binary-search-tree-iterator/)
    * inorder traversal without recursion, using one _Stack_ and one _Queue_
