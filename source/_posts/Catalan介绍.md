---
title: Catalan介绍
date: 2020-07-16 01:01:22
tags:
mathjax: true
---

# 卡特兰数

卡特兰数定义
$$
Catalan_n = \sum_{i=1}^{n-1} Catalan_i * Catalan_{n-i}
$$
通项公式
$$
Catalan_n = \frac{1}{n+1}C_{2n}^{n}
$$
或
$$
Catalan_n = C_{2n}^{n} - C_{2n}^{n+1}
$$
递推关系[参考](https://blog.csdn.net/pallypally/article/details/8102557)
$$
Catalan_n = \frac{4n-2}{n+1}Catalan_{n-1}
$$




## 练习题型

[参考](https://blog.csdn.net/astpu84200/article/details/101642136?utm_medium=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase)

[参考](https://blog.csdn.net/weixin_40688217/article/details/94750175)

[参考](https://www.cnblogs.com/zyt1253679098/p/9190217.html)

[证明](https://blog.csdn.net/hemeinvyiqiluoben/article/details/11320419)



\1. 出栈次序

\2. 01序列

\3. ‘+1’ ‘-1’序列

\4. 括号序列

\5. 找零问题

\6. 矩阵链乘

\7. 二叉树计数

\8. 凸多边形划分

\9. 圆上n条线段

\10. 单调路径

\11. 填充阶梯图形

\12. 摞碗问题

\13. 汽车胡同加油问题

\14. 还书借书问题

\15. 高矮排队问题

#### [96. 不同的二叉搜索树](https://leetcode-cn.com/problems/unique-binary-search-trees/)