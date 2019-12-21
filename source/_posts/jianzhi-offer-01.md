---
title: 《剑指 offer》 跳台阶
top: false
cover: false
toc: true
mathjax: true
date: 2019-12-14 15:56:14
password:
summary:
tags: 
- 刷题 
- 递归
categories: 
- 刷题
- 剑指 offer
---

# 题目

一只青蛙一次可以跳上1级台阶，也可以跳上2级。求该青蛙跳上一个n级的台阶总共有多少种跳法（先后次序不同算不同的结果）。

# 题解

对于第n个台阶来说，只能从n-1或者n-2的台阶跳上来，所以
`F(n) = F(n-1) + F(n-2)`
斐波拉契数序列，初始条件
n=1:只能一种方法
n=2:两种
递归一下就好了

```js
function jumpFloor(number)
{

     if(number <= 0)
            return 0;
        else if(number == 1)
            return 1;
        else if(number == 2)
            return 2;
        else
            return jumpFloor(number-1) + jumpFloor(number-2);
}
```