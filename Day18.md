## Day 17

### Tree Operation

(<https://leetcode-cn.com/problems/vertical-order-traversal-of-a-binary-tree/>)

### 思路

1. inorder traverse the tree to get the column, row, value array
2. sort the array
3. generate the result array based the sorted array

### 語言

JavaScript

### Code Solution

```
var verticalTraversal = function(root) {
    let nodes = [];
    getNodesArr(root, 0, 0, nodes);
    // sort by col first, then row, then node.val
    nodes.sort((a, b) => a[0] - b[0] || a[1] - b[1] || a[2] - b[2]);
    // generate result array
    let res = [];
    let minCol = -Infinity;
    for (const node of nodes) {
        const col = node[0];
        const val = node[2];
        if (col !== minCol) {
            minCol = col;
            res.push([]);
        }
        res[res.length - 1].push(val)
    }
    return res;

};

function getNodesArr(root, row, col, nodes) {
    if (root) {
        getNodesArr(root.left, row + 1, col - 1, nodes);
        nodes.push([col, row, root.val]);
        getNodesArr(root.right, row + 1, col + 1, nodes);
    };
}
```

### 複雜度分析

- 時間複雜度 O(NlogN)
- 空間複雜度 O(N)
