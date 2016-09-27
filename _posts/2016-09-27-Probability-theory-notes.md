---
layout:    post
title:     统计概率
subtitle:  概率论笔记 1.4
keywords:  math,probability
category:  probability theory
tags:      [math,probability]
mathjax:   true
date:      2016-09-27
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

## 统计概率

### 随机事件的频率

**定义：** 设随机事件A在n次重复实验中出现$$ n_A $$次，则事件A在n次试验中出现的**频率**为$$ f_n(A) = n_A / n $$。易知，随机事件的频率具有以下性质：

  1. 对任意事件A，$$ 0 \le f_n(A) \le 1 $$。
  2. 对必然事件$$ \Omega $$，$$ f_n(\Omega) = 1 $$。
  3. 若$$ A_1, ... , A_k $$为k个不相容事件，则:
  \\[ f_n(\bigcup_{i=1}^{k}A_i) = \Sigma_{i=1}^{k}f_n(A_i) \\]

值得注意的是，随机事件的频率$$ f_n(A) $$是随着试验总次数n而定的数，不可与古典概型的概率相混淆。

### 频率的性质及统计概率

**定义：** 在n次重复进行的随机试验中，当n很大时，事件A出现的频率$$ f_n(A) = \frac{n_A}{n} $$将稳定地在某一数值p附近摆动，且随着试验次数n的增大，摆动的幅度也越来越小，则称该数值p为事件A发生的**概率**，记为：$$ P(A) = p $$。
该定义**概率的频率定义**，其概率称作**统计概率**。
