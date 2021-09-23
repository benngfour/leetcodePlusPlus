## Day 7

### LinkedList Operation

(<https://leetcode-cn.com/problems/rotate-list/>)

### 思路

1.找 LinkedList 的 Length，k 如果是 length 的倍數就會跟原本的一樣 2.找到需要停下的點，開始 loop over linkedlist，數到點之後斷開
3.return newHead

### 語言

JavaScript

### Code Solution

```
var rotateRight = function(head, k) {
    if (head === null) {
        return null;
    }
    let len = 1;
    let dummyHead = head;
    while (dummyHead.next !== null) {
        len++;
        dummyHead = dummyHead.next;
    }
    let stopPos = len - k % len;

    if (k === len || stopPos === len || k ===0 || len === 1) {
        return head;
    }
    dummyHead.next = head;

    while (stopPos) {
        dummyHead = dummyHead.next;
        stopPos--;
    }

    const newHead = dummyHead.next;
    dummyHead.next = null;

    return newHead;
};
```

### 複雜度分析

- 時間複雜度: O(N): loop linkedlist once
- 空間複雜度 O(1)： only created dummyHead
