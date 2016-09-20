---
layout:    post
title:     概率论笔记 1.2
subtitle:  古典概率
keywords:  math,probability
category:  probability theory
tags:      [math,probability]
mathjax:   true
date:      2016-09-06
author:     "BINISM"
header-img:  /images/pages/probability.jpg
---

---

* derived from  《概率论与数理统计》 高祖新、陈华均

---


---

## 目录
{: .no_toc}

* 目录
{:toc}

---

## 古典概率

### 古典概率与古典概型

**定义1.1**： 随机事件A发生的可能性大小的数值度量就称为**事件A发生的概率**，记作$$ P(A) $$。

首先来考虑一类最简单的随机现象，它具有以下特点：

  1. 它的基本事件为有限个，设为$$ {\omega}_1,....,{\omega}_n $$，则$$ \Omega = \{ \omega_1,....,\omega_n \}; $$

  2. 每个基本事件的出现是等可能的。

这类随机现象的数学模型称为**古典概型**，这是因为它们是概率论发展初期所研究的主要对象。

对于古典概型，我们有

**定义1.2**： 设随机试验为古典概型，其样本空间为$$ \Omega = \{ \omega_1,....,\omega_n \} $$，若事件A由m个基本事件构成，则事件A的概率为：
\\[ P(A) = \frac\{m\}\{n\} = \frac\{A所包含的基本事件数\}\{基本事件数\} \\]
该定义即为**概率的古典定义**，简称**古典概率**。

### 古典概率的性质

对于古典概型而言，其样本空间$$ \Omega = \{ \omega_1,....,\omega_n \} $$是个必然事件，它发生的可能性为1。又由于每个事件$$ \omega_i $$发生的可能性相同，都为$$ \frac{1}{n} $$。即：$$ P( \omega_1 ) =  P( \omega_2 ) = .... =P( \omega_n ) = \frac{1}{n}, $$
有因事件A含m个基本事件，不妨设：
$$ A = {\omega}_{i_1},....,{\omega}_{i_n} $$
则：
\\[ P(A) = P(\{ \omega_{i_1}\}) +  P(\{ \omega_{i_2}\}) + .... + P(\{ \omega_{i_m}\}) = \frac{1}{n} + \frac{1}{n} + \frac{1}{n} + .... = \frac{m}{n} \\]
这就得到了古典概率的定义公式。由该定义公式，不难得到古典概率的基本性质：

  1. 对于任意事件A，$$ 0 \le P(A) \le 1 $$。

  2. $$ P(\Omega) = 1, P(\phi) = 0 $$；

  3. 若事件$$ A_1, .... , A_K $$互不相容，则：
  \\[ P(\bigcup_{i=1}^{k}A_i) = \sum_{i=1}^{k}P(A_i) \\]
