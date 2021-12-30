# 第二章 一维随机变量

## 2-1 一维随机变量的定义

当考虑变量 $x$ 的取值频率时，其就成了一个一维随机变量 $X$。

## 2-2 概率密度函数

**概率分布函数**：$F_X(x)=P(\{X\leq x\})$

性质：
1. $0\leq F_X(x)\leq1$
2. $\lim_{x\rightarrow+\infty}F_X(x)=1$
3. $\lim_{x\rightarrow-\infty}F_X(x)=0$
4. $F_X(x)$ 单调递增
5. $F_X(x)$ 右连续，即 $\lim_{x\rightarrow a^+}F_X(x)=F_X(x)$
6. $P(a<X\leq b)=F_X(b)-F_X(a)$
7. $P(X=a)=F_X(a)-F_X(a^-);P(a\leq X\leq b)=F_X(b)-F_X(a^-)$

**概率密度函数**定义为概率分布函数的广义导数：
$$f_X(x)=\frac{dF_X(x)}{dx}$$

性质：
1. $f_X(x)\geq0$
2. $\int^{\infty}_{-\infty}f_X(x)dx=1$
3. $P(a\leq X<b)=\int_a^{b^-}f_X(x)dx$
4. $F_X(x)=\int^x_{-\infty}f_X(x)dx$

## 2-3 数字特征

- **均值**: $m_{X}=E\{X\}=\int_{-\infty}^{\infty} x f_{X}(x) \mathrm{d} x$
- **均方**: $\psi_{X}^{2}=E\left\{X^{2}\right\}=\int_{-\infty}^{\infty} x^{2} f_{X}(x) \mathrm{d} x$
- **方差**: $\sigma_{X}^{2}=\operatorname{Var}\{X\}=E\{X^2\}-E^2\{X\}=E\left\{\left(X-m_{X}\right)^{2}\right\}$
$=\int_{-\infty}^{\infty}\left(x-m_{X}\right)^{2} f_{X}(x) \mathrm{d} x=\psi_{X}^{2}-m_{X}^{2}$
- $n$ 阶原点矩: $E\left\{X^{n}\right\}=\int_{-\infty}^{\infty} x^{n} f_{X}(x) \mathrm{d} x$
- $n$ 阶鿇对原点矩: $E\left\{|X|^{n}\right\}=\int_{-\infty}^{\infty}|x|^{n} f_{X}(x) \mathrm{d} x$
- $n$ 阶中心矩: $E\left\{\left(X-m_{X}\right)^{n}\right\}=\int_{-\infty}^{\infty}\left(x-m_{X}\right)^{n} f_{X}(x) \mathrm{d} x$
- $n$ 阶绝对中心矩: $E\left\{\left|X-m_{X}\right|^{n}\right\}=\int_{-\infty}^{\infty}\left|x-m_{X}\right|^{n} f_{X}(x) \mathrm{d} x$

### 2-3-3 熵

- 事件的信息量：$I(A)=-\log_cP(A)$
- 一维随机变量的熵：$H(X)=E\{I(X)\}=-\sum^N_{n=1}P(x_n)\log_cP(x_n)\\=-\int^\infty_{-\infty}f_X(x)\log_cf_X(x)dx$

### 常见分布

**对数分布**：$P(k)=-\frac{q^k}{k\lg p}$

**Cauchy分布**：
- 概率密度函数：$f_X(x)=\frac{\alpha/\pi}{x^2+\alpha^2},\alpha>0$
- 概率特征函数：$\Phi_X(\omega)=e^{-\alpha|\omega|}$

**Laplace分布**：
- 概率密度函数：$f_X(x)=\frac{\alpha}{2}e^{-\alpha|x|},-\infty<x<\infty,\alpha>0$
- 概率特征函数：$\Phi_X(\omega)=\frac{\alpha^2}{\omega^2+\alpha^2}$

**Poisson分布**：
- 概率质量函数：$P_k=\frac{\alpha^k}{k!}e^{-\alpha},k=0,1,2,\dots$
- 概率生成函数：$G_X(z)=e^{\alpha(z-1)}$
- 均值：$E\{X\}=\alpha$
- 方差：$Var\{X\}=\alpha$


**指数分布**：
- 概率分布函数：$F_X(x)=1-e^{-\lambda x}$
- 概率密度函数：$f_X(x)=\lambda e^{-\lambda x}, x\geq0$
- 概率特征函数：$\Phi_X(\omega)=\frac{\lambda}{\lambda-j\omega}$

- **概率质量函数**：$P(x_i)$，实际上是离散的概率密度函数
- **概率生成函数**：$G_X(z)=\sum_{k=0}^\infty z^kP(x_k)$，概率质量函数的 z 变换
- **概率分布函数**：$F_X(x)=P(\{X\leq x\})$，离散和连续都有
- **概率密度函数**：$f_X(x)=\frac{dF_X(x)}{dx}$，pdf
- **概率特征函数**：$\Phi_X(\omega)=\int_{-\infty}^\infty f_X(x)e^{j\omega x}dx=E\{e^{j\omega k}\}=\sum_{k=0}^\infty e^{j\omega k}P_k=G_X(e^{j\omega})$，概率密度函数的 ==负== Fourier 变换

# 第三章 多维随机变量

联合概率分布函数中令某个分量趋于无穷大，就得到边界概率分布函数

- **概率密度函数**：$f(x,y)$，有 $\int_{-\infty}^{+\infty}\int_{-\infty}^{+\infty} f(x,y)dxdy=1$
- **联合概率密度函数**：为联合概率分布函数的 n 阶导数
- **联合概率分布函数**：$F_X(x)=P(X\leq x),F_{XY}(x,y)=\int_{-\infty}^y\int_{-\infty}^{x} f(x,y)dxdy$
- **边界概率密度函数**：$f_X(x)=\int_{-\infty}^{+\infty}f(x,y)dy$

## 3-3 数字特征

- **均值**: $m_{X}=E\{X\}=\int_{-\infty}^{\infty}\int_{-\infty}^{\infty} x f_{XY}(x,y) \mathrm{d} x\mathrm{d} y$
- **均方**：$\psi^2_X=\int_{-\infty}^{\infty}\int_{-\infty}^{\infty} x^2 f_{XY}(x,y) \mathrm{d} x\mathrm{d} y$
- **方差**：$\sigma^2_X=\psi^2_X-m^2_X$
- **相关矩**: $R_{X_{1} X_{2}}=E\left\{X_{1} X_{2}\right\}=\int_{\mathbb{R}^{2}} x_{1} x_{2} f_{X_{1} X_{2}}\left(x_{1}, x_{2}\right) \mathrm{d} x_{1} \mathrm{~d} x_{2}$
- **协方差**: $C_{X_{1} X_{2}}=\operatorname{Cov}\left\{X_{1}, X_{2}\right\}=E\left\{\left(X_{1}-m_{X_{1}}\right)\left(X_{2}-m_{X_{2}}\right)\right\}$ $=R_{X_{1} X_{2}}-m_{X_{1}} m_{X_{2}}$
- **相关系数**: $\rho_{X_{1} X_{2}}=\frac{C_{X_{1} X_{2}}}{\sqrt{C_{X_{1} X_{1}} C_{X_{2} X_{2}}}}$
- **联合原点矩**: $E\left\{X_{1}^{m} X_{2}^{n}\right\}=\int_{\mathbb{R}^{2}} x_{1}^{m} x_{2}^{n} f_{X_{1} X_{2}}\left(x_{1}, x_{2}\right) \mathrm{d} x_{1} \mathrm{~d} x_{2}$
- **联合中心矩**: $E\left\{\left(X_{1}-m_{X_{1}}\right)^{m}\left(X_{2}-m_{X_{2}}\right)^{n}\right\}=\int_{\mathbb{R}^{2}}\left(x_{1}-m_{X_{1}}\right)^{m}\left(x_{2}-m_{X_{2}}\right)^{n} f_{X_{1} X_{2}}\left(x_{1}, x_{2}\right) \mathrm{d} x_{1} \mathrm{~d} x_{2}$

- 相关性：协方差不恒为 0
- 独立性：边界密度函数之积等于联合密度函数

## 3-4 多维随机变量分量间的关系

- **条件概率密度函数**：$f_{X|Y}(x|y)=\frac{f_{XY}(x,y)}{f_Y(y)}$
- **条件期望**：$E\{X|Y\}=\int_{-\infty}^\infty xf_{X|Y}(x|Y)dx$

### 复随机变量

一维复随机变量：$Z=X+jY$
- **均值**：$m_Z=E\{X\}+jE\{Y\}$
- **方差**：$\sigma_Z^2=E\{X^2\}+E\{Y^2\}-|m_Z|^2$