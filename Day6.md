## Day 6

### Array Operation

(<https://leetcode-cn.com/problems/max-chunks-to-make-sorted-ii/>)

### 思路

參考單調盞

### 語言

JavaScript

### Code Solution

```
class Stack {
    constructor() {
        this.list = [];
    }
    push(value) {
        return this.list.push(value);
    }
    peek() {
        return this.list[this.list.length - 1];
    }
    pop() {
        return this.list.pop();
    }
    size() {
        return this.list.length;
    }
    isEmpty() {
        return this.list.length === 0;
    }
}


/**
 * @param {number[]} arr
 * @return {number}
 */
var maxChunksToSorted = function(arr) {
    const stack = new Stack();
    for (let i = 0; i < arr.length; i++) {
        if (stack.isEmpty() || stack.peek() <= arr[i]) {
            stack.push(arr[i]);
        } else {
            const temp = stack.pop();
            while(stack.peek() > arr[i]) {
                stack.pop()
            }
            stack.push(temp);
        }
    }
    return stack.size();
};
```

### 複雜度分析

- 時間複雜度: O(N)
- 空間複雜度 O(N)
