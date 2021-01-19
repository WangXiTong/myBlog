---
title: js实现链表反转
date: 2021-01-19 15:42:19
tags: 算法
---

```
// 引用了上一篇博文中的一些方法，具体可看上一篇
import { Node, LinkNodeList } from "./LinkNode.js";

Object.assign(LinkNodeList.prototype, {
  reversal() {
    let prev = null;
    let cur = this.head;
    while (cur) {
      const next = cur.next;
      cur.next = prev;
      prev = cur;
      cur = next;
    }
    this.head = prev;
  },
});
let linkNode = new LinkNodeList();
linkNode.append("0000");
linkNode.append("1111");
linkNode.append("2222");
linkNode.append("3333");
linkNode.append("4444");
linkNode.print();
linkNode.reversal();
linkNode.print();

```
