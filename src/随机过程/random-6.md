# 第六章 二阶矩过程的数学分析

## 6-1 离散时间随机过程的均方收敛

**概率分布意义**上相等：概率分布函数恒等：$F_X(t)\equiv F_Y(t)$

**概率意义**上相等（几乎处处相等）：事件发生概率相等：$P\{X=Y\}=1$

**均方意义**上相等：X 与 Y 的二阶矩存在且满足 $E\{|X-Y|^2\}=\int_{\mathbb{R}^2}|x-y|^2f_{XY}(x,y)dxdy=0$

**Loève准则**：$X_n$ 均方收敛 当且仅当 序列 $X_n$ 的自相关函数 $R_X[n_1,n_2]$ 满足 $\lim_{n_1,n_2\rightarrow\infty}R_X[n_1,n_2]=C$，C 为常数。

## 6-2 连续时间随机过程的均方连续

对于设有定义于时间指标集 $\mathbb{T}$ 上的连续时间随机过程 $X(t),\mathbb{T}$ 是 $\mathbb{R}$ 或某个区间 $[a,b]$，若对 $t_{0} \in \mathbb{T}$，当 $t \rightarrow t_{0}$ 时有
$$\operatorname{ms} \lim _{t \rightarrow t_{0}} X(t)=X\left(t_{0}\right)$$
则称随机过程 $X(t)$ 在 $t_{0}$ 点均方连续; 若对 $\mathbb{T}$ 内任意一点 $t_{0},X(t)$ 都在 $t_{0}$ 点连续，则称 $X(t)$ 在 $\mathbb{T}$ 上均方连续。

**性质**：若 $X(t)$ 为宽平稳过程，则 $X(t)$ 在 $\mathbb{T}$ 上均方连续，当且仅当 $R(\tau)$ 在 $\tau=0$ 点连续。

## 6-3 连续时间随机过程的均方导数

设有定义于连续时间指标集 $\mathbb{T}$ 上的随机过程 $X(t)$，若有
$$\operatorname{ms}_{\tau \rightarrow 0} \frac{X\left(t_{0}+\tau\right)-X\left(t_{0}\right)}{\tau}=Y\left(t_{0}\right)$$

则称 $X(t)$ 在 $t_{0}$ 点均方可导，并称 $Y\left(t_{0}\right)$ 为 $X(t)$ 在 $t_{0}$ 点的均方导数，$Y\left(t_{0}\right)$ 有时也记为 $\mathrm{d} X\left(t_{0}\right) / \mathrm{d} t 、 X^{\prime}\left(t_{0}\right)$ 或 $X^{(1)}\left(t_{0}\right)$ 。若对任意 $t_{0} \in \mathbb{T},X(t)$ 都均方可导，则称 $X(t)$ 在 $\mathbb{T}$ 上 均方可导。

也即：
$$\lim _{\tau \rightarrow 0} E\left\{\left[\frac{X\left(t_{0}+\tau\right)-X\left(t_{0}\right)}{\tau}-Y\left(t_{0}\right)\right]^{2}\right\}=0$$

$X(t)$ 在 $t_{0}$ 点的 $n$ 阶均方导数可以递归地定义为
$$\frac{\mathrm{d}^{n} X\left(t_{0}\right)}{\mathrm{d} t^{n}}=X^{(n)}\left(t_{0}\right)=\operatorname{ms}_{\tau \rightarrow 0} \frac{X^{(n-1)}\left(t_{0}+\tau\right)-X^{(n-1)}\left(t_{0}\right)}{\tau}$$

## 6-3 连续时间随机过程的均方积分

可积的证明，可以先算出 $X(t)$ 的积分为 $Y(t)$，然后再证明 $Y(t)$ 的导数为 $X(t)$，以及 $Y(0)=0$ 即可
