---
title: 判断 SAC 数据是否已去除仪器响应
date: 2016-03-13
author: SeisMan
categories: SAC
tags: [仪器响应]
---

有些时候，波形数据拿到手了，但是却不知道波形数据是否有被处理过，尤其是有没有去除仪器响应。

先说结论，判断一个 SAC 数据是否已经去除仪器响应的准则是：

> 若一个 SAC 数据中每个数据点的值都是整数，则这个数据的仪器响应没有被去除的概率为 99.9%

<!--more-->

几点说明：

1.  可以使用 [sac2col](https://github.com/seisman/sac_tools)
    将 SAC 的每个数据点提取出一列 ASCII 数据，这样就可以直观的去判断是否符合上述准则
2.  这个准则仅对现代的数字地震仪成立

要理解这个准则成立的原因，首先需要对仪器响应有清晰的认识。在博客的前几篇博文中
已经有了详细的介绍。简单来说，地面的运动物理量（比如速度，单位为 `m/s`）会首先被
转换成电压信号（单位为 `V`），然后每个电压值会被转换成离散的数字信号，数字信号的
最小间隔由模数转换器决定，故而现代数字地震仪的输出的单位总是 `counts`，即最原始的
波形数据总是最小间隔的整数倍。
