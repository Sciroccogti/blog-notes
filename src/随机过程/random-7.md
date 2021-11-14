# 第七章 随机变量的变换

## 7-2 有限维随机变量间的变换

**定理7.2.1**：设一维随机变量 X 的概率密度函数为 $f_X(x)$，$Y=g(X)$ 是单调可微函数，则 Y 的概率密度函数为 $f_Y(y)=f_X[g^{-1}(y)]|[g^{-1}(y)]'|$

**定理7.2.4**：同维变换时，若 $det(A)\neq0$，则有 $f_Y(y)=\frac{1}{|det(A)|}f_X(A^{-1}(y-b))$

**定理7.2.6**：若 $y=g(x)$ 有一阶偏导数，则有
$$f_Y(y)=\sum^N_{n=1}\left[f_X(x)\left|det\left(\frac{\partial x}{\partial y}\right)\right|\right]_{x=x^{(n)}}$$
其中，$x^{n}$ 为 $y=g(x)$ 的 N 个实根，$\partial x / \partial y$ 为下列 Jacobi 矩阵：
$$\frac{\partial x}{\partial y}=\begin{pmatrix}
    \partial x_1/\partial y_1 & \partial x_1/\partial y_2 & \dots & \partial x_1/\partial y_n \\
    \partial x_2/\partial y_1 & \partial x_2/\partial y_2 & \dots & \partial x_2/\partial y_n \\
    \vdots & \vdots & & \vdots \\
    \partial x_n/\partial y_1 & \partial x_n/\partial y_2 & \dots & \partial x_n/\partial y_n \\
\end{pmatrix}$$

若 $y=g(x)$ 无解，则 $f_Y(y)=0$
