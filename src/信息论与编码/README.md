<!-- ---
title: 小结
date: 2022-03-07T14:00:00+08:00
categories: ["信息论"]
layout: note
article: false
--- -->

课程内容和要求
- 教材：《信息论与编码》，参考书：《信息论——基础理论与应用》
- 开卷考试，卷面占总成绩 60%，可以带计算器


简答题就简答，不要太多

信息度量和三大定理

主要计算题：信源编码和信道编码

$I(X;Y)$ 的最大值就是信道容量 $C$

平均功率 $\mathrm{E}\left\{y^{2}\right\}=\mathrm{E}\left\{(x+n)^{2}\right\}=\mathrm{E}\left\{x^{2}\right\}+\mathrm{E}\left\{n^{2}\right\}=S+\sigma^{2}=S+N$

平均交流功率就是方差，就是自相关函数的峰值

熵和信道容量要写单位

导数和积分表

- 给定方差情况下，高斯信源的信息率失真函数最大，即最难压缩；
- 给定方差情况下，噪声服从高斯分布时的信道容量最小

设函数求导比大小

- $a_n = np^n$
- $\sum_{i=1}^n a_n=\frac{p-p^{n+1}}{(1-p)^2}-\frac{np^{n+1}}{1-p}$

高斯：$f(x)={\frac {1}{\sigma {\sqrt {2\pi }}}}\;e^{-{\frac {\left(x-\mu \right)^{2}}{2\sigma ^{2}}}}$

切比雪夫不等式：$P(|X-E(X)|\geq b)\leq {\frac {Var(X)}{b^{2}}}$

## 第二章

**Jensen 不等式**（凹函数定义）：$\sum_{i=1}^N p_i\operatorname{lb}(x_i)\leq\operatorname{lb}\left(\sum_{i=1}^N p_i x_i\right)$

消息中平均每个符号携带的信息量有别于离散平均无记忆信源平均每个符号携带的信息量，后者是信息熵

若信源熵居然大于等概分布的信源熵，则一定是 信源空间不满足概率空间的完备集，譬如概率之和不为1

- $I(x_i)=-\operatorname{lb}P(x_i)$ bit
- $H(X)=-\sum_{i=1}^N P(x_i)\operatorname{lb} P(x_i)$ bit/符号
- $H(XY)=H(X)+H(Y|X)$
- $H(X|Y)=-\sum_{x\in X, y\in Y}P(xy)\operatorname{lb}P(x|y)$
- K 重扩展信源的熵：$H(X^K)$
- **平均符号熵**：$H_K(X_1X_2\dots X_K)=\frac{1}{K}H(X_1X_2\dots X_K)$
- **互信息量**：$I(x_i;y_j)=I(x_i)-I(x_i|y_i)=\operatorname{lb}\frac{P(x_i|y_j)}{P(x_i)}=\operatorname{lb}\frac{P(x_iy_j)}{P(x_i)P(y_j)}=\operatorname{lb}\frac{P(y_j|x_i)}{P(y_j)}=I(y_j;x_i)$，没有负号！
- **平均互信息量** ：$I(X;Y)=\sum_{XY}P(xy)\operatorname{lb}\frac{P(x|y)}{P(x)}$
- $I(X;Y)=H(X)-H(X|Y)=H(Y)-H(Y|X)$

## 第三章

联合熵与条件熵的关系：$H(X_1X_2X_3)=H(X_3|X_1X_2)+H(X_1X_2)$

- 信源的冗余度：$R=\frac{H_{max}-H}{H_{max}}\times 100\%$

## 第四章

平均码长是加权的，且 K 重扩展的平均码长单位为 码元/K个符号，往往要再除以 K

$\sum_i\frac{i}{2^i}=2$：乘公比错位相减

单义可译码：
1. 等长码，且各消息对应码字不同
2. 变长码，且不能用不同的多个码字拼出相同的一串序列，譬如$a_1a_2=a_3a_4a_5$
3. 也可以直接算单义可译码和即时码的必要条件： $\sum^N_{i=1}D^{-b_i}\leq 1$ ，$b_i$ 为各码长，D 为符号种数
   - 满足 Kraft 不等式只是表明这种码长分布可以构造单义可译码和即时码
   - 即时码仅是单义可译码的一种排布，没有更严格的要求

最佳编码：具有最短的代码组平均长度或编码效率接近于 1 的信源编码
- 二元霍夫曼编码

$\bar{L}_N$：N 个信源符号的平均编码符号长度


- 编码效率：$\eta=\frac{H(X^K)/\bar{B}}{\operatorname{lb}D}\times 100\%$

先试扩展倍数小的，不够再加

## 第五章

**信道矩阵**：（给出信道特性）
$$
\Pi=\left[\begin{array}{cccc}
P\left(y_{1} \mid x_{1}\right) & P\left(y_{2} \mid x_{1}\right) & \cdots & P\left(y_{L} \mid x_{1}\right) \\
P\left(y_{1} \mid x_{2}\right) & P\left(y_{2} \mid x_{2}\right) & \cdots & P\left(y_{L} \mid x_{2}\right) \\
& \ddots & & \\
P\left(y_{1} \mid x_{M}\right) & P\left(y_{2} \mid x_{M}\right) & \cdots & P\left(y_{L} \mid x_{M}\right)
\end{array}\right]_{M \times L}
$$

**对称离散信道**：
信道矩阵的所有行由相同元素组成，所有列也由相同元素组成

**二进制对称信道容量**：$C_{BSC}=1+\varepsilon\operatorname{lb}\varepsilon+(1-\varepsilon)\operatorname{lb}(1-\varepsilon)$ bit/符号

**离散准对称信道**：
- 定义：信道矩阵可以按列分解为若干互不相交的子集，每个子集构成的矩阵都对应对称信道
- 设信源符号个数和信宿符号个数分别为 r 和 s，
当信源符号消息等概分布时，达到信道容量 C，且
$C=\operatorname{lb}r+\sum_{j=1}^s p_j\operatorname{lb}p_j-\sum_{k=1}^n N_k\operatorname{lb}M_k$ 比特/符号，
其中 $\{p_1,\dots,p_s\}$ 是信道矩阵每一行的元素，n 表示子矩阵个数，
$N_k$表示第k个子矩阵行元素之和，$M_k$表示第k个子矩阵列元素之和。

译码准则：规定把 什么 y 判成 什么 x
- 先画香农线图
- 最小错误概率：对每个 $y_j$，取最大的 $P(x_i|y_j)$（其实也就是最大 $P(xy)$
  1. 列出发送码字到接收码字的转移概率矩阵 $P(xy)$
  2. 每列求和得到 $P(y)$，每列除以它
  3. 每列取最大的
- 最大似然：对每个 $y_j$，取最大的 $P(y_j|x_i)$
- 错误概率：先求正确概率 $P_C=P(x_1)P(y_{c1}|x_1)+P(x_2)P(y_{c2}|x_2)$

码率：$R=(\operatorname{lb}M)/N$ 比特/码元，M 为码字种数

## 第六章
- 相对熵：$h(x)=-\int_{-\infty}^{\infty} p(x) \operatorname{lb} p(x) \mathrm{d} x$
 
将随机变量 $X$ 和 $Y$ 的变换关系记作 $X=f(Y)$，则有$h(y)=h(x)-E_{X}\left\{\log \left|J\left(\frac{X}{Y}\right)\right|\right\}$，其中 $J\left(\frac{X}{Y}\right)=\frac{\mathrm{d} f(Y)}{\mathrm{d} Y}$（==是反的导数！f是Y到X！==）

若 $p(xy)=p(x)p(y)$，则平均互信息量为 0

相对熵积分要复习一下

**熵功率**：达到指定熵所需的最小功率

6.3 需要仔细看（特别是6.3.2）

## 第八章

- $\bar{D}_{max}$：选一列取得最小失真度
- $\bar{D}_{min}$：取得最小失真度
- 二元离散信源的率失真函数：$R(D)=H(X)-H(\frac{D}{\alpha})$
- 等概离散信源的率失真函数：$R(D)=\operatorname{lb}r-H(\frac{D}{\alpha})-D\operatorname{lb}(r-1)$
  - $H(D)=-[D\log D+(1-D)\log(1-D)]\sum_V P(v)$，$\sum_V P(v)$ 通常为 1
  - $\alpha$ 为失真矩阵中的非零元

$R(D)$ 是比特 / 信源符号，$R_t$ 是比特 / 秒

## 第十章

> 陪集首不能属于对应子群，且汉明重应最小

- 线性分组码的最小距离等于非零码字的最小重量
- 设C是 $(n, k)$线性分组码，其纠错能力为t。如果用且只用不大于t个错误的全部错误图样作陪集首就能构成标准阵，那么就称这个码为**完备码**。

## 第十一章

有可能满足循环性但不是线性码！线性：两个码字相加也是码字
