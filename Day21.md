## Day 21

### Hash Table

(<https://leetcode-cn.com/problems/number-of-boomerangs/>)

### 思路

暴力法

### 語言

JavaScript

### Code Solution

```
var numberOfBoomerangs = function(points) {
    if (points.length < 3) {
        return 0;
    }
    let res = 0;
    for (const point1 of points) {
        const hash = new Map();
        for (const point2 of points) {
            const dis = getDis(point1, point2);
            hash.set(dis, (hash.get(dis) || 0) + 1);
        }
        for (const entry of hash.entries()) {
            res += entry[1]*(entry[1] - 1)
        }
    }
    return res;
};

function getDis(tuple1, tuple2) {
    return Math.sqrt((tuple1[0] - tuple2[0])**2 + (tuple1[1] - tuple2[1])**2);
}
```

### 複雜度分析

- 時間複雜度 O(N^2): nested loop
- 空間複雜度 O(N)
