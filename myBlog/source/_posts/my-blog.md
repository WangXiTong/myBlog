---
title: 2sum
date: 2020-12-16 20:05:34
tags: 算法
---


# 描述：

```js
[1, 2, 4, 3, 6]
7
```

# 思路一：暴力解法

双重循环   时间复杂度O(n²)   空间复杂度  O(1)

```js
var twoSum = function (nums, target) {
    // const arr = [];
    for (let i = 0; i < nums.length; i++) {
        for (let j = i + 1; j < nums.length; j++) {
            if (nums[i] + nums[j] === target) {
                // 只能输出一种结果  
                // return new Array(i, j);
            }
        }
    }
    // 可以把所有可能的结果都进行输出
    arr.push(new Array(i, j));
    return arr;
};

const targetArr = [1, 2, 4, 3, 6];
const targetNum = 7;

console.log(twoSum(targetArr, targetNum));

// 输出  [ [ 0, 4 ], [ 2, 3 ] ]
```
<!--more-->
# 思路二：空间换时间

1 缺 6
2 缺 5
4 缺 3

## 使用indexOf  但是复杂度略高

```js
var twoSum = function (nums, target) {
    const arr = [];
    for (let i = 0; i < nums.length; i++) {
        if (nums.indexOf(target - nums[i]) > -1) {
            // 只能输出一种结果
            // return new Array(i, nums.indexOf(target - nums[i]));

            arr.push(new Array(i, nums.indexOf(target - nums[i])));
        }
    }
    // 输出所有可能的结果
    return arr;
}

const targetArr = [1, 2, 4, 3, 6];

console.log(twoSum(targetArr, 7));

// 输出 [ [ 0, 4 ], [ 2, 3 ], [ 3, 2 ], [ 4, 0 ] ]
```

## 不使用indexOf 
```jsx
// 时间复杂度 O(n)    但是使用了object  所以占用空间  空间复杂度O(n)
var twoSum = function(nums, target) {
    const obj = {};
    for (let i = 0; i < nums.length; i++) {
        const num = nums[i];
        if (num in obj) {
            return [obj[num], i];
        } else {
            obj[target - num] = i
        }
    }
}
```