---
title: 《剑指 offer》 扑克牌顺子
top: false
cover: false
toc: true
mathjax: true
date: 2019-12-29 13:46:58
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

LL今天心情特别好,因为他去买了一副扑克牌,发现里面居然有2个大王,2个小王(一副牌原本是54张^_^)...他随机从中抽出了5张牌,想测测自己的手气,看看能不能抽到顺子,如果抽到的话,他决定去买体育彩票,嘿嘿！！“红心A,黑桃3,小王,大王,方片5”,“Oh My God!”不是顺子.....LL不高兴了,他想了想,决定大\小 王可以看成任何数字,并且A看作1,J为11,Q为12,K为13。上面的5张牌就可以变成“1,2,3,4,5”(大小王分别看作2和4),“So Lucky!”。LL决定去买体育彩票啦。 现在,要求你使用这幅牌模拟上面的过程,然后告诉我们LL的运气如何， 如果牌能组成顺子就输出true，否则就输出false。为了方便起见,你可以认为大小王是0。

## 题解
这道题的思路很简单，0可以作为任意数字，那么我们有以下几种情况。
- 不是顺子的情况
1. 如果出现对子，则肯定不是顺子
2. 如果数组为空，肯定不是顺子
- 是顺子的情况
1. 排序后相邻数字间隔总数`（间隔为1的记0）`等于0的个数，那就说明是顺子。
2. 还有一种情况就是没有0，原本就是顺子，上面的判断条件依然起效，无须再过多判断。
### 解题过程
1. 判断是否为空
2. 排序
3. 计算0的个数
4. 计算所有相邻数字的间隔总数
5. 如果`3>=4`那就是顺子
6. 如果出现对子，则不是顺子
具体见下方代码
## 代码
```js
function IsContinuous(numbers)
{
    // write code here
  
    if(numbers.length==0){
        return false;
    }
    numbers=numbers.sort();
    let numberZero=0;//0的个数
    let gapNum=0;//间隔总数
    
    for(let i=0;i<numbers.length-1;i++){
        if(numbers[i]==0){
            //统计王的个数
            numberZero++;
            continue;
        }
        if(numbers[i]==numbers[i+1]){
            //出现对子
            return false;
        }
        gapNum+=numbers[i+1]-numbers[i]-1;//间隔等于1则不计算
        
    }
    if(numberZero>=gapNum){
       return true;
    }
    return false;
    
}
```