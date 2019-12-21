---
title: 《剑指 offer》 和为s的两个数字
top: false
cover: false
toc: true
mathjax: true
date: 2019-12-21 19:59:04
password:
summary:
tags:
- 刷题
- 递归
- 数学
categories:
- 刷题
- 剑指 offer
---

## 题目

输入一个递增排序的数组和一个数字S，在数组中查找两个数，使得他们的和正好是S，如果有多对数字的和等于S，输出两个数的乘积最小的。

## 输出描述:

对应每个测试案例，输出两个数，小的先输出。

## 题解

数列满足递增，设两个头尾两个指针i和j，
若ai + aj == sum，就是答案（相差越远乘积越小）
若ai + aj > sum，aj肯定不是答案之一（前面已得出 i 前面的数已是不可能），j -= 1
若ai + aj < sum，ai肯定不是答案之一（前面已得出 j 后面的数已是不可能），i += 1
O(n)

## 代码
```js
function FindNumbersWithSum(array, sum)
{
    // write code here
    let i=0;
    let j=array.length-1;
    let res=[];
    while(i<j){
        let temp=array[i]+array[j];
        if(temp==sum){
            res=[array[i],array[j]];
            break;
        }else if(i<j&&temp>sum){
            j--;
        }else{
            i++;
        }
    }
    return res;
}
```