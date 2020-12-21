---
title: fib斐波那契数
date: 2020-12-21 19:36:36
tags: 算法
---

```jsx
// 方案一：暴力递归
// var fib = function (N) {
//     if (N === 0 || N === 1) {
//         return N;
//     }
//     return fib(N - 1) + fib(N - 2);
// };

// 方案二：递推 使用循环  利用缓存优化重复的计算
var fib = function (N) {
  // O(n)
  let cache = [];
  for (let i = 0; i <= N; i++) {
    if (i === 0 || i === 1) {
      cache[i] = i;
    } else {
      cache[i] = cache[i - 1] + cache[i - 2];
    }
  }
  return cache[N];
};
```
