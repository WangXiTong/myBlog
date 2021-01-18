---
title: js实现链表的增删改查
date: 2021-01-18 10:53:29
tags: 算法
---

# 大家都知道 js 不像 c、Java 等可以直接操作链表、树等结构，所以只能自己模拟，下边简单实现一下 js 操作基本单向链表的增删改查

```
// 先实现一个node类 把普通的元素变成一个节点 拥有element和next
class Node {
  constructor(element) {
    this.element = element;
    this.next = null;
  }
}

// 实现链表的类
class LinkNodeList {
  constructor() {
    // 链表的第一个元素
    this.head = null;
    this.length = 0;
  }
  // 增删改查
  // 增
  append(element, index) {
    let node = new Node(element);
    let cur;

    // 两种情况  1、链表是空的   2、 不是空的
    if (this.head == null) {
      // 链表是空的 head 是第一个
      this.head = node;
    } else {
      // 链表非空
      cur = this.head;
      let i = 0;
      let prev;
      if ((index && index <= this.length) || index == 0) {
        // 传入index 说明是在第index插入
        if (index == 0) {
          node.next = cur;
          this.head = node;
        } else {
          while (i < index) {
            prev = cur;
            cur = cur.next;
            i++;
          }
          node.next = cur;
          prev.next = node;
        }
      } else {
        // 没传入index   或者index大于链表长度   从末尾添加
        // 遍历链表
        while (cur.next) {
          cur = cur.next;
        }
        cur.next = node;
      }
    }
    this.length += 1;
  }
  // 删
  removeAt(index) {
    // 上一个节点指向下一个节点
    // 把自己的下一个节点指向取消
    let cur = this.head;
    let prev;
    let i = 0;
    if (index > this.length || index < 0) {
      return;
    }
    if (index == 0) {
      // 删除第一项
      this.head = cur.next;
    } else {
      while (i < index) {
        // 上一个和当前都需要保存
        prev = cur;
        cur = cur.next;
        i++;
      }
      prev.next = cur.next;
      cur.next = null;
    }
    this.length -= 1;
    return cur.element;
  }
  // 改
  changeAt(element, index) {
    let node = new Node(element);
    let cur;
    if (this.head == null) {
      this.head = node;
    } else {
      cur = this.head;
      let i = 0;
      if ((index && index <= this.length) || index == 0) {
        while (i < index) {
          cur = cur.next;
          i++;
        }
        cur.element = node.element;
      } else {
        // 没传入index   或者index大于链表长度  抛出异常
        console.error("请传入合理的index");
      }
    }
  }
  // 查
  findAt(index) {
    // let node = new Node(element);
    let cur;
    if (this.head == null) {
      console.log("空链表");
    } else {
      cur = this.head;
      let i = 0;
      if ((index && index <= this.length) || index == 0) {
        while (i < index) {
          cur = cur.next;
          i++;
        }
        console.log("目标element", cur.element);
      } else {
        // 没传入index   或者index大于链表长度  抛出异常
        console.error("请传入合理的index");
      }
    }
  }
  // 打印链表
  print() {
    let cur = this.head;
    let ret = [];
    while (cur) {
      ret.push(cur.element);
      cur = cur.next;
    }
    console.log(ret.join("==>"));
    return ret.join("==>");
  }
}

let linkNode = new LinkNodeList();
linkNode.append("0000");
linkNode.append("1111");
linkNode.append("2222");
linkNode.append("3333");
// linkNode.append("插入222", 2);
// linkNode.append("插入333", 3);
// linkNode.append("插入888", 88);
// linkNode.append("插入000", 0);
// linkNode.append("插入-1", -1);
// linkNode.changeAt("替换000", 0);
// linkNode.changeAt("替换111", 1);
// linkNode.changeAt("替换222", 2);
// linkNode.changeAt("替换888", 8);
linkNode.findAt(1);
linkNode.findAt(2);
linkNode.findAt(66);
linkNode.print();
// linkNode.removeAt(-111);
// linkNode.print();

```
