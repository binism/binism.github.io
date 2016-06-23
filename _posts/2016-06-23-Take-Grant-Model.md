---
layout:    post
title:     取予（Take-Grant）保护模型
keywords:  security,system
category:  security
tags:      [security,system]
---
# 取予（Take-Grant）保护模型

* 作者：BINISM

* 转载需注明出处

---

## 取予模型定义
取予（take-Grant）保护模型使用有向图的形式来表示系统，称这样的有向图为保护图。

**节点**
可以是主体或客体。节点可能是主体或客体的。

$$
\left( \sum_{k=1}^n a_k b_k \right)^{\!\!2} 
\leq 
\left( \sum_{k=1}^n a_k^2 \right) 
\left( \sum_{k=1}^n b_k^2 \right)
$$

![取予模型节点](/images/images/security/take-grant-pic1.png)
边都标记为从源点到目标节点的权限。权限就是预定义的集合R，R含有两个特殊权限
![取予模型特殊边的定义](/images/images/security/take-grant-pic2.png)
**Take规则：**
设x，y和z是保护图G0的三个不同节点，并且x是一个主体。设x到z有一条标记为 $\gamma$ 的边，且 $t\in\gamma$ ,z到y有一条边 $\beta$ 且 $\alpha\subseteq\beta$ 。Take规则定义了一个新图G1，新图在原有的保护图上加入了一条x到y的标记为 $\alpha$ 的边。从图上看，这条规则被写为“x从y中取得了到y的权限 $\alpha$ ”。

![Take G0](/images/images/security/take-grant-pic3.png) 

![Take G1](/images/images/security/take-grant-pic4.png)

表示成G0├─ G1 ：“x从y中取得了到y的权限 $\alpha$ ”

**Grant规则:**
设x，y和z是保护图G0的三个不同节点，并且z是一个主体。设z到x有一条标记为 $\gamma$ 的边，且 $g\in\gamma$ ，z到y有一条边 $\beta$ ，且 $\alpha\subseteq\beta$ 。Grant规则定义了一个新图G1，新图在原有的保护图中加入了一条x到y的标记为 $\alpha$ 的边。从图上看这条规则别写为“z赋予了x到y的权限 $\alpha$ ”。

![Grant G0](/images/images/security/take-grant-pic5.png)

![Grant G1](/images/images/security/take-grant-pic6.png)

表示成G0├─ G1：├─“z赋予了x到y的权限 $\alpha$ ”。

**Create规则：**设x是保护图G0的一个主体，并且 $\alpha\subset R$ 。Create规则定义了一个产生新图的G1方法（1）加入一个新的节点y;(2)加入一条从x到y的标记为 $\alpha$ 的边。这条规则称为：“x通过权限 $\alpha$ 创建了节点y。”
![Create](/images/images/security/take-grant-pic7.png)

**Remove规则：** Remove规则：设x、y是保护图G0的两个节点，并且x是主体。从x到y存在一条标记为β的边，并且 $\alpha\subseteq\beta$ 。Remove规则定义了一个产生新图的G1方法：新图中边的标记 $\beta$变为$β-α$ ，如果结果为空集，则边要被去掉。

![Remove](/images/images/security/take-grant-pic16.png)

## 权限共享
**定义:**设G0是一个保护图，x,y是G0中两个不同实体节点， $\alpha$ 是权限集合R的一个子集。谓词can·share( $\alpha$ ,x,y，G0)的意义是：
1. 存在一个保护图的序列G1, G2, ……,Gn， ρi,i=1,……，n, 利用规则ρi可以实现Gi-1 ⊢ * Gi, i=1,……，n；

1. Gn中存在包含权限子集 $\alpha$ 的x到y的边；

**引理：**

![引理](/images/images/security/take-grant-pic9.png)

**证明：**

x创建了新节点v，并且边标记为tg。

![证明step1](/images/images/security/take-grant-pic10.png)

z从x取得了到v的权限g。

![证明step2](/images/images/security/take-grant-pic11.png)

z赋予了v到y的权限 $\alpha$ 。

![证明step3](/images/images/security/take-grant-pic12.png)

x从v中取得了到y的权限 $\alpha$ 。

![证明step4](/images/images/security/take-grant-pic13.png)

类似的证明可得出以下引理：
**引理：**

![引理](/images/images/security/take-grant-pic14.png)

**取予(take-grant)模型—— 主体对称性**

![主体对称性](/images/images/security/take-grant-pic15.png)

**对称性：**如果连接x和y的tg路径中的节点都是主体，则Take和Grant规则是对称的。

**定义：**一个岛屿是最大的tg相连的、仅有主体的子图。

