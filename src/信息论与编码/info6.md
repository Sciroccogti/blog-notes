<!-- ---
title: 第六章 - 连续消息和连续信道
date: 2022-05-29T22:00:00+08:00
categories: ["信息论"]
layout: note
article: false
--- -->

# 第六章 连续消息和连续信道

## 6-1 连续消息的信息度量

1. 将连续型信源变换成离散型信源，用离散信源的分析方法进行分析
2. 再将量化单位无限缩小，在极限情况下分析离散情况得到的结果

**样值量化**——连续信源变为离散信源
1. 时间抽样
2. 量化幅度
3. 每个样值的自信息量以及信源熵都可用离散信源理论计算，所得离散信源的熵可近似作为此连续信源的熵

**量化级无限增大** ——离散信源还原成连续信源
1. 量化幅度与原幅度间的差异会引起量化噪声
2. 可以使用非线性压扩和减小量化单位减少量化噪声
3. 当量化单位无限缩小时，离散信源就能还原为连续信源

- 设样值的熵为 $H(x)$，它实际上就是量化后得到的单符号离散信源的信息熵
- 设量化前样值的幅度为 $x$，对应的概率密度值为 $p(x)$；若量化后的样值幅度为 $x_i$，对应的概率密度值为 $p(x_i)$，则在区间 $(x_i，x_i+\Delta x)$，其概率为 $p(x_i)\cdot\Delta x$
- 量化后共有 $2 L+1$ 个取值, 则离散信源的信息熵
$$H(x)=-\sum_{L}^{L} p\left(x_{i}\right) \Delta x \mathrm{lb}\left[p\left(x_{i}\right) \Delta x\right]$$
- 当 $\Delta x$ 趋于 0 , 得到连续信源的熵的计算公式 
$$H(x)=-\int_{-\infty}^{\infty} p(x) \mathrm{lb} p(x) \mathrm{d} x-\int_{-\infty}^{\infty} p(x) \mathrm{lb} \Delta x \mathrm{~d} x$$
第一项由且仅由 $p(x)$ 决定, 为确定值, 称为**相对熵**, 用 $h(x)$ 表示;
$$h(x)=-\int_{-\infty}^{\infty} p(x) \operatorname{lb} p(x) \mathrm{d} x$$
第二项当 $\Delta x \rightarrow 0$ 时它趋于无限大, 称为**绝对熵**, 用 $H\left(x_{0}\right)$ 表示:
$$H\left(x_{0}\right)=-\int_{-\infty}^{\infty} p(x) \operatorname{lb} \Delta x \mathrm{~d} x$$

**相对熵**：
- 相对熵的形式与离散信源熵的形式相近，另外当考虑信息传输问题时，由于互信息量等于两个熵相减，所以绝对熵可以抵消，只剩下相对熵
- 相对熵能够很好地量度连续信源的信息特性，在后面的讨论中，如无特别说明，一般所说的信源熵都是指相对熵

**绝对熵**：
- 之所以称为绝对熵，是因为 $\Delta x \rightarrow 0$ 时它趋于无限大，且连续信源的各种熵都有这一项

**输出随机序列的连续信源**
- **联合相对熵**为 $h(\mathbf{x})=-\int_{-\infty}^{\infty} \cdots \int_{-\infty}^{\infty} p(\mathbf{x}) \mathrm{lb} p(\mathbf{x}) \mathrm{d} \mathbf{x}$ 比特 / 样值序列

**输出随机信号的波形信源**
- 采样后转换为无穷维随机序列
  - $h(x(t))=\lim _{N \rightarrow \infty} h(\mathbf{x})$ 比特/样值序列
  - $h(x(t))=\lim _{T \rightarrow \infty} \frac{1}{T} h(\mathbf{x})$比特/秒（更常用)
- 对于带宽为 $B$，时长为 $T$ 的信号, 等价于计算长度为 $N=2 B T$ 的随机序列信源的相对熵

### 6-1-2 几种连续信源的相对熵

**均匀分布**：
1. 相对熵：$h(x)=\operatorname{lb}(b-a)$ 比特/样值
2. $b-a<1$ 时，相对熵为负

**N维区域体积内均匀分布的连续信源**：
N维连续信源输出随机向量 $X^N=[ X_1 \cdots X_N ]$ 的各个分量分别在 $[a_1, b_1 ],\cdots,[a_N, b_N ]$区域内均匀分布，
- 该信源的相对熵为
$h(\mathbf{x})=\sum_{i=1}^{N} h\left(x_{i}\right)$ 比特/样值序列
等于 $N$ 维区域体积的对数, 也等于各分量相对熵之和 (与离散无记忆信源一致)
- 推广到带宽为 $B$, 时长为 $T$ 的波形信源, 如果每个样值 在 $[a, b]$ 区间服从均匀分布, 相对熵为 $h(\mathbf{x})=2 B T \mathrm{lb}(b-a)$ 比特/样值序列
- 单位时间内的相对熵为$h(\mathbf{x})=2 B \mathrm{lb}(b-a)$ 比特/秒

**高斯分布连续信源**：
- 相对熵：$h(x)=\frac{1}{2}\ln(2\pi e\sigma^2)$ 奈特 / 样值
- 当均值为 0 时，即不计高斯连续信源X中的直流部分时，$h(x)=\frac{1}{2}\ln(2\pi eP)$ 奈特 / 样值，P 为平均功率
- 对于协方差矩阵为 C 的高斯向量 x：$h(x)=\frac{1}{2}\ln\left[(2\pi e)^N|C|)\right]$ 奈特 / 样值；
  - 当 x 的各元素独立时，有 $h(x)=\sum_{i=1}^N h(x_i)$

**指数分布**：
- 相对熵为：$h(x)=\ln ae$ 奈特/样值

### 6-1-3 条件熵

离散信源条件熵
$$H(\mathbf{X} \mid \mathbf{Y})=-\sum_{\mathbf{X Y}} P(x y) \mathrm{lb} P(x \mid y)$$
其中任意两事件 $x_{i}, y_{j}$ 的联合概率为
$$P\left(x_{i} y_{j}\right)=P\left(y_{j}\right) P\left(x_{i} \mid y_{j}\right)=P\left(x_{i}\right) P\left(y_{j} \mid x_{i}\right)$$
连续信源经取样、量化后的样值共有 $2 L+1$ 个取值, 则条件熵为
$$H(\mathbf{X} \mid \mathbf{Y})=-\sum_{j=-L i=-L}^{L} \sum_{j}^{L} P\left(y_{j}\right) P\left(x_{i} \mid y_{j}\right) \operatorname{lb} P\left(x_{i} \mid y_{j}\right)$$

相对条件熵:
$$
h(x \mid y)=-\int_{-\infty}^{\infty} \int_{-\infty}^{\infty} p(x y) \mathrm{lb} p(x \mid y) \mathrm{d} x \mathrm{~d} y$$
绝对条件熵：
$$
H\left(x_{0} \mid y_{0}\right)=-\mathrm{lb} \Delta x \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} p(x \mid y) p(y) \mathrm{d} x \mathrm{~d} y
$$
当 $\Delta x \rightarrow 0$ 时绝对条件熵趋于无限大
- 对于输出随机序列的连续信源, 相对条件熵为
$$
h(\mathbf{x} \mid \mathbf{y})=-\int_{-\infty}^{\infty} \ldots \int_{-\infty}^{\infty} p(\mathbf{x} \mathbf{y}) \mathrm{l} b p(\mathbf{x} \mid \mathbf{y}) \mathrm{d} \mathbf{x} d \mathbf{y}
$$

### 6-1-4 连续消息熵的性质

- $h(xy) = h(x) + h(y|x) = h(y) + h(x|y)$
- $h(y|x) \leq h(y)$，$h(x|y) \leq h(x)$ 以及 $h(xy) \leq h(x) + h(y)$，当且仅当x和y相互独立时取等
- 可加性：x和y 独立时 $h(xy) = h(x) + h(y)$
- 强可加性：$h(xy) = h(x) + h(y|x)$
- 相对熵可以是正值或0，也可以是负值，取决于概率密度函数
- 相对熵是 $p(x)$ 的凹函数
- 相对熵存在最大值，但是与离散信源不同，对信源不同限制条件下的最大熵不相同
- 连续信源输出的随机变量（随机向量）通过确定的一一对应变换后，相对熵会发生变化
  1. 将随机变量 $X$ 和 $Y$ 的变换关系记作 $X=f(Y)$, 则有
$$h(y)=h(x)-E_{X}\left\{\log \left|J\left(\frac{X}{Y}\right)\right|\right\}$$
  其中
$$J\left(\frac{X}{Y}\right)=\frac{\mathrm{d} f(Y)}{\mathrm{d} Y}$$
  若 X、Y 为矩阵，则
$$
J\left(\frac{\mathbf{X}}{\mathbf{Y}}\right)=\left|\begin{array}{ccc}
\frac{\partial f_{1}}{\partial Y_{1}} & \cdots & \frac{\partial f_{N}}{\partial Y_{1}} \\
\vdots & \ddots & \vdots \\
\frac{\partial f_{1}}{\partial Y_{N}} & \cdots & \frac{\partial f_{N}}{\partial Y_{N}}
\end{array}\right|
$$

> $J(\frac{Y}{X})=-J(\frac{X}{Y})$

> $J(\frac{Ax}{x})=\operatorname{det} A$

> $p(y)=p(x)|\frac{dx}{dy}|$

### 6-1-5 最大相对熵定理

**定理 6.1** 设 $p(x)$ 是在 $(a, b)$ 区间具有某种分布的概率密度函数，其约束条件为
$\int_{a}^{b} p(x) d x=1$；
$q(x)$ 为不同于 $p(x)$ 的其他分布，但约束条件和 $p(x)$ 相同，也为
$\int_{a}^{b} q(x) d x=1$。
则有
$$-\int_{a}^{b} p(x) \log p(x) d x \leq-\int_{a}^{b} p(x) \log q(x) d x$$
区间 $(a, b)$ 在极限情况 $(-\infty, \infty)$ 时, 上式仍然成立。

**定理 6.2 峰值功率受限条件下信源的最大熵定理** 
若某信源输出信号的峰值功率受限，即信号的取值被限定在某一有限范围内，
则在限定的范围内，当输出信号幅度的**概率密度函数是均匀分布时**该信源达到**最大熵**值。

设 $a=-A,b=A$，则峰值功率为 $P_s=A^2$，该信源的最大相对熵为
$$h(x)_{max}=\operatorname{lb}2A=\frac{1}{2}\operatorname{lb}(4P_s)$$

如果将对应的分布称为最佳分布并用 $p_{opt}$ 表示，则有

$$p_{\text {opt }}=\left\{\begin{array}{cc}
\frac{1}{2 \sqrt{P_{s}}} \text { 或 } \frac{1}{2 A}, & -A<x<A \\
0, & \text { 其他 }
\end{array}\right.$$

**定理 6.3 平均功率受限条件下信源的最大熵定理**
若某信源输出信号的平均功率被限定，则当其输出信号的概率密度函数 $p(x)$ 是高斯分布时，
信源达到最大熵值；对于 N 维连续信源来说，若N维随机矢量的协方差矩阵被限定，
则 N 维连续信源为 N 维高斯分布时达到最大熵值。

> 平均交流功率：方差

**定理6.4 均值受限条件下信源的最大熵定理**
若某连续信源 X 输出非负信号的均值被限定，则其输出信号幅度为指数分布时，
连续信源 X 达到最大熵值。

### 6-1-6 熵功率和熵功率不等式

#### 熵功率

熵功率是给定零均值高斯分布的相对熵 $h(x)_{max}$，反推出平均功率：
$$\overline{P}=\frac{1}{2\pi}e^{2h(x)}\leq\frac{1}{2\pi}e^{2h(x)_{max}}=P$$

可以采用 $P-\overline{P}$ 衡量连续信源的冗余度

#### 熵功率不等式

两个零均值统计独立的连续随机变量 X 和 Z，平均功率分别为 $P_X$ 和 $P_Z$，
则随机变量 $Y=X+Z$ 的平均功率 $P_Y=P_X+P_Z$

$\bar{P}_X+\bar{P}_Z\leq\bar{P}_Y\leq P_X+P_Z$，当 X 和 Z 为独立高斯随机变量时等号成立

## 6-2 连续消息在信道上的传输问题

- 连续消息的平均互信息量 $I(X;Y)=h(x)-h(x|y)=h(y)-h(y|x)=h(x)+h(y)-h( xy )$ 比特 /样值
- 连续消息序列的平均互信息量 $I(X^N;Y)=h(x)-h(x|y)=h(y)-h(y|x)=h(x)+h(y)-h( xy )$ 比特 /样值
- 波形信号的平均互信息量  $I(x(t);y(t))=\lim_{N\rightarrow\infty}I(X^N;Y^N)$ 比特/样值序列
  - $R_s=\lim_{N\rightarrow\infty}\frac{1}{T}I(X^N;Y^N)$ 比特/秒
  - 对于带宽为B，时长为T的信号，等价于计算长度N=2BT的连续消息序列的平均互信息量

连续消息平均互信息量性质:
- 非负性
- 对称性
- 上凸函数
- 数据处理定理：若 $X \rightarrow Y \rightarrow Z$ 形成马氏链，则$I(X;Z)\leq I(X;Y)$
- 一一对应的变换不改变平均互信息量关系
- $I\left(\mathbf{X}^{N} ; \mathbf{Y}^{N}\right)$ 和 $I\left(X_{i} ; Y_{i}\right)$ 的关系
  1. 如果多维连续信源无记忆, 则 $I\left(\mathbf{X}^{N} ; \mathbf{Y}^{N}\right) \geq \sum_{i=1}^{N} I\left(X_{i} ; Y_{i}\right)$
  2. 如果多维连续信道无记忆, 则 $I\left(\mathbf{X}^{N} ; \mathbf{Y}^{N}\right) \leq \sum_{i=1}^{N} I\left(X_{i} ; Y_{i}\right)$
  3. 如果信源和信道均无记忆, 则 $I\left(\mathbf{X}^{N} ; \mathbf{Y}^{N}\right)=\sum_{i=1}^{N} I\left(X_{i} ; Y_{i}\right)$

单符号加性信道的平均互信息量: 
$$I ( X; Y)=h( y )-h( y | x)=h( y )-h(n)$$

多维加性信道的平均互信息量: 
$$I ( X^N; Y^N)=h( y )-h( y | x)=h( y )-h(n)$$

对于多维加性信道, 信道无记忆等价于噪声分量独立
$$p(\mathbf{y} \mid \mathbf{x})=\prod_{i=1}^{N} p\left(y_{i} \mid x_{i}\right)=p(\mathbf{n})=\prod_{i=1}^{N} p\left(n_{i}\right)$$

加性波形信道的平均互信息量
$$R_{t}=\lim _{T \rightarrow \infty} \frac{1}{T} I\left(\mathbf{X}^{N} ; \mathbf{Y}^{N}\right)=\lim _{T \rightarrow \infty} \frac{1}{T}[h(\mathbf{y})-h(\mathbf{n})]$$

## 6-3 香农信道容量公式
### 6-3-1 加性信道的信道容量

加性噪声：$p ( y | x )=p (n )$

连续加性信道的信道容量
- 单符号信道
$$C=\max _{p(x)} I(\mathbf{X} ; \mathbf{Y})=\max _{p(x)}[h(y)-h(y \mid x)]=\max _{p(x)}[h(y)-h(n)]$$

- 多维信道
$$C=\max _{p(\mathbf{x})} I\left(\mathbf{X}^{N} ; \mathbf{Y}^{N}\right)=\max _{p(\mathbf{x})}[h(\mathbf{y})-h(\mathbf{y} \mid \mathbf{x})]=\max _{p(\mathbf{x})}[h(\mathbf{y})-h(\mathbf{n})]$$

- 波形信道
$$\begin{aligned}
&C=\max _{p(\mathbf{x})}\left\{\lim _{T \rightarrow \infty} \frac{1}{T} I\left(\mathbf{X}^{N} ; \mathbf{Y}^{N}\right)\right\}=\max _{p(\mathbf{(})}\left\{\lim _{T \rightarrow \infty} \frac{1}{T}[h(\mathbf{y})-h(\mathbf{y} \mid \mathbf{x})]\right\} \\
&=\max _{p(\mathbf{x})}\left\{\lim _{T \rightarrow \infty} \frac{1}{T}[h(\mathbf{y})-h(\mathbf{n})]\right\}=\lim _{T \rightarrow \infty} \frac{1}{T}\left\{\max _{p(\mathbf{x})}[h(\mathbf{y})-h(\mathbf{n})]\right\}
\end{aligned}$$

- 单符号高斯加性信道：
  - $h(n)=\ln\sqrt{2\pi e \sigma^2}$
  - $C=\frac{1}{2}\ln(1+\frac{S}{N})$ 奈特 /样值

- 单符号非高斯加性信道
  - $\frac{1}{2}\ln(1+\frac{S}{N})\leq C\leq \frac{1}{2}\ln(\frac{S+N}{\overline{N}})$ 奈特 /样值
  - 同等噪声功率情况下高斯噪声是最坏情况噪声（使得信道容量最小）

- 多维无记忆高斯加性信道

**注水原则**：应当向 噪声功率较小分量度 分配 较多的输入信号功率；若噪声各分量等功率，则输入信号等功率分配最优

- 多维有记忆高斯加性信道

### 6-3-2 带限AWGN信道的信道容量

WGN采样点为服从独立同分布的高斯随机变量

WGN各样值方差均为 $N_0 B$（即自相关函数）

（AWGN信道中）当输入信号的样值服从零均值独立高斯分布，且每个样值的功率相等时（即输入信号具有高斯白噪声特性）

带限AWGN信道的信道容量为 $C=BT\ln(1+\frac{P_s}{N_0B})$

单位时间的信道容量（**Shannon 公式**）：$C_T=B\ln(1+\frac{P_s}{N_0B})$

Shannon公式成立的条件
1. 输入信号平均功率为 $P_s$（为AWGN时达到信道容量）
2. 带宽为 $B$ 的带限信道
3. 噪声为AWGN，功率谱密度为 $N_0/2$

### 有色加性高斯噪声信道的信道容量

### 6-3-3 香农公式的意义

1. 信道容量与所传输信号的有效带宽成正比，信号的有效带宽越宽，信道容量越大
2. 信道容量与信道上的信号噪声比有关，信噪比越大，信道容量也越大，但其制约规律呈对数关系
3. 信道容量 C、有效带宽 B 和信噪比 S/N 可以相互起补偿作用，即可以互换
4. 当信噪比小于1时，信道的信道容量并不等于0，这说明此时信道仍具有传输消息的能力。也就是说，信噪比小于1时仍能进行可靠的通信
5. 信号有效带宽无限时，信道容量 $C=\frac{P_s}{N_0}\operatorname{lb}e\approx 1.44\frac{P_s}{N_0}bit/s$
6. $\frac{E_b}{N_0}=\frac{C}{R}\ln2\geq\ln2$
7. 香农公式是在噪声为AWGN情况推得的，对那些不是白色高斯噪声的信道干扰而言，其信道容量应该大于按香农公式计算的结果
