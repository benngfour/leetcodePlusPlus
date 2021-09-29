## Day 15

### Tree Operation

(<https://leetcode-cn.com/problems/sum-root-to-leaf-numbers/>)

### 思路

1. create a helper function for tracking the sum while traverse the tree (using recursion)
2. call helper function in main function

### 語言

JavaScript

### Code Solution

```
var sumNumbers = function(root) {
    return sumHelper(root, 0)
};

function sumHelper(root, sum){
    if (!root) return 0;
    const total = sum * 10 + root.val;
    if (!root.left && !root.right) {
        return total;
    } else {
        return sumHelper(root.left, total) + sumHelper(root.right, total);
    }
}
```

### 複雜度分析

- 時間複雜度 O(N): Tree Depth (for constrains of this problem, the max depth of the tree is 10, I would say O(10), but that's not practical)
- 空間複雜度 O(N): function recursion
