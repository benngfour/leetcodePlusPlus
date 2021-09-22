## Day 13

### Tree Operation

(<https://leetcode-cn.com/problems/maximum-depth-of-binary-tree/>)

### 思路

Using Recursion to traverse left and right of the tree root, then get the max.

### 語言

JavaScript

### Code Solution

```
var maxDepth = function(root) {
    if (!root) return 0;
    let leftDepth = 1;
    let rightDepth = 1;
    leftDepth += maxDepth(root.left);
    rightDepth += maxDepth(root.right);
    return Math.max(leftDepth, rightDepth);
};
```

### 複雜度分析

- 時間複雜度 O(N): Tree Depth
- 空間複雜度 O(N): function recursion
