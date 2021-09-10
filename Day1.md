## Day 1

### Array Operation

(<https://leetcode-cn.com/problems/add-to-array-form-of-integer/>)

### 思路

從 Array 尾部開始相加，然後計算剩下的；最後檢查 carryOver 的數字

### 語言

JavaScript

### Code Solution

```
var addToArrayForm = function(num, k) {
    let result = [];
    let carryOver = 0;
    const arrK = k.toString().split('');
    let numLen = num.length;
    let kLen = arrK.length;
    if (kLen >= numLen) {
        for (let j = numLen - 1; j >= 0; j--) {
                let kNum = Number(arrK[kLen - 1]);
                let sum = kNum + num[j] + carryOver;
                if (sum < 10) {
                    result.push(sum);
                    carryOver = 0;
                } else {
                    result.push(sum - 10);
                    carryOver = 1;
                }
                kLen--;
        }
        for (let i = kLen - 1; i >= 0; i--) {
            let kNum = Number(arrK[i]);
            if (kNum + carryOver >= 10) {
                result.push((kNum + carryOver) - 10);
                carryOver = 1;
            } else {
                result.push(kNum + carryOver);
                carryOver = 0;
            }
        }
    } else {
        for (let i = kLen - 1; i >= 0; i--) {
            let kNum = Number(arrK[i]);
                let sum = kNum + num[numLen - 1] + carryOver;
                if (sum < 10) {
                    result.push(sum);
                    carryOver = 0;
                } else {
                    result.push(sum - 10);
                    carryOver = 1;
                }
            numLen--;
        }
        for (let j = numLen - 1; j >= 0; j--) {
            if (num[j] + carryOver >= 10) {
                result.push((num[j] + carryOver) - 10);
                carryOver = 1;
            } else {
                result.push(num[j] + carryOver);
                carryOver = 0;
            }
        }

    }
    if (carryOver > 0) {
        result.push(1);
    }
    return result.reverse();
};
```

### 複雜度分析

- 時間複雜度 O(N): 沒有 nested for loop， 時間取決於最大的那個 Array length
- 空間複雜度 O(1): 只佔用 result array
