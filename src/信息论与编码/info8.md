<!-- ---
title: 第八章 - 信息率失真理论及其应用
date: 2022-06-15T17:30:00+08:00
categories: ["信息论"]
layout: note
article: false
--- -->

# 第八章 信息率失真理论及其应用

## 8-1 失真函数和平均失真度

### 8-1-1 失真函数

**定义 8.1** 对于图示系统, 对应于每一对 $\left(a_{i}, b_{j}\right)$ $(i=1,2, \ldots r ; j=1,2, \ldots, s)$, 定义一个非负实值函数
$$d\left(a_{i}, b_{j}\right) \geq 0, i=1,2, \cdots r ; j=1,2, \cdots s$$
表示信源发出符号 $a_{i}$ 而经信道传输后再现成信道输出符号集合中的 $b_{j}$ 所引起的误差或失真, 称之为 $a_{i}$ 和 $b_{j}$ 之间的失真函数。

![](./P(YX).png)

失真函数的值可人为规定，一般定义为 $i=j$ 时（即 $b_j=b_i=a_i$）取 0

#### 失真矩阵 $[D]$
输入符号集 $\mathrm{X}:\left\{a_{1}, a_{2}, \ldots, a_{r}\right\}$ 中有 $r$ 种不同的符号 $a_{i}(i=1,2, \ldots, r)$; 输出符号集 $Y:\left\{b_{1}, b_{2}, \ldots, b_{s}\right\}$ 中有 $s$ 种不同的符号 $b_{j}(j=1,2, \ldots, s)$; 失真函数 $d\left(a_{i}, b_{j}\right)(i=1,2, \ldots, r ; j=1,2, \ldots, s)$ 共有 $(r \times s)$ 个具体值, 按 $a_i$ 和 $b_{j}$ 的对应关系, 排列 成一个 $(r \times s)$ 阶矩阵：
$$[D]=\begin{gathered}
a_{1} \\
a_{2} \\
\vdots \\
a_{r}
\end{gathered}\left[\begin{array}{cccc}
d\left(a_{1}, b_{1}\right) & d\left(a_{1}, b_{2}\right) & \cdots & d\left(a_{1}, b_{s}\right) \\
d\left(a_{2}, b_{1}\right)  & d\left(a_{2}, b_{2}\right) & \cdots & d\left(a_{2}, b_{s}\right) \\
\vdots & \vdots & & \vdots\\
d\left(a_{r}, b_{1}\right) & d\left(a_{r}, b_{2}\right) & \cdots & d\left(a_{r}, b_{s}\right)
\end{array}\right]$$
称为信道 $\mathrm{X}-\mathrm{P}(\mathrm{Y} / \mathrm{X})-\mathrm{Y}$ 的失真矩阵。

汉明失真矩阵（只有主对角线为 0）：
$$[D]=\left[\begin{array}{cccc}
0 & 1 & \cdots & 1 \\
1 & 0 & \ddots & 1 \\
\vdots& \ddots & \ddots & \\
1 & \cdots & 1 & 0
\end{array}\right]$$

> 把 $d(a_i,b_j)$ 分类讨论并写出来，再写失真矩阵

### 8-1-2 平均失真度

**定义 8.2**：称随机变量 $X$ 和 $Y$ 的联合概率 $P(a_i b_j)$对失真函数 $d(a_i,b_j)$
进行加权的统计平均值为该通信系统的平均失真度 $\overline{D}$。

就是加权的失真度

$$\begin{aligned}
\bar{D} &=\sum_{i=1}^{r} \sum_{j=1}^{s} P\left(a_{i} b_{j}\right) d\left(a_{i}, b_{j}\right) \\
&=\sum_{i=1}^{r} \sum_{j=1}^{s} P\left(a_{i}\right) P\left(b_{j} / a_{i}\right) d\left(a_{i}, b_{j}\right)
\end{aligned}$$

#### N次扩展信源的情况

将定义8.1进行扩展, 可得 $N$ 次扩展的信源和信宿符号序列 $\alpha_{i}$ 与 $\beta_{j}$ 之间的失真函数为
$$\begin{aligned}
d\left(\alpha_{i}, \beta_{j}\right) &=d\left(a_{i 1} a_{i 2} \cdots a_{i N}, b_{j 1} b_{j 2} \cdots b_{j N}\right) \\
&=d\left(a_{i 1}, b_{j 1}\right)+d\left(a_{i 2}, b_{j 2}\right)+\cdots+d\left(a_{i N}, b_{j N}\right) \\
&=\sum_{k=1}^{N} d\left(a_{i k}, b_{j k}\right)
\end{aligned}$$

对应的失真矩阵为
$$[D]=\left[\begin{array}{cccc}
d\left(\alpha_{1}, \beta_{1}\right) & d\left(\alpha_{1}, \beta_{2}\right) & \cdots & d\left(\alpha_{1}, \beta_{s^{v}}\right) \\
d\left(\alpha_{2}, \beta_{1}\right) & d\left(\alpha_{2}, \beta_{2}\right) & \cdots & d\left(\alpha_{2}, \beta_{s^{v}}\right) \\
\vdots & \vdots & & \vdots \\
d\left(\alpha_{r^{N}}, \beta_{1}\right) & d\left(\alpha_{r^{v}}, \beta_{2}\right) & \cdots & d\left(\alpha_{r^{v}}, \beta_{s^{v}}\right.
\end{array}\right]$$

平均失真度 $\bar{D}(N)$ 为
$$\begin{aligned}
\bar{D}(N) &=\sum_{i=1}^{r^{N}} \sum_{j=1}^{s^{N}} P\left(\alpha_{i} \beta_{j}\right) d\left(\alpha_{i}, \beta_{j}\right) \\
&=\sum_{i=1}^{r^{N}} \sum_{j=1}^{s} P\left(\alpha_{i}\right) P\left(\beta_{j} / \alpha_{i}\right) d\left(\alpha_{i}, \beta_{j}\right)
\end{aligned}$$

对无记忆信源和信道有
$$\begin{aligned}
\bar{D}(N)=&\sum_{i_{1}=1}^{r} \cdots \sum_{i_{N}=1}^{r} \sum_{j_{1}=1}^{s} \cdots \sum_{j_{N}=1}^{s} P\left(a_{i_{1}}\right) P\left(a_{i_{2}}\right) \cdots P\left(a_{i_{N}}\right) \\
&\cdot P\left(b_{j_{1}} / a_{i_{1}}\right) P\left(b_{j_{2}} / a_{i_{2}}\right) \cdots P\left(b_{j_{N}} / a_{i_{N}}\right) \sum_{k=1}^{N} d\left(a_{i_{k}}, b_{j_{k}}\right)\\
=&\sum_{k=1}^{N} \bar{D}_{k}
\end{aligned}$$

式中 $\bar{D}_{k}=\sum_{i_{k}=1}^{r} \sum_{j_{k}=1}^{s} P\left(a_{i_{k}}\right) P\left(b_{j_{k}} / a_{i_{k}}\right) d\left(a_{i_{k}}, b_{j_{k}}\right), k=1,2, \cdots N$

离散无记忆信源X的N次扩展信源通过无记忆信道传输后的平均失真度是未扩展情况的N倍:
$$\bar{D}(N)=N\bar{D}$$

> 类比扩展信源的信息熵和平均互信息量

## 8-2 信息率失真函数

### 8-2-1 保真度准则

**定义 8.3 保真度准则** 信道每传送一个符号所引起的平均失真，不能超过某一给定的限定值D，即要求$\bar{D}\leq D$ ，称这种对于失真的限制条件为保真度准则。

保真度准则指出，给定的失真限定值D是平均失真度 $\bar{D}$ 的上限值

平均失真度取决于如下几个因素
1. 信源的统计特性，即 $P(a_i)$
2. 信道统计特性，即 $P (b_j / a_i )$
3. 失真函数，即 $d(a_i,b_j)$

### 8-2-2 失真许可的试验信道
**定义 8.4** 凡是能满足保真度准则 $\bar{D}\leq D$ 的信道，称之为D失真许可的试验信道

所有的 D 失真许可的试验信道构成的集合表示为：
$$B_{D}=\left\{P\left(b, / a_{i}\right) ; \bar{D} \leq D\right\}$$

感兴趣的是 在同样的保真度准则下，能使信道的信息传输率尽可能小 的试验信道

### 8-2-3 信息率失真函数
**定义 8.5**：用给定的失真 $D$ 为自变量来描述的**信息传输速率**，
称为**信息率失真函数**，用 $R(D)$表示
- 信息传输速率 $R$ 本质上是描述信源输出的信息速率
- 一方面， $R = R(D)$，是 $D$ 的函数，另一方面，信道上的信息传输速率 $R = I (X;Y)$，因此，$R(D)$又可以用平均互信息量 $I (X;Y)$ 来表示
- $I(X ; Y)$ 是 $P\left(b_{j} \mid a_{i}\right)$ 的凸函数, 故总可以在 $B_{D}$ 集合中找到某 一试验信道, 使 $R=I(X ; Y)$ 达到最小值 $R(D)$, 故有
$$R(D)=\min _{P\left(b_{j} / a_{i}\right) \in B_{D}}\{I(\mathbf{X} ; \mathbf{Y})\}=\min _{D \leq D} I(\mathbf{X} ; \mathbf{Y})$$

#### 信息率失真函数的物理意义

- 信息率失真函数是在 $\bar{D}\leq D$ 的前提下，信宿必须获得的平均信息量的最小值，是信源必须输出的最小信息率
- 信息传输速率本质上是描述信源特性的，因此R(D)也仅用于描述信源
- 若信源消息经无失真编码后的信息传输速率为R，则在保真度准则下信源编码输出的信息率就是R(D)，且$R(D)<R$

#### R(D) 与 C

- 信道容量仅与信道有关，是信道的最大传输能力
- 信息率失真函数仅与信源有关，是在给定失真度下，信源至少要给信宿的信息率

#### N次扩展的信息率失真函数

$$R(ND)=N\cdot R(D)$$

### 8-2-4 信息率失真函数的性质

D必须在给定的信源X的概率分布P(X)、信宿Y的概率分布P(Y)和给定的失真函数 $d(a_i, b_j)$条件下所得的平均失真度 D 的最小值 $\bar{D}_{min}$ 和最大值 $\bar{D}_{max}$ 之间适当选择

可以求得平均失真度 $\bar{D}$ 的最小值, 为
$$\bar{D}_{\min }=\sum_{i=1}^{r} P\left(a_{i}\right) \cdot\left\{\min _{j} d\left(a_{i}, b_{j}\right)\right\}$$

$\bar{D}$ 的最小值 $\bar{D}_{\text {min }}$ 就是允许的平均失真度 $D$ 的最小值, 即

$$D_{\min }=\bar{D}_{\min }=\sum_{i=1}^{r} P\left(a_{i}\right) \cdot\left\{\min _{j} d\left(a_{i}, b_{j}\right)\right\}$$

- 当失真矩阵中每行至少有一个零元素时，$D_{\min }=\bar{D}_{\min }=0$
- 若某一行没有零元素，则可以让该行所有元素减去该行最小值，这样就有了零元素（毕竟失真度可以自定义）
- 因此，总是可以认为 $D_{min}=0$

- **如果失真矩阵每一列至多有一个0**，则 $D_{min}=0$ 对应的试验信道疑义熵 $H(X|Y)=0$，即$R(0)=I(X;Y)=H(X)–H(X|Y)= H(X)$，收到Y以后对X不存在不确定性
- 如果失真矩阵的列有大于1个0，则 $D_{min}=0$ 对应的试验信道疑义熵 $H(X|Y)>0$，即$R(0)=I(X;Y)=H(X)–H(X|Y)<H(X)$，收到Y以后对X存在不确定性

#### $D_{max}$ 和 $R(D_{max})$
- $\boldsymbol{R}(D)$ 是在保真度准则 $\bar{D} \leq D$ 下平均互信息量 $I(\mathrm{X} ; \mathrm{Y})$ 最小值
- $I(\mathbf{X} ; \mathbf{Y})$ 是非负数, 因此 $R(D)$ 最小值是 0
- 定义最大允许失真度 $D_{\max }$ 为使 $R(D)=0$ 的最小平均失真度 $\bar{D}_{\min }$ (平均失真度超过 $\bar{D}_{\text {min }}, R(D)$ 仍然等于 0 )
- $R(D)=0$ 等价于 $I(X ; Y)=0$, 此时信道的输入随机变量 $X$ 和 输出随机变量 $Y$ 之间一定统计独立, 即有
$$P\left(b_{j} \mid a_{i}\right)=P\left(b_{j}\right), i=1,2, \ldots, s$$

**R(D)为减函数，D越大，所需要的信息量越少，所以R也越小，直到为0。$D_{max}$ 就是 R 即便为 0 也满足 D 的要求的那个点**

#### R(D) 函数的凸性

（下凸）

**定理 8.1** $R(D)$ 在定义域内是凸函数, 即对任意 $0 \leq \alpha \leq 1$ 有
$$R\left[\alpha D_{1}+(1-\alpha) D_{2}\right] \leq \alpha R\left(D_{1}\right)+(1-\alpha) R\left(D_{2}\right)$$

#### R(D)函数的单调递减性

**定理 8.2** 信息率失真函数R(D)在定义域内是严格单调递减的。

使得平均互信息量最小的试验信道一定在试验集合的边界取到

## 8-3 信息率失真函数R(D)的计算

### 8-3-1 几种特殊离散信源的信息率失真函数

> Fano不等式 $H(\mathbf{X} \mid \mathbf{Y}) \leq H\left(P_{e}\right)+P_{e} \mathbf{l b}(r-1)$，式中 $H\left(P_{e}\right)=-\left[P_{e} I \mathrm{~b} P_{e}+\left(1-P_{e}\right) \mid \mathrm{b}\left(1-P_{e}\right)\right], r$ 是输入符号种数,

扰码器：让输出变为近似等概分布，必须在压缩编码之后（因为等概的时候压缩的概率很低）

### 8-3-2 离散信源R(D)的参量表述

### 8-3-3 连续信源的信息率失真函数

连续信源的失真函数一般为 $d(x,y)=(x-y)^2$

将离散情况中的求和运算改为积分运算

平均失真度：
$$\bar{D}=\iint_{-\infty}^{\infty} p(x) p(y \mid x) d(x, y) \mathrm{d} x \mathrm{~d} y$$

信息率失真函数：
$$R(D)=\min _{\bar{D} \leq D} I(X ; Y)=h(Y)-h(Y \mid X)$$

#### 高斯信源的信息率失真函数

概率密度函数
$$p(x)=\frac{1}{\sqrt{2 \pi} \sigma} e^{-(x-m)^{2} / 2 \sigma^{2}}$$
平方误差失真
$$d(x, y)=(x-y)^{2}$$
利用参量表述结果可得
$$R(D)=\left\{\begin{array}{cc}
\frac{1}{2} \log \frac{\sigma^{2}}{D} & D \leq \sigma^{2} \\
0 & D \geq \sigma^{2}
\end{array}\right.$$

#### 一般信源的信息率失真函数

均值为 0 , 方差为 $\sigma^{2}$ 的连续信源 $X$, 相对熵为 $h(X)$, 平方 误差失真下的信息率失真函数满足
$$h(X)-\frac{1}{2} \log (2 \pi e D) \leq R(D) \leq \frac{1}{2} \log \frac{\sigma^{2}}{D}$$

- 当X为高斯信源时，取到等号
- 在平方误差失真下，相同方差的信源要达到同样平均失真，高斯信源具有最大信息率失真函数，即高斯信源最难压缩

## 8-4 保真度准则下的信源编码定理

**定理 8.3 限失真信源编码定理 或 Shannon第三定理** 设 $R(D)$ 是某离散无记忆信源的信息率失真函数, 并且选定有限的失真函数 $D$ 。
对于任意允许的平均失真度和任意小的正数 $\varepsilon(\varepsilon>0)$, 以及任意足够长的码字长度 $N$, 则一定存在一种信源编码, 其码字个数为
$$M \geq \exp \{N[R(D)+\varepsilon]\}$$
而编码后码的平均失真度
$$\bar{D}(W) \leq D+\varepsilon$$
若码字数为
$$M<\exp \{N R(D)\}$$
则一定有
$$\bar{D}(W)>D$$

实际上就是 $R\geq R(D)$


- 也可以将定理8.3作如下的叙述：
  - 若R(D)为离散无记忆信源的信息率失真函数，D为允许的失真度，则只要实际的信息率R满足
$R \geq R(D)$，就存在一种编码方法，使其译码的平均失真度 $\bar{D}\leq D$；
反之，若R < R(D)，则无论怎样的编码方法，都不能使 $\bar{D}\leq D$
- R(D)是保真度准则下，信源信息率压缩的下限值。无失真信源编码信息率压缩的下限值是信源熵H(X)，而 $0 <R( D)< H ( X )$
- 若给定信源 $X$，其信息熵 $H(X)$，规定了失真函数，选定了允许的失真度 $D$，即可求得信息率失真函数$R(D)$
- 根据Shannon第三定理，必然存在一种压缩编码方法，使其平均失真度不大于 $D$，且其输出信息率由$H(X)$ 下降到$R'$，只要$R'\geq R(D)$

**联合信源信道编码定理（信源信道编码分离定理）**：
设离散无记忆信道的容量为 $C$ 比特/秒，离散无记忆信源熵为 $H$ 比特/秒，则当 $H<C$ 时，
则总存在一种编码方案使得译码错误概率任意小；反之，如果 $H>C$，
则不存在使得译码错误概率任意小的编码方案。