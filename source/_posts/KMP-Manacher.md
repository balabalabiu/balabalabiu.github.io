---
title: KMP Manacher
date: 2020-07-16 18:48:23
tags: [algorithm,KMP,Manacher]
---

## KMP

实现：String.getIndexOf()应用了kmp，或者其改进

字符串匹配问题

**概念**

+ 子序列 ： 子序列正常不连续

+ 子数组/字串：连续

**暴力法**

+ 时间复杂度$O(N*M)$

**KMP**

概念引入/定义

+ 最长前缀和最长后缀

+ 最长前缀不包括字串最后一个

+ 最长后缀不包含字串第一个字符

当前元素存储的信息，寻找之前字串（不包括当前元素）的最长前缀和最长后缀相等

str1 > str2

next_arr[]：信息数组，和str2长度相同

+ 0位置，之前没有字符串，认为规定-1
+ 1位置，之前字符串长度为1，最长前缀、最长后缀不包括最后一个和第一个，所以人为规定0
+  依次填好之后位置，有一种快速计算的 方法，之后介绍

**KMP实质**

没有否定str1从j位置开始配出str2的可能性，但是省略掉从str1的j到x（即str2的0~z）的配对过程，因为已经根据最长前缀和最长后缀得到了。

j位置之后的并没丢失，

省略了从i到j中间位置都配不出str2，从而加速。正确性很好证明

一直推到最长前缀和最长后缀为0了，说明没有匹配的了str1的i到x，从x+1位置匹配str2的0位置

**题目**

1. 给定字符串s，求解含有两个s的最短字符串。例如"ababa"含有两个"aba"

   解题思路：
   利用kmp求解字符串的最后一个字符的下一个字符的next[]
   处理成最大前缀和最大后缀能重复多少，向尾部添加从最大相同前缀后开始到结尾的子串

2. 二叉树的子结构

   解题思路

   将A、B两树唯一序列化，达到能唯一重建的目的

   在A中查找是否存在B的字串

3. 判断某个字符串是否由一个子字符串重复组成

## Manacher 

马拉车

最长回文子串 

**暴力解**

数组的每个位置开始左右扩展，最后取出最大值

奇数和偶数回文串直接处理需要分开处理奇偶

技巧：在数开头、中间、结尾加入特殊字符（虚数）,都变为奇数了，结果为求得得最大值/2

+ 1 1 -> #1#1		

+ 111 -> #1#1#1#

特殊字符可以是任意字符，因为避过过程中，实数和实数比对，虚数和虚数比对，所以特殊字符是什么不影响结果。

时间复杂度$O(n^2)$

**Manacher** 

概念建立 

回文直径/回文半径

1. 回文半径数组
2. 回文右边界数组
3. 第一次到达回文右边界的中心

**状态分析**

+ i不在回文右边界里面：可能性1->暴力左右扩展

+ i在回文右边界内

  ​		L(----------i'------------C------------i----------)R

  + 可能性2

    L(----------i'------------C------------i----------)R

    L(----$L_i$----i'----$R_i$---C------------i----------)R

    [L,R]包住了  $i'$的回文半径[Li,Ri]   

    i的回文半径  = i’的回文半径

  + 可能性3

    -----------L(---i'------------C------------i---)R----------

    ----$L_i$--*L(---i'-------$R_i$-C------------i---)R&----------

    [L,R]没有包住  $i'$的回文半径[Li,Ri]   

    i的回文半径  = [i,R]*2

  + 可能性4

    -----------L(---i'------------C------------i---)R----------

    ----------$L_i$---i'---$R_i$------C------------i---)R----------

    [L,R]没有包住  $i'$的回文半径[Li,Ri] 出现 重叠，

    i的回文半径 $\geq$ i‘的回文半径,需要比对，但是i到R是不需要计算的，因为由之前的i'可以得到

**题目**

给定一个字符串str1，只能往str1的后面添加字符变成str2,要求str2整体都是回文串且最短