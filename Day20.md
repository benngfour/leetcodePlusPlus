## Day 20

### Hash Table

(<https://leetcode-cn.com/problems/top-k-frequent-elements/>)

### 思路

1. use hash table to get the frequency of each number
2. use Set to create an array with non-repeat number from nums array
3. sort the array by the hash value, then slice to k.

### 語言

JavaScript

### Code Solution

```
var topKFrequent = function(nums, k) {
    let hash = {};
    for(const num of nums) {
        if (!hash[num]) {
            hash[num] = 1
        } else {
            hash[num] += 1;
        }
    }
    const uniqeNums = [...new Set(nums)];
    uniqeNums.sort((a,b) => hash[b] - hash[a])
    return uniqeNums.slice(0, k);
};
```

### 複雜度分析

- 時間複雜度 O(NlogN)
- 空間複雜度 O(N)
