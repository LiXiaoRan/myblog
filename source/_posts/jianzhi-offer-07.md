---
title: 《剑指 offer》不用加减乘除做加法
top: false
cover: false
toc: true
mathjax: true
date: 2020-01-15 22:55:35
password:
summary:
tags:
- 刷题
- 进制转化
categories:
- 刷题
- 剑指offer
---

## 题目

写一个函数，求两个整数之和，要求在函数体内不得使用+、-、*、/四则运算符号。





## 题解

两个数异或：相当于每一位相加，而不考虑进位；
两个数相与，并左移一位：相当于求得进位；
将上述两步的结果相加

## 代码
```js
function Add(num1, num2)
{
    // write code here
    while( num2!=0 ){
        let sum = num1 ^ num2;
        let carray = (num1 & num2) << 1;
        num1 = sum;
        num2 = carray;
    }
    return num1;
}
```