---
title: css实现左右横线
date: 2020-12-21 21:05:50
tags: css
---

## 有些场景会需要实现一段文字，左右有居中的横线，然后中间的文字数量不定，但是横线距离文字的距离是保持不变的

eg1:
———— 这里是想要的文字 ————
———— 文字文字 ————
———— 文字 ————

## 解决思路：

第一想法肯定是使用伪类 before after
这个想法是没错的 但是如果把伪类的 diaplay 设置成 block 会出现一个问题 当然 也可能是另一种场景就是需要这样
eg2:
———— 文字文字文字 ————
———— 文字文字 ————
———— 文字 ————

什么意思呢 就是会造成你的伪类永远是在你元素的两边 然后文字居中展示 text-align: center
这样两边的横线到文字的距离是会变得 文字越多 距离越小 文字越少 距离越大
如果要想实现 eg1 的样子就要把伪类的 display 设置成 inline-block
思路就是把左右的横线也当成是文字考虑 比如你写一段话，不管你中间添加了多少个字但是第一个字和最后一个字距离第二个字和倒数第二个字的距离肯定是一样的
（仔细读，可能会比较抽象）
eg3:
横线文字文字文字横线
横线文字文字横线
横线文字横线

大概就是 eg3 的意思 只需要调整一下横线和文字的距离就可以了
具体实现 代码如下：

<!--more-->

html：

```
<div class="title">
    文字文字文字
</div>
```

css： (pr 是我项目中为了适应屏幕自定义的单位可以忽略 根据自己项目来 相当于 rem)

```
.title
    height pr(70)
    line-height pr(70)
    font-size pr(58)
    text-align center
    color #5b2ac1
    overflow hidden
    margin 0 auto
    margin-top pr(84)
    position relative
    font-weight bold
    .title::before {
        content ""
        display inline-block
        width pr(100)
        height pr(3)
        background-color #5b2ac1
        margin-right pr(25)
        margin-bottom pr(18)
    }
    .title::after {
        content ""
        display inline-block
        width pr(100)
        height pr(3)
        background-color #5b2ac1
        margin-left pr(25)
        margin-bottom pr(18)
    }
```
