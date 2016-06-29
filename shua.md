##Dynamic Programming
#####QA
1. [动态规划十问十答](http://chuansong.me/n/1543583)
2. [yuanbin Dynamic Programming](http://algorithm.yuanbin.me/zh-hans/dynamic_programming/)

#####Questions
1. [Palindrome Partitioning II](http://www.lintcode.com/en/problem/palindrome-partitioning-ii/)
2. [Word Break](http://www.lintcode.com/en/problem/word-break/)


##Binary Tree & Divide Conquer
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

####BFS
6. [Binary Tree Level Order Traversal](http://www.lintcode.com/en/problem/binary-tree-level-order-traversal/#)
7. [Binary Tree Level Order Traversal II](http://www.lintcode.com/en/problem/binary-tree-level-order-traversal-ii/#)
7. [Binary Tree Zigzag Level Order Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)

####Binary Search Tree
8. [Validate Binary Search Tree](http://www.lintcode.com/en/problem/validate-binary-search-tree/#)
  1. [Online Solution](http://algorithm.yuanbin.me/zh-hans/binary_search_tree/validate_binary_search_tree.html)
10. [Inorder Successor in Binary Search Tree](http://www.lintcode.com/en/problem/inorder-successor-in-binary-search-tree/)
11. [Binary Search Tree Iterator](http://www.lintcode.com/en/problem/binary-search-tree-iterator/)
