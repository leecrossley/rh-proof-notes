# 为什么 II 类和 III 类使用的二进层数有多项式高度

固定本原 Dirichlet 特征 $\chi$，模数 $Q$、阶 $o$，以及 [宿主 $h$](%E6%AD%A3%E5%8F%B7%E4%B8%8A%E5%90%8C%E8%B0%83%E7%9A%84%E4%B8%83%E7%A7%8D%E9%95%BF%E5%BA%A6%E4%BC%B0%E8%AE%A1%E6%80%8E%E6%A0%B7%E9%80%89%E7%94%A8.md)，其基础特征为 $\chi$，模数 $N$。记 $p_1$ 为该篇所定义的、只依赖 $\chi$ 的辅助素数。取奇素数 $\ell$、项目允许的 $\ell$-进整数环 $O$、整数 $e\ge2$，及在 $H$ 上平凡、奇偶性等于 $(-1)^e$ 的模 $N$ 的 $O$-值 Dirichlet 特征 $\psi$。记 $c=c_2(\psi)$ 为模二幂分量的导子指数。设 $\theta$ 由 $\psi$ 去掉其 $\ell$-幂阶部分，再去掉其模二幂分量得到。令

$$
f_0=\operatorname{ord}_{(\mathbb Z/\operatorname{lcm}(4,\operatorname{ord}\theta)\mathbb Z)^\times}(\ell),
\qquad n_0=v_2(\ell^{f_0}-1).
$$

$\lceil\log_2(m)\rceil$ 表示最小的满足 $m\le2^j$ 的非负整数 $j$，在这里 $m\ge1$。定义

$$
\begin{aligned}
n_2&=\left\lceil\log_2\max\{\ell N4^{n_0},\,2^{c+6}o\ell^3 Q^2\}\right\rceil,\\
n_3&=\left\lceil\log_2\max\{\ell Qp_1 4^{n_0},\,8\ell^2\}\right\rceil .
\end{aligned}
$$

**命题。** 对任意非负整数 $C_0,A$，存在整数 $C_\chi$，只依赖 $\chi,C_0,A$，使对所有以上参数及两种选择 $(n',P)=(n_2,1),(n_3,p_1)$ 均有

$$
2C_0\,(\ell-1)2^{n'}(2o)
\,[\ell\,2^{n'}NP(e+1)]^A\,\log p_0(\ell NP)\le(\ell Ne)^{C_\chi}.
$$

这里 $p_0(m)$ 是最小的不整除 $m$ 且至少为 $5$ 的素数。本篇解释 II、III 类的变形估计为什么对宿主层数保持多项式规模。

## 证明

先估计 $n_0$。去掉模二幂分量后，宿主特征的阶整除 $2o$。具体地，把单位群中模二幂分量恒等的子群送入 $\chi$ 及模两个辅助素数的平方商，其像的指数整除 $\operatorname{lcm}(o,2)\mid2o$，而 $H$ 上平凡的 $\psi$ 经过该像。再去掉 $\ell$-幂阶部分，$\operatorname{ord}\theta$ 仍整除 $2o$ 且与 $\ell$ 互素。因此 $m_0=\operatorname{lcm}(4,\operatorname{ord}\theta)\mid4o$，且 $\ell$ 是模 $m_0$ 的单位。它的阶 $f_0$ 整除 $\varphi(m_0)$，后者整除 $\varphi(4o)$。对后一个整除性，可用单位群换模的满射，也可直接从欧拉函数的素幂公式看出。于是

$$
2\le n_0,\qquad
2^{n_0}\le\ell^{f_0}-1<\ell^{\varphi(4o)} .
$$

这就把模数增长的二进层长控制在 $\ell$ 的一个固定幂内。

设 $X=\ell Ne$ 和 $f=\varphi(4o)$。注意 $Q\le N,\ o\le Q$，且 $2^c\mid N$。另 $X\ge16$，因为宿主模数可被 $2^{u+2}$ 整除且 $u\ge2$。一旦 $m\ge1$，有 $2^{\lceil\log_2 m\rceil}\le2m$。于是

$$
\begin{aligned}
2^{n_2}
&\le2\max\{\ell N\ell^{2f},\,64\, 2^c o\ell^3Q^2\}
\le X^{2f+10},\\
2^{n_3}
&\le2\max\{\ell Qp_1\ell^{2f},\,8\ell^2\}
\le X^{1+(10+Q+p_1+2f)} .
\end{aligned}
$$

第一行用 $2\le X$、$128\le X^2$。第二行还可以用 $Q\le X^Q,\ p_1\le X^{p_1}$，两者在选定 $\chi$ 后都是固定参数。取
$a=(2f+10)+(1+10+Q+p_1+2f)$，便同时有 $2^{n'}\le X^a$。从第一种最大值的第二项还可直接读出 $c\le n_2$；在 III 类 $\psi$ 具有奇数阶，所以其模二幂分量平凡，$c=0\le n_3$。

由 Bertrand 定理，在 $m+5$ 与 $2(m+5)$ 之间有素数。它比 $m$ 大，故不整除 $m$，也满足下限 $5$。所以 $p_0(m)\le2m+10$。取 $B=1+p_1$，则 $P\le B\le X^B$。现在

$$
\begin{aligned}
2C_0 &\le X^{2C_0},\\
(\ell-1)2^{n'}(2o)&\le X^{1+a+2o},\\
\ell 2^{n'}NP(e+1)&\le X^{1+a+1+B+2},\\
\log p_0(\ell NP)&\le 2\ell NP+10\le X^{2+(1+1+B)+10+1}.
\end{aligned}
$$

最后一行的常数也可用更小的幂吸收。将这些幂相乘，并给第三项的指数乘 $A$，就得到所要求的 $C_\chi$。

## Lean 对照

- [`Host.nII` 和 `Host.nIII`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/DirichletPrimeToLPartMulLPowerPart.lean#L221) 给出两层的精确定义。[`hostTh1`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/OrdProjNDvd.lean#L37) 和 [`cmDatum_char_two_adic_order_bounds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/CmDatumCharTwoAdicOrderBounds.lean#L61) 将宿主群的阶界变成 $n_0$ 的界。
- [`pZeroLe`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/PZeroLe.lean#L6) 给出最小可用素数的界。
- [`arith`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/TwoPowClogLe.lean#L172) [`arith`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/TwoPowClogLe.lean#L172) 按上面展示的幂作最终估计，供 [II、III 类主证明](%E4%B8%BA%E4%BB%80%E4%B9%88II%E7%B1%BB%E5%92%8CIII%E7%B1%BB%E7%9A%84%E9%95%BF%E5%BA%A6%E5%8F%AF%E4%BB%A5%E5%90%88%E7%94%A8%E7%A7%A9%E5%9B%9B%E6%96%B9%E6%B3%95.md) 使用。本篇为发布版源码对照。
