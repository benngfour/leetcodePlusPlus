## Day 5

### Array Operation

(<https://leetcode-cn.com/problems/implement-queue-using-stacks/>)

### 思路

用 Array 作為數據結構的基礎，然後再使用 JavaScript Array 內置的 function 實現題目的要求

### 語言

JavaScript

### Code Solution

```
/**
 * Initialize your data structure here.
 */
var MyQueue = function() {
    this.queue = [];
};

/**
 * Push element x to the back of queue.
 * @param {number} x
 * @return {void}
 */
MyQueue.prototype.push = function(x) {
    this.queue.push(x);
};

/**
 * Removes the element from in front of queue and returns that element.
 * @return {number}
 */
MyQueue.prototype.pop = function() {
    if (this.queue.length !== 0) {
        return this.queue.shift();
    } else {
        return null;
    }
};

/**
 * Get the front element.
 * @return {number}
 */
MyQueue.prototype.peek = function() {
    if (this.queue.length > 0) {
        return this.queue[0];
    } else {
        return null;
    }
};

/**
 * Returns whether the queue is empty.
 * @return {boolean}
 */
MyQueue.prototype.empty = function() {
    if (this.queue.length === 0) {
        return true;
    } else {
        return false;
    }
};
```

### 複雜度分析

- 時間複雜度: 因為 Peek 使用了 Array 的 shift function， shift function 最差是 O(N)，其餘均是 O(1)
- 空間複雜度 O(1)
