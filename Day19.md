## Day 19

### Hash Table

(<https://leetcode-cn.com/problems/maximum-depth-of-binary-tree/>)

### 思路

1. create object hast table, loop over the input array
2. number of array as key, index as value
3. if key = target - nums[i] exist, result is hash[target - nums[i] and i 

### 語言

JavaScript

### Code Solution

```
var twoSum = function(nums, target) {
    if (nums.length === 2) {
        return [0, 1];
    }
    let hash = {}
    for (let i  = 0; i < nums.length; i++) {
        if (hash[target - nums[i]] !== undefined) {
            return [hash[target - nums[i]], i];
        }
        hash[nums[i]] = i;
    }
    return [];
};
```

### 複雜度分析

- 時間複雜度 O(N): loop the array
- 空間複雜度 O(1): hash table 
