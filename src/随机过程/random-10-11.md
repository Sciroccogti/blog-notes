# 第十章 信号检测

信号的统计推断又称为统计信号处理，是指根据观察数据与待推断数据之间的先验统计关联信息
（如联合概率密度函数、条件概率密度函数等），由观察数据的情况来推断另一个阈值关联的数据情况。

所谓假设检验，就是在已知 不可直接观察的随机现象的样本空间 $\mathcal{H}$ 和 可直接观察的随机现象的样本空间 $\mathcal{O}$
的联合概率函数的条件下，根据当前观察到的 $\mathcal{O}$ 的取值，来推断到底是 $\mathcal{H}$ 中哪一个假设导致了目前的观察值。

信号检测是假设检验的一种，当观察空间和待检验空间都是信号时，这种假设检验就是**信号检测**。

$$f_{y|b}(y|b)=f_z(y-RAb)=\frac{1}{(2\pi)^{K/2}det(R)^{-1/2}}exp\left\{-\frac{(y-RAb)^TR^{-1}(y-RAb)}{2}\right\}$$

## 10-2 常见判决准则

### Bayes 判决准则

如果输入 “假设” 为 $H_{0}, H_{1}, \cdots, H_{N-1}$, 设 $c_{j i}$ 为将 $H_{i}$ 判定为 $H_{j}$ 的代价, 所谓 Bayes 䖺堆则就是观测空间的一个判决分割 $\pi_{\mathcal{O}}: \mathcal{O}_{0}, \mathcal{O}_{1}, \cdots, \mathcal{O}_{N-1}$, 这种判决分割使下列风险收敛达到最小, 即
$$R\left(\pi_{\mathcal{O}}\right)=\sum_{i, j=0}^{N-1} c_{j i} P\left(H_{j} \mid H_{i}\right) P\left(H_{i}\right)$$

$P\left(H_{i}\right)$ 为在判决分割 $\pi_\mathcal{O}$ 下将 $H_i$ 判决为 $H_j$ 的概率

**定理** (二择一 Bayes 检测) 只有两个 “假设” 的 Bayes 检测, 代价满足 $c_{10}>c_{00}, c_{01}>c_{11}$ 。设两个 “假设” 分别为 $H_{0} 、 H_{1}$, 观测空间 $\mathcal{O} \subset \mathbb{R}^{n}$, 设观察向量为 $x$, 记
$$
\lambda(\boldsymbol{x})=\frac{P\left(\boldsymbol{x} \mid H_{1}\right)}{P\left(\boldsymbol{x} \mid H_{0}\right)}, \quad \lambda_{\mathrm{B}}=\frac{P\left(H_{0}\right)\left(c_{10}-c_{00}\right)}{P\left(H_{1}\right)\left(c_{01}-c_{11}\right)}
$$
则 $H_{1}$ 的 Bayes 判决区域为 $\mathcal{O}_{1}=\left\{x \in \mathcal{O} \mid \lambda(x) \geqslant \lambda_{B}\right\}, H_{0}$ 的判决区域为 $\mathcal{O}_{0}=\{x \in \mathcal{O}|\left.\lambda(x)<\lambda_{B}\right\}$ 。这里 $\lambda(x)$ 被称为似然比, $\lambda_{B}$ 被称为门限似然比。

# 第十一章 信号参数估计

估计与假设检验并无本质性的差别，只是待推断的对象分别是“离散”和“连续”的差别。

信号估计按照其待估计的对象可以分为“信号参数估计”与“信号波形估计”这两类。
