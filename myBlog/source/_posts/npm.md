---
title: npm
date: 2020-12-17 22:24:15
tags: 工程化
---
## 核心目标：Bring the best of open source to you, your team and your company （给你和你的团队、你的公司带来最好的开源库和依赖。）  注重安装和维护依赖

## 安装机制

会优先安装依赖包到当前项目目录，使得不同应用项目的依赖各成体系，同时还减轻了包作者的 API 兼容性压力，但这样做的缺陷也很明显：如果我们的项目 A 和项目 B，都依赖了相同的公共库 C，那么公共库 C 一般都会在项目 A 和项目 B 中，各被安装一次。这就说明，同一个依赖包可能在我们的电脑上进行多次安装。

当然，对于一些工具模块比如 supervisor 和 gulp，你仍然可以使用全局安装模式，这样方便注册 path 环境变量，我们可以在任何地方直接使用 supervisor、 gulp 这些命令。（不过，一般还是建议不同项目维护自己局部的 gulp 开发工具以适配不同项目需求。）

![](/images/npm.jpg)


## 参考文献：LucasHC（侯策） https://kaiwu.lagou.com/course/courseInfo.htm?courseId=584#/detail/pc?id=5906
