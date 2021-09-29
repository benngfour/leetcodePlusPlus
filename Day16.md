## Day 16

### Tree Operation

(<https://leetcode-cn.com/problems/find-bottom-left-tree-value/>)

### 思路

Using queue data structure and bfs in tree to get the bottom left node

### 語言

JavaScript

### Code Solution

```
var findBottomLeftValue = function(root) {
    let nodes = [];
    if (root === null) {
        return null;
    }
    nodes.push(root);
    let res;
    while (nodes.length) {
        const len = nodes.length
        for (let i = 0; i < len; i++) {
            let headNode = nodes.shift();
            if(i === 0) {
                res = headNode.val;
            }
            if (headNode.left) {
                nodes.push(headNode.left)
            }
            if (headNode.right) {
                nodes.push(headNode.right)
            }
        }
    }
    return res;
};
```

### 複雜度分析

- 時間複雜度 O(N): Tree Depth
- 空間複雜度 O(1)? Only created an array to store the nodes.
