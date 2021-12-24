## 6-1 Moore-Penrose 方程

**定义**：设 $A\in C^{s\times n}$，若 $G\in C^{n\times s}$ 满足下述四个条件，则称 $G$ 是 $A$ 的广义逆矩阵：
1. $AGA=A$
2. $GAG=G$
3. $(AG)^H=AG$
4. $(GA)^H=GA$

这四个方程也称为 M-P 方程

1. 若 $A$ 为可逆阵，则 $A^{-1}$ 为 $A$ 的广义逆
2. $A=O_{s\times n}, G=O_{n\times s}$

**定理**：设 $A\in C^{s\times n}$，则 $A$ 的广义逆矩阵是存在的，且是唯一的。$A$ 的广义逆记为 $A^+$

${A^H}^{-1}={A^{-1}}^{H}$

由广义逆存在性的证明可知，如果矩阵 $A$ 的满秩分解为 $A=BC$，则 $A^+=C^H(CC^H)^{-1}(B^HB)^{-1}B^H$

## 6-2 广义逆矩阵的性质

### 6-2-1 分块矩阵的广义逆

1. $O_{s \times n}^{+}=O_{n \times s}$
2. $\left(\begin{array}{ll}A & O \\ O & B\end{array}\right)^{+}=\left(\begin{array}{cc}A^{+} & O \\ O & B^{+}\end{array}\right),\left(\begin{array}{ll}O & A \\ B & O\end{array}\right)^{+}=\left(\begin{array}{cc}O & B^{+} \\ A^{+} & O\end{array}\right)$
3. $\left(\begin{array}{l}A \\ O\end{array}\right)^{+}=\left(\begin{array}{ll}A^{+} & O\end{array}\right), \quad\left(\begin{array}{ll}A & O\end{array}\right)^{+}=\left(\begin{array}{l}A^{+} \\ O\end{array}\right)$
4. $\left(\begin{array}{cccc}\lambda_{1} & & & \\ & \lambda_{2} & & \\ & & \ddots & \\ & & & \lambda_{n}\end{array}\right)^{+}=\left(\begin{array}{cccc}\lambda_{1}^{+} & & & \\ & \lambda_{2}^{+} & & \\ & & \ddots & \\ & & & \lambda_{n}^{+}\end{array}\right)$,
其中, $\lambda_{j}^{+}=\left\{\begin{array}{cc}\lambda_{j}^{-1}, & \lambda_{j} \neq 0 \\ 0, & \lambda_{j}=0\end{array}\right.$

### 6-2-2 运算性质

注意：$(AB)^+$ 与 $B^+A^+$ 一般不相等！除非 $B=A^H$

**定理**：设 $A \in C^{s \times n}$, 则:
1. $\left(A^{+}\right)^{+}=A$
2. $\left(A^{H}\right)^{+}=\left(A^{+}\right)^{H}$
3. $\left(A^{T}\right)^{+}=\left(A^{+}\right)^{T}$
4. 若 $k$ 为实数, 则 $(kA)^{+}=k^{+}A^{+},k^{+}=\left\{\begin{array}{c}k^{-1},k\neq 0 \\ 0,k=0\end{array}\right.$
5. $A^{H}=A^{H}AA^{+}=A^{+}AA^{H}$
6. $\left(A^{H} A\right)^{+}=A^{+}\left(A^{H}\right)^{+}; \left(A A^{H}\right)^{+}=\left(A^{H}\right)^{+} A^{+}$
7. $A^{+}=\left(A^{H} A\right)^{+} A^{H}=A^{H}\left(A A^{H}\right)^{+}$
8. 若 $U, V$ 是酉矩阵, 则 $(U A V)^{+}=V^{H} A^{+} U^{H}$
9. $A^{+} A B=A^{+} A C \Leftrightarrow A B=A C$

若 $A$ 为 Hermite 矩阵，则 $A^+$ 也为 Hermite 矩阵

若 $A$ 为正规阵，则 $(A^2)^+=(A^+)^2$

### 6-2-3 广义逆的值域与核

**定理**
1. $A A^{+} x=\left\{\begin{array}{ll}x,& x \in R(A) \\ \theta,& x \in K\left(A^{H}\right)\end{array}\right.$
2. $A^{+} A x=\left\{\begin{array}{ll}x,& x \in R\left(A^{H}\right) \\ \theta,& x \in K(A)\end{array}\right.$
3. $R\left(A^{+}\right)=R\left(A^{H}\right)=R\left(A^{H} A\right)=R\left(A^{+} A\right)=K\left(I-A^{+} A\right)$
4. $R(A)^{\perp}=K\left(A^{H}\right)=K\left(A^{+}\right)=R\left(I-A A^{+}\right)$
5. $R\left(A^{+}\right)^{\perp}=K(A)=K\left(A^{H} A\right)=R\left(I-A^{+} A\right)$

助记：
1. 在涉及到值域和核空间的时候，$A^H,A^+$ 的性质类似
2. $K^\perp(A)=R(A^H)=R(A^\perp), R^\perp=K(A^H)$
3. 只要记助记，定理就会证明了

## 6-3 广义逆矩阵的应用：最小二乘解

当线性方程组 $A x=b$ 无解时, 如何求最好的近似解, 即求 $x$ 使 得 $\|A x-b\|_{2}$ 最小?

**定义**：
设 $A \in C^{s \times n}, x_{0} \in C^{n}$, 若
$$\left\|b-A x_{0}\right\|=\min _{x \in C^{n}}\|b-A x\|$$
则称 $x_{0}$ 是线性方程组 $A x=b$ 的最小二乘解, 长度最小的最小二乘解称为极小最小二乘解

**定理**：
$\eta$ 是 $A x=b$ 的最小二乘解 $\Leftrightarrow \eta$ 是 $A^{H} A x=A^{H} b$ 的解

**定理**：
$A x=b$ 的最小二乘解的通解
为: $x=A^{+} b+\left(I-A^{+} A\right) y, \forall y \in C^{n}$, 其中, $A^{+} b$ 是唯一的极小最小二乘解
