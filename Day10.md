## Day 10

### LinkedList Operation

(<https://leetcode-cn.com/problems/intersection-of-two-linked-lists/>)

### 思路

兩個LinkedList一起遍歷，檢測兩個nodes是否相等，其中一個到了盡頭就到另外一個遍歷。

### 語言

JavaScript

### Code Solution

```
var getIntersectionNode = function(headA, headB) {
    if (!headA || !headB) return null;
    let a = headA, b = headB;
    while (a !== b) {
        a = !a ? headB : a.next;
        b = !b ? headA : b.next;
    }
    return a;
};
```

### 複雜度分析

- 時間複雜度: O(N): loop linkedlist once
- 空間複雜度 O(1)：
