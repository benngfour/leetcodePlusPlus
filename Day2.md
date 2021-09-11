## Day 2

### Array Operation

(<https://leetcode-cn.com/problems/shortest-distance-to-a-character>)

### 思路

先獲取 input 字符在 s 的所有 index，然後 loop over s 中的字符，計算最短距離，再放入 answer 中

### 語言

JavaScript

### Code Solution

```
var shortestToChar = function(s, c) {
    let answer = [];
    let idx = [];
    for (let i = 0; i < s.length; i++) {
        if (s[i] === c) {
            idx.push(i);
        }
    }
    for (let j = 0; j < s.length; j++) {
        let shortestIdx = s.length;
        for (let k = 0; k < idx.length; k++) {
            shortestIdx = Math.min(Math.abs(j - idx[k]), shortestIdx);
        }
        answer.push(shortestIdx);
    }
    return answer;
};
```

### 複雜度分析

- 時間複雜度 O(N^2): nested for loop
- 空間複雜度 O(2): one answer array, one idx array
