## Day 14

### Tree Operation

(<https://leetcode-cn.com/problems/same-tree>)

### 思路

Set up base case, then recurse function to traverse the tree.

### 語言

JavaScript

### Code Solution

```
var isSameTree = function(p, q) {
    if (!q && !p) return true;
    if (!q || !p) return false;
    if (q.val !== p.val) return false;
    return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
};
```

### 複雜度分析

- 時間複雜度 O(N): Tree Depth
- 空間複雜度 O(N): function recursion
