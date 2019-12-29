---
title: 《剑指 offer》 左旋转字符串
top: false
cover: false
toc: true
mathjax: true
date: 2019-12-22 22:19:51
password:
summary:
tags:
- 刷题
- 字符串
categories:
- 剑指 offer
- 刷题
---

## 题目描述

汇编语言中有一种移位指令叫做循环左移（ROL），现在有个简单的任务，就是用字符串模拟这个指令的运算结果。对于一个给定的字符序列S，请你把其循环左移K位后的序列输出。例如，字符序列S=”abcXYZdef”,要求输出循环左移3位后的结果，即“XYZdefabc”。是不是很简单？OK，搞定它！



## 题解

原理：$YX = (X^TY^T)^T$
1.先翻转前半部分
2.再翻转后半部分
3.再对字符串整个进行翻转
## 代码
```js
function LeftRotateString(str, n)
{
    // write code here

    if(str==null||str.length==0){
        return "";
    }
    
    let len=str.length;
    n=n%len;
    str=reverseStr(str.slice(0,n))+str.slice(n);
    str=str.slice(0,n)+reverseStr(str.slice(n));
    str=reverseStr(str);
    return str;
}

function reverseStr(str){
    return str.split("").reverse().join("");
}
```