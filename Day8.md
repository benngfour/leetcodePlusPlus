## Day 8

### LinkedList Operation

(<https://leetcode-cn.com/problems/rotate-list/>)

### 思路

Set one more head in front of the original list，loop over the list and swap the nodes.

### 語言

JavaScript

### Code Solution

```
var swapPairs = function(head) {
    if (!head || head.next === null) {
        return head;
    }
    let newHead = new ListNode(0);
    newHead.next = head;
    let temp = newHead;
    while(temp.next && temp.next.next) {
        const node1 = temp.next;
        const node2 = temp.next.next;
        temp.next = node2;
        node1.next = node2.next;
        node2.next = node1;
        temp = node1;
    }
    return newHead.next
};
```

### 複雜度分析

- 時間複雜度: O(N): loop linkedlist once
- 空間複雜度 O(1)： only created newHead
