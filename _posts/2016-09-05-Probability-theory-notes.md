---
layout:    post
title:     随机事件及其运算
subtitle:  概率论笔记 1.1
keywords:  math,probability
category:  probability theory
tags:      [math,probability]
mathjax:   true
date:      2016-09-05
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

## 随机事件及其运算

### 随机试验和随机事件

所谓**随机试验**是指具有以下三个特点的试验：

  1. 试验可在相同的条件下重复进行；

  2. 试验的所有结果事先是明确可知的，且不止一个；

  3. 每次试验恰好出现可能结果中的一个，但试验前无法预知到底出现那一结果。

我们将随机试验简称为**试验**。

在试验中，每个可能的结果成为**基本事件**，又称**样本点**，记为$$ {\omega}_0 $$，基本事件的全体，即实验中所有可能的结果组成的集合为**试验**的**样本空间**，记为$$ \Omega $$。

由单个或多个事件组成的集合成为**随机事件**，简称**事件**，通常用大写字母$$ A B C $$表示。

一个随机事件对应一个样本空间的一个子集。在随机试验中，若发生的结果是事件$$ A $$包含的事件$$ \omega $$就称**事件$$ A $$发生**，记为$$ \omega \in A $$。

**必然事件**：每次试验必然发生。**不可能事件**：每次试验都不会发生。

### 事件间的关系和运算

下面的讨论总认为是在给定的样本空间**$$ \Omega $$**上进行，其中，**$$ A B C $$**等是**$$ \Omega $$**上的事件。

1. **B包含A**： 若A的发生必定导致B的发生，则称B包含A，记为 $$ B \supset A $$ 或 $$ A \subset B $$。

2. **A等于B**： 若$$ B \supset A $$ 或 $$ A \supset B $$。则称事件A与事件B相等，记为$$ A = B $$。

3. **A与B的并**： 事件A与事件B中至少有一个发生所组成的事件称为事件A与B的并，记为$$ A \cup B $$。

4.  **A与B的交**： 事件A与事件B同时发生所组成的事件称为事件A与B的交，记为$$ A \cap B $$。

5.  **A与B的差**： 事件A发生而事件B不发生所组成的事件称为事件A与B的差，记为$$ A - B $$。

6. **A的对立事件**： 对事件A，所有不属于事件A的基本事件所组成的事件称为事件A的对立事件。记为$$ \overline{A} $$，即$$ \Omega - A $$。

7. **A与B互不相容**： 若A和B不能同时发生，则称A和B是互不相容，即$$ A \cap B = \phi $$。

我们用下图直观地表示事件间的关系和运算。矩形表示样本空间E，圆表示事件。（图片来源：[http://liyuans.net/](http://liyuans.net/%E9%9B%86%E5%90%88%E7%9F%A5%E8%AF%86%E7%B3%BB%E5%88%97%E4%BA%8C%EF%BC%9A%E9%9B%86%E5%90%88%E7%9A%84%E8%BF%90%E7%AE%97%E5%8F%8A%E6%96%87%E6%B0%8F%E5%9B%BE/)侵删。

![](/images/images/math/set.jpg)

事件的运算满足以下规则：

  1. **交换律**：  $$ A \cup B = B \cup A; A \cap B = B \cap A; $$
  2. **结合律**：  $$ (A \cup B) \cup C = A \cup (B \cup C);  (A \cap B) \cap C = A \cap (B \cap C); $$
  3. **分配律**：  $$ A \cup (B \cap C) = (A \cup B) \cap (A \cup C);  A \cap (B \cup C) = (A \cap B) \cup (A \cap C); $$
  4. **De Morgen律（对偶）**：  $$ \overline{A \cup B} = \overline{A} \cap \overline{B};  \overline{A \cap B} = \overline{A} \cup \overline{B}; $$
