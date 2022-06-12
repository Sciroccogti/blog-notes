<!-- ---
title: 第五章 - 离散信源及其信道编码
date: 2022-05-15T22:26:00+08:00
categories: ["信息论"]
layout: note
article: false
--- -->

# 第五章 离散信源及其信道编码

## 5-1 信道的分类及其描述

（1） 信道按输入/输出符号空间的性质来划分，根据幅度和时间上的取值是离散或连续，分为四类：
- 离散信道：输入和输出的随机序列取值均为离散的信道，也称为数字信道
- 连续信道：输入和输出的随机序列取值均为连续的信道
- 半离散或半连续信道：输入序列是离散型但相应输出序列是连续的信道，或者相反
- 波形信道：输入和输出都是时间上连续的随机信号，也称为模拟信道

（2）按信道的输入消息集合和输出消息集合的个数来划分：
- 两端信道：信道的输入消息集合只有一个X集合，同时信道的输出消息集合也只有一个Y集合，又称为单向单路信道
- 多端信道：信道的输入端和输出端中，至少有一端具有一个以上的消息集合，又称为多用户信道

（3） 信道按输入/输出信号间的关系是否确定来划分，
- 无扰信道：信道输入/输出之间是一种确定的关系，这是一种理想化的信道，信道上不存在噪声及干扰。可以作为衡量其他信道特性的参考
- 有扰信道：信道输入/输出之间是一种统计依存的关系，信道上存在干扰和（或）噪声。实际的通信信道几乎都是有扰信道

（4） 信道按其输入/输出之间关系的记忆性来划分，
- 无记忆信道：在某一时刻信道的输出消息仅与当时的信道输入消息有关，而与前面时刻的信道输入或输出消息无关。信道的统计特性可以用信道传输概率的集合{P(y|x)}来描述
- 有记忆信道：在任意时刻信道的输出消息不仅与当时的信道输入消息有关，还与以前时刻的信道输入和（或）输出消息有关。实际信道一般都是有记忆的

（5）信道按其统计特性来划分，
- 恒参信道：信道的统计特性不随时间变化，又称为平稳信道
- 变参信道：信道的统计特性随时间变化

## 5-2 无扰离散信道的传输特性

**定义 5.1** 单位时间内所传输的信息量，称为消息在信道中的**信息传输速率**，简称为信息率 R
- 量纲为比特/码元或比特/符号、比特/符号序列等时，用 R 表示
- 量纲为 bit/s 或 bps，用 $R_t$ 表示

平均互信息量 $I(X;Y)$ 代表收到 Y 后获得关于 X 的平均信息量，因此实质上就是量纲为比特/码元（或比特/符号、比特/符号序列等）的信息传输速率，即 $R =I(X;Y)$ bit/码元；如果改变其时间单位，则有 $R_t =\frac{1}{t} I(X;Y)$ bit/s
- 无扰离散信道下信息传输速率等于信源熵，即$R =H(X)$ bit/码元；$R_t =\frac{1}{t} H(X)$ bit/s

**信道容量**：
消息在不失真传输的条件下，信道所允许的最大信息传输速率称为信道容量，即 $C = R_{max}$ bit/码元；当单位为bit/s（bps）时，C 变换为 $C_t =R_{t max}$ bit/s

**信道容量和信道中传输的消息数目 N 的关系**：
对无扰信道，信道传输的信息量就是信源发出的信息量，根据最大信息熵定理，所有信源符合等概率的时候信源熵最大，因此信道容量 $C=\operatorname{lb}N$ bit / 码元；$C=\frac{\operatorname{lb}N}{t}$ bit / s

**定义5.3** 基本符号时间等长的信道称为**均匀编码信道**，这种等长的基本符号称为**码元**。

- 损失熵：$H(X|Y)$
- 噪声熵：$H(Y|X)$

**无噪无损信道**：输入与输出符号一对一
- 损失熵 $H(X|Y)$ 和 噪声熵 $H(Y|X)$ 均为 0，$I(X;Y)=H(X)=H(Y)$
- 信道容量 $C=\max_{P(x)}I(X;Y)=\max_{P(x)}H(X)=\operatorname{lb}|X|$ bit/码元

**无噪有损信道**：输入与输出符号多对一
- 损失熵 $H(X|Y)\neq0$，噪声熵 $H(Y|X)=0$，$I(X;Y)=H(Y)<H(X)$
- 信道容量 $C=\max_{P(x)}I(X;Y)=\max_{P(x)}H(Y)=\operatorname{lb}|Y|$ bit/码元

**有噪无损信道**：输入与输出符号一对多
- 损失熵 $H(X|Y)=0$，噪声熵 $H(Y|X)\neq0$，$I(X;Y)=H(X)<H(Y)$
- 信道容量 $C=\max_{P(x)}I(X;Y)=\max_{P(x)}H(X)=\operatorname{lb}|X|$ bit/码元

## 5-3 有扰离散信道的传输特性

**信道矩阵**：（给出信道特性）
$$
\Pi=\left[\begin{array}{cccc}
P\left(y_{1} \mid x_{1}\right) & P\left(y_{2} \mid x_{1}\right) & \cdots & P\left(y_{L} \mid x_{1}\right) \\
P\left(y_{1} \mid x_{2}\right) & P\left(y_{2} \mid x_{2}\right) & \cdots & P\left(y_{L} \mid x_{2}\right) \\
& \ddots & & \\
P\left(y_{1} \mid x_{M}\right) & P\left(y_{2} \mid x_{M}\right) & \cdots & P\left(y_{L} \mid x_{M}\right)
\end{array}\right]_{M \times L}
$$

$P(y_j|x_i)$ 为信道传输概率

**对称离散信道**：
信道矩阵的所有行由相同元素组成，所有列也由相同元素组成

**强对称离散信道（均匀信道）**：信道矩阵为方阵
$$
\mathbf{P}=\left[\begin{array}{ccccc}
\bar{p} & \frac{p}{r-1} & \frac{p}{r-1} & \cdots & \frac{p}{r-1} \\
\frac{p}{r-1} & \bar{p} & \frac{p}{r-1} & \cdots & \frac{p}{r-1} \\
\vdots & \vdots & \vdots & \cdots & \vdots \\
\frac{p}{r-1} & \frac{p}{r-1} & \frac{p}{r-1} & \cdots & \bar{p}
\end{array}\right], \quad p, \bar{p} \in[0,1], \quad p+\bar{p}=1
$$
- 总错误概率为p，均匀分给r-1个输出符号
- 信道矩阵各列之和也等于1

**二进制对称信道（BSC）**：其中$\varepsilon$为交叉传输概率
![](BSC.png)

$$
\Pi=\left[\begin{array}{cc}
1-\varepsilon & \varepsilon \\
\varepsilon & 1-\varepsilon
\end{array}\right]
$$

**准对称离散信道**
- 信道矩阵的列可以分解为若干互不相交的子集，每个子集构成的矩阵都对应对称信道

**二进制删除信道**：
![](BEC.png)
$$
\Pi=\left[\begin{array}{ccc}
1-\varepsilon_{1}-\varepsilon_{2} & \varepsilon_{1} & \varepsilon_{2} \\
\varepsilon_{2} & \varepsilon_{1} & 1-\varepsilon_{1}-\varepsilon_{2}
\end{array}\right]
$$

### 5-3-4 有扰离散信道的信道容量

有扰离散信道的信道容量是指在不失真传输的条件下，信道所允许的最大信息传输速率（平均互信息量）：
$$C = \max R = \max I (X;Y)$$

- 信道容量 C 是信道的最大传输能力，是信道自身的特性
- 能使平均互信息量达到信道容量C的信源称为**匹配信源**
- $I (X;Y)$ 是 $P(x)$ 和 $P(y|x)$ 的函数
- $P(x)$ 只与具体信源有关；$P(y|x)$ 只与信道特性有关，与具体信源无关，因此 $C=\max_{\{P(x)\}}I(X;Y)$

#### 几种特殊信道的信道容量

**定理 5.1** 对于信源符号个数和信宿符号个数分别为 r 和 s 的**离散对称信道**，
当信源符号消息等概分布时，达到信道容量 C ，且
$C=\operatorname{lb}s+\sum_{j=1}^s p_j\operatorname{lb}p_j$ 比特/符号，
其中 $\{p_1,\dots,p_s\}$ 是信道矩阵每一行的元素

**二进制对称信道容量**：
$$C_{BSC}=1+\varepsilon\operatorname{lb}\varepsilon+(1-\varepsilon)\operatorname{lb}(1-\varepsilon)$$

**定理 5.2** 对于信源符号个数和信宿符号个数分别为 r 和 s 的**离散准对称信道**，
当信源符号消息等概分布时，达到信道容量 C，且
$C=\operatorname{lb}r+\sum_{j=1}^s p_j\operatorname{lb}p_j-\sum_{k=1}^n N_k\operatorname{lb}M_k$ 比特/符号，
其中 $\{p_1,\dots,p_s\}$ 是信道矩阵每一行的元素，n 表示子矩阵个数，
$N_k$表示第k个子矩阵行元素之和，$M_k$表示第k个子矩阵列元素之和。

**二进制删除信道容量**：
$$
C_{BEC}
=\varepsilon_{2} \mathrm{lb} \varepsilon_{2}+\left(1-\varepsilon_{1}-\varepsilon_{2}\right) \mathrm{lb}\left(1-\varepsilon_{1}-\varepsilon_{2}\right)+\left(1-\varepsilon_{1}\right) \mathrm{lb} \frac{2}{1-\varepsilon_{1}}
$$

**一般离散信道**：
$$\max_{P(a_i)}I(X;Y), s.t. \sum_{i=1}^rP(a_i)=1,P(a_i)\geq0$$

> 凸问题一定能用拉格朗日解，否则不一定

定义
$$
I\left(x_{i} ; \mathbf{Y}\right)=\sum_{j=1}^{s} P\left(b_{j} \mid a_{i}\right) \log \frac{P\left(b_{j} \mid a_{i}\right)}{P\left(b_{j}\right)}
$$
表示接收到 $\mathbf{Y}$ 之后获得关于 $x_{i}=a_{i}$ 的信息量（某个符号与信宿之间的平均互信息量）

**定理 5.2**：输入概率分布达到信道容量的充要条件为
$$
I\left(x_{i} ; \mathbf{Y}\right)\left\{\begin{array}{ll}
=C & P\left(a_{i}\right) \neq 0 \\
\leq C & P\left(a_{i}\right)=0
\end{array}\right.
$$

- 概率不为 0 的信源符号和 Y 的平均互信息量都等于信道容量
- 达到信道容量的最优输入分布不唯一

#### 信道容量的通解

对信道矩阵每行列一个方程：

$$
\sum_{j=1}^{s} P\left(b_{j} \mid a_{i}\right) \beta_{j}=\sum_{j=1}^{s} P\left(b_{j} \mid a_{i}\right) \log P\left(b_{j} \mid a_{i}\right), i=1, \ldots, r
$$
若信道矩阵为方阵且可逆, 则可以求出 $\beta_{j}$ ；
继续求出 C 和 $P(\beta)$：
$$C=\mathrm{lb} \sum_{j=1}^{s} 2^{\beta_{j}}$$
$$P\left(b_{j}\right)=2^{\beta_{j}-C}$$
最后根据 $P\left(b_{j}\right)=\sum_{i=1}^{r} P\left(a_{i}\right) P\left(b_{j} \mid a_{i}\right)$ 得到最优输入概率分布

> $\beta$ 通常为负

#### K 重扩展信源的信道

对于信源 $\mathbf{X}$ 的 $K$ 重扩展信源 $\mathbf{X}^{K}=\left(\mathbf{X}_{1} \mathbf{X}_{2} \ldots \mathbf{X}_{K}\right)$, 对应的 $\boldsymbol{K}$ 重扩展信宿 $\mathbf{Y}^{K}=\left(\mathbf{Y}_{1} \mathbf{Y}_{2} \ldots \mathbf{Y}_{K}\right)$, 且 $\mathbf{x}^{K} \in \mathbf{X}^{K}$, $\mathbf{y}^{K} \in \mathbf{Y}^{K}, x_{i} \in X_{i}, y_{i} \in Y_{i}$
- 当信道无记忆时, 即信道传输概率满足
$P\left(\mathbf{y}^{K} \mid \mathbf{x}^{K}\right)=\prod_{i=1}^{K} P\left(y_{i} \mid x_{i}\right)$，则有$I\left(\mathbf{X}^{K} ; \mathbf{Y}^{K}\right) \leq \sum_{i=1}^{K} I\left(X_{i} ; Y_{i}\right)$
- 当信源无记忆时, 即满足
$P\left(\mathbf{x}^{K}\right)=\prod_{i=1}^{K} P\left(x_{i}\right)$，则有$I\left(\mathbf{X}^{K} ; \mathbf{Y}^{K}\right) \geq \sum_{i=1}^{K} I\left(X_{i} ; Y_{i}\right)$
- 当信源和信道都无记忆时,则有$I\left(\mathbf{X}^{K} ; \mathbf{Y}^{K}\right) = \sum_{i=1}^{K} I\left(X_{i} ; Y_{i}\right)$

$C^K\leq\sum_{i=1}^K C_i$
- 当且仅当信源无记忆且各个 $X_i$ 达到最佳概率分布时取等
- 对于时不变信道，即各个 $X_i$ 经过相同信道时，$C_i=C, C^K\leq KC$

#### 并联信道

$\widetilde{C}\leq\sum_{i=1}^N C_i$

#### 串联信道

信道矩阵为各个子信道的信道矩阵的乘积

两个 BSC 串联后仍是 BSC

级联将使信道容量C下降，且随着 $\varepsilon$ 的增大变得非常明显

## 5-4 译码准则

**定义 5.6** 在一般的信息传输系统中，信宿收到的消息不一定与信源发出的消息相同，
而信宿需要知道此时信源发出的是哪一个信源消息，
故需要把信宿收到的消息 $y_j$ 根据某种规则判决为对应于信源符号消息集合中的某一个，
例如 $x_i$，这个判决的过程称为接收译码，简称译码，译码时所用的规则称为译码准则。
- 任何译码准则所遵循的基本要求都是要使信宿得到的判决结果中错误最少
- 译码准则就是一种能满足 $g(y_j) = x_i$ 的函数关系，它使得译码结果中的错误概率达到最小

### 5-4-1 常用的译码准则

例：$g(0)=0,g(1)=1$

#### 最小错误概率准则 即 最大后验概率准则

对于所有的 i ，若 $x_i\neq x^*$，且 $P(x^*|y_j)>P(x_i|y_j)$，则 $g(y_j)=x^*$

可以通过求所有的 $P(x_i|y_j)$，对每个 $y_j$ 取最大的后验概率，算出正确传输概率 $P_C$

也可以直接从信源的概率分布和条件概率来求采用最小错误概率准则时的接收错误概率：
$$P_{E min}=\sum_{j=1}^L\sum_{i=1}^M P(x_i)P(y_j|x_i)$$

#### 最大似然译码准则

$P(y_j|x_i)$ 是信道传输概率，也称为最大似然函数

$$P(x_i|y_j)=\frac{P(x_i)P(y_j|x_i)}{P(y_j)}$$

1. 信源符号等概分布
   - 只要选取 $x^*$ 使得 $P(y_j|x^*)$ 最大，则 $P(x_i|y_j)$ 最大
   - 此时错误概率为 $P_{E min}=1/M\sum_{j=1}^L\sum_{i=1, i\neq*}^M P(y_j|x_i)$
2. $P(y_j|x_1)=P(y_j|x_2)=\cdots=P(y_j|x_M)$
   - 不论发送哪个符号，收到 $y_j$ 的概率都相等
   - 此时只要选取 $P(x^*)$ 最大即可

## 5-5 有扰离散信道的信道编码定理

### 5-5-1 编码方法与平均错误译码概率

信息传输速率（码率）：$R=(\operatorname{lb}M)/N$ 比特/码元

### 5-5-2 汉明距与编码原则

略

在同样的信道条件下，所能达到的 $P_{Emin}$，与所选择许用码组的 $D_{min}$有关
- 许用码组：有对应信源符号的信宿符号

#### 二元对称无记忆信道的最大似然译码

假设发送码字 $\alpha_i$ 经过信道后变为 $\beta_j$，则信道传输概率为
$$P(\beta_j|\alpha_i)=\prod_{n=1}^N P(\beta_{j_n}|\alpha_{i_n})=p^{D(\alpha_i,\beta_j)}(1-p)^{N-D(\alpha_i,\beta_j)}$$
p为单个符号传输错误概率，通常小于0.5
因此，$D(\alpha_i,\beta_j)$ 越小，$P(\beta_j,\alpha_i)$ 越大，等价于最小距离译码

- 发射的信源等概时，最小错误概率译码退化为最大似然译码；
- 二元对称无记忆信道下，最大似然译码退化为最小距离译码。

#### 编码原则

任意许用码字间的最小汉明距尽量大

### 5-5-3 有扰离散信道的信道编码定理

**定理 5.3 抗干扰信道编码定理 香农第二定理**：
设信道有 D 个输入符号，s 个输出符号，信道容量为 C，被传消息的码长为 N，信息传输速率为 R，
则当 R< C 时，只要码长 N 足够长，总可以在输入集合中，找到 M 个码字（$M < 2^{N(C-\varepsilon)}$ ，
$\varepsilon$为任意小的正数），分别代表M个等可能性的消息，组成一种信道编码，
选择相应的译码规则，使信宿端译码后的最小平均错误译码概率 $P_{Emin}$ 达到任意小

**定理 5.4香农第二定理逆定理** 设信道有 D 个输入符号、s 个输入符号，信道容量为 C；
令 ε 为任意小的正数，若选择许用码组个数 $M = 2^{N(C+\varepsilon)}$（即R > C），
则无论码长 N 多大，也不可能找到一种编码，使 $P_{E}$ 任意小。

## 5-6 信道编码定理的应用


