# 怎样用分次与多项式消去 Herr 复形的二次障碍

## 命题

取交换环 $O$、交换 $O$-代数 $A$、$A$-模 $D$ 及子模 $N$，素数 $p$，$X,Q\in A$，以及整数 $M,a\ge0$。定义 $U=\{y\in D:Q^My\in N\}$，即允许分母的第一坐标空间。Herr 复形在这里是由两个互相交换的差分算子构成的复形。记 $\varphi,\gamma:D\to D$ 为两条交换的 $O$-线性算子，

$$
d_1(y,z)=(\gamma-1)y-(\varphi-1)z,\qquad (y,z)\in U\times XN.
$$

假定 $X$ 在 $D$ 上作用单射，存在 $O$-线性 $\delta$ 使 $X\delta=\gamma-1$，且 $\delta$ 保持 $N$ 与 $U$。给定 $R(T)\in O[T]$ 与 $C\in O$，另假定：

1. $\delta R(\delta)(U)\subset N$，且若 $y\in U,\ py\in N$，则 $y\in N$。如果 $y\in U,\ Cy\in N$，也有 $y\in N$。
2. $(\varphi-1)(XN)\subset U$，且 $\varphi(X^{a+1}N)\subset X^{a+1}N$。
3. 对每个 $n\in N$ 可写 $CXn=(\gamma-1)Xx+X^{a+1}m$，其中 $x,m\in N$。
4. $1-\varphi$ 在 $X^{a+1}N$ 上满射。

那么对每个 $w\in U$，如果 $p^jXw\in d_1(U\times XN)$ 对某个 $j\ge0$ 成立，就有

$$
R(0)C Xw\in d_1(U\times XN).
$$

工程把后一个包含称为二次余边界。结论给出一个统一标量，消去每个已知被某个 $p$ 幂消去的障碍，无需知道该 $j$ 有多大。

## 证明

设 $p^jXw=d_1(y,Xn)$，其中 $y\in U,n\in N$。按第 3 条写 $CXn=(\gamma-1)Xx+X^{a+1}m$，并令

$$
y'=Cy-(\varphi-1)Xx\in U.
$$

用 $\varphi,\gamma$ 交换，将 $p^jXw$ 的方程乘以 $C$ 得

$$
Cp^jXw=(\gamma-1)y'+(1-\varphi)X^{a+1}m.
$$

因第 2 条，最后一项可写成 $X^{a+1}m'$，其中 $m'\in N$。用 $X\delta=\gamma-1$ 并消掉单射的 $X$，得到

$$
Cp^jw=\delta y'+X^am'.
$$

施加 $R(\delta)$。右边第一项属于 $N$，依第 1 条；第二项也属于 $N$，因为 $\delta$ 保持 $N$。因此 $Cp^jR(\delta)w\in N$。$R(\delta)w$ 本身在 $U$ 中，先连续用 $p$ 的饱和性去掉 $p^j$，再用 $C$ 的饱和性去掉 $C$，得到

$$
R(\delta)w\in N.
$$

现在写 $R(T)=R(0)+TR_1(T)$。对 $R(\delta)w\in N$ 再用第 3 条，取 $x_2,m_2\in N$ 使

$$
CXR(\delta)w=(\gamma-1)Xx_2+X^{a+1}m_2 .
$$

然后按第 4 条取 $z_2\in N$ 使 $X^{a+1}m_2=(1-\varphi)X^{a+1}z_2$。代回 $R(0)C Xw$，得到

$$
\begin{aligned}
R(0)CXw
 &=CXR(\delta)w-CX\delta R_1(\delta)w\\
 &=d_1\bigl(Xx_2-CR_1(\delta)w,\ X^{a+1}z_2\bigr).
\end{aligned}
$$

第一坐标属于 $U$，因为 $\delta$ 保持 $U$，第二坐标属于 $XN$。这给出了二次障碍的确切余边界。

## 两个因子的来历

在工程的不分歧情形，$p=\ell\ge3$，$u\in\mathbb Z_\ell^\times$ 满足 $v_\ell(u-1)=1$，$u_1=u^{\ell-1}$。[分次与完备性的两个算子方程](%E6%80%8E%E6%A0%B7%E4%BB%8EWach%E6%A8%A1%E7%9A%84%E5%88%86%E6%AC%A1%E4%B8%8E%E5%AE%8C%E5%A4%87%E6%80%A7%E5%8F%96%E5%BE%97%E4%B8%A4%E4%B8%AA%E7%AE%97%E5%AD%90%E6%96%B9%E7%A8%8B.md)给出

$$
C=\prod_{i=1}^a(1-u_1^i),\qquad a=\lfloor M/(\ell-1)\rfloor .
$$

它是一个单位乘以 $\ell^{a+v_\ell(a!)}$，所以 $p$ 饱和性已蕴含 $C$ 饱和性。另有

$$
R(T)=\prod_{j\in J}\bigl(T-(1-u^{-j})/\ell\bigr).
$$

分次上的特征值关系使 $\delta R(\delta)(U)\subset N$。集合 $J$ 包含由过滤跳点平移得到的所有非零指标。零指标的特征值是 $0$，由额外的 $\delta$ 处理。对 $j\ne0$，$v_\ell((1-u^{-j})/\ell)=v_\ell(j)$，所以 $v_\ell(R(0))=\sum_{j\in J}v_\ell(j)$。这两个赋值正是 $e_U$ 的来源。

## Lean 对照

- `C1` 对应允许坐标 $U\times XN$，`d1` 对应差分，`TorsKilled` 写出倍数成为余边界的统一要求。[Statement.lean:61](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CoboundaryTransfers/Statement.lean#L61) · [同文件:75](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CoboundaryTransfers/Statement.lean#L75)
- `claim_key` 从 $p^jXw=d_1(y,z)$ 推出 $CR(\delta)w\in N$，`claim_fin` 用 $R(T)-R(0)$ 构造余边界。两项由 `torsionKilledCriterion_holds` 合用。[TorsionKilledCriterionHolds.lean:106](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CoboundaryTransfers/GammaStableTransfers/TorsionKilledCriterionHolds.lean#L106) · [同文件:170](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CoboundaryTransfers/GammaStableTransfers/TorsionKilledCriterionHolds.lean#L170) · [同文件:200](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CoboundaryTransfers/GammaStableTransfers/TorsionKilledCriterionHolds.lean#L200)
- `lifta_core` 接入分次、周期比较和上述多项式。它用单位倍的 $\ell$ 幂代替 $R(0)C$，最后以略宽的 $a_0=a+1$ 做统一的 $e_U$ 上界。[BaseChangePreservesUnitaryOf.lean:1050](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/BaseChangePreservesUnitaryOf.lean#L1050)

状态为源码级推导。另行未重新编译。这篇把多项式整化关系列为输入，并展开从它到二次障碍消失的论证。
