## Day 17

### Tree Operation

(<https://leetcode-cn.com/problems/serialize-and-deserialize-binary-tree/>)

### 思路

Using bfs-preorder to serialize the tree, same way apply to the deserialize function.

### 語言

JavaScript

### Code Solution

```
var serialize = function(root) {
    return serializeHelper(root, '')
};
function serializeHelper(root, str) {
    if (root === null) {
        str += 'None,'
    } else {
        str = str + root.val + ',';
        str = serializeHelper(root.left, str);
        str = serializeHelper(root.right, str);
    }
    return str;
}

var deserialize = function(data) {
    const dataArr = data.split(',')
    return deserializeHelper(dataArr)
};
function deserializeHelper(dataArr) {
    if (dataArr[0] === "None") {
        dataArr.shift();
        return null;
    }
    const root = new TreeNode(Number(dataArr[0]));
    dataArr.shift();
    root.left = deserializeHelper(dataArr);
    root.right = deserializeHelper(dataArr);
    return root;
}
```

### 複雜度分析

- 時間複雜度 O(N): Tree Depth
- 空間複雜度 O(N)
