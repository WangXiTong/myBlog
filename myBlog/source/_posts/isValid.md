---
title: isValid 有效的括号
date: 2020-12-21 20:06:40
tags: 算法
---

# 描述

给定一个只包括 '('，')'，'{'，'}'，'['，']'  的字符串，判断字符串是否有效。

有效字符串需满足：

左括号必须用相同类型的右括号闭合。
左括号必须以正确的顺序闭合。
注意空字符串可被认为是有效字符串。

# 示例

```
输入: "()"
输出: true

输入: "()[]{}"
输出: true

输入: "(]"
输出: false

输入: "([)]"
输出: false

输入: "{[]}"
输出: true
```

# 思路

```
var isValid = function (s) {
    // 1、定义一个栈 利用栈的概念分析 先看目标字符串元素是不是左括号，如果是 则入栈 然后看下一个
    // 2、如果不是 看栈的长度是否为0 如果为0的话说明没有左括号元素直接就是右括号 肯定不合规 直接 return false
    // 3、判断当前元素和栈顶元素是否匹配，如果匹配说明是一组合法括号 把栈顶元素弹出 并继续看下一个 如果不匹配 则直接return false
    // 4、循环结束之后判断栈里是否还有元素，如果没有则说明完全匹配 否则 return false
    const cache = [];
    const map = new Map();
    map.set("(", ")");
    map.set("[", "]");
    map.set("{", "}");
    for (let i = 0; i < s.length; i++) {
        if (map.has(s[i])) {
            // 元素是左括号  入栈
            cache.push(s[i]);
        } else {
            // 元素不是左括号
            if (cache.length === 0) {
                // 步骤2
                // 栈里没有左括号 直接来了一个右括号 直接return false
                return false;
            }
            if (map.get(cache[cache.length - 1]) === s[i]) {
                // 步骤3
                cache.pop();
            } else {
                return false;
            }
        }
    }
    // 步骤4
    if (cache.length) {
        return false;
    }
    return true;
};
```
