---
title: 《剑指 offer》 和为s的正整数序列
top: false
cover: false
toc: true
mathjax: true
date: 2019-12-22 17:12:03
password:
summary:
tags:
- 刷题
- 穷举
categories:
- 刷题
- 剑指 offer
---

## 题目

小明很喜欢数学,有一天他在做数学作业时,要求计算出9~16的和,他马上就写出了正确答案是100。但是他并不满足于此,他在想究竟有多少种连续的正数序列的和为100(至少包括两个数)。没多久,他就得到另一组连续正数和为100的序列:18,19,20,21,22。现在把问题交给你,你能不能也很快的找出所有和为S的连续正数序列? Good Luck!

## 输出描述

输出所有和为S的连续正数序列。序列内按照从小至大的顺序，序列间按照开始数字从小到大的顺序

## 题解
双指针技术，就是相当于有一个窗口，窗口的左右两边就是两个指针，我们根据窗口内值之和来确定窗口的位置和宽度。非常牛逼的思路，虽然双指针或者所谓的滑动窗口技巧还是蛮常见的，但是这一题还真想不到这个思路。
两个窗口都是从左边出发，不是两边夹逼。另外，当小于目标数时high++；大于目标数时low++，如果是high--，那么你仔细想想，你的窗口还怎么往后移动，整个结果在第一次大于目标数之后就不会往后移动，相反，而是在在这个low和high之间夹逼试探，最终啥都找不到或者只能找到一个。
### 具体做法
（1）两个起点，相当于动态窗口的两边，根据其窗口内的值的和来确定窗口的位置和大小
（2）相等，那么就将窗口范围的所有数添加进结果集
（3）如果当前窗口内的值之和小于sum，那么窗口右侧边界右移一下
（4）如果当前窗口内的值之和大于sum，那么窗口左侧边界右移一下
判定是否循环条件是窗口的左侧小于右侧。
## 代码
```js
function FindContinuousSequence(sum)
{
    // write code here
    let result=[];//存储结果
    let low=1,heigh=2;
    while(low<heigh){
        //由于是连续的，差为1的一个序列，那么求和公式是(a0+an)*n/2
        let currSum=(low+heigh)*(heigh-low+1)/2;
        if(currSum==sum){
            let tempRes=[];
            for(let i=low;i<=heigh;i++){
                tempRes.push(i);
            }
            result.push(tempRes);
            low++;
        }else if(currSum<sum){
            heigh++;
        }else{
            low++;
        }
    }
    return result;
}
```