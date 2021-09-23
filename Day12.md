## Day 12

### LRU Operation

(<https://leetcode-cn.com/problems/lru-cache/>)

### 思路

使用 JavaScript 內置的 Map 數據結構，可以紀錄輸入數據的順序，從而達到題目的要求

### 語言

JavaScript

### Code Solution

```
var LRUCache = function(capacity) {
    this.limit = capacity;
    this.storage = new Map();
};

/**
 * @param {number} key
 * @return {number}
 */
LRUCache.prototype.get = function(key) {
    if (this.storage.has(key)) {
        const val = this.storage.get(key);
        this.storage.delete(key);
        this.storage.set(key, val);
        return val;
    } else {
        return -1;
    }
};

/**
 * @param {number} key
 * @param {number} value
 * @return {void}
 */
LRUCache.prototype.put = function(key, value) {
    if (this.storage.has(key)) {
        this.storage.delete(key);
    }
    this.storage.set(key, value)
    if (this.storage.size > this.limit) {
        this.storage.delete(this.storage.keys().next().value);
    }
};
```

### 複雜度分析

- 時間複雜度: O(1) get and put functions are O(1)
- 空間複雜度 O(N)：it depends on the capacity passed in.
