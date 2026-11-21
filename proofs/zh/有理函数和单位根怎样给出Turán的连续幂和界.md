# 有理函数和单位根怎样给出Turán的连续幂和界

**命题（[`turan2Main`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/Turan2Main.lean#L29)）。** 对任意整数 $n\ge1,m\ge0$，若 $z_1,\ldots,z_n\in\mathbb C$ 满足 $|z_i|\le1$，且至少有一个 $|z_i|=1$，则存在整数 $k\in[m+1,m+n]$，使

$$
\left|\sum_{i=1}^n z_i^k\right|\ge
 \left(\frac{n}{1600(m+n)}\right)^n .
 \tag{1}
$$

[`turan_power_sum_bound`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/TuranPowerSumBound.lean#L12) 将这一结论交给筛选用的 Deuring–Heilbronn 排斥。这条证明的结论取幂和的模。此前的实部版使用附加几何条件和 Fejér 权。[实部版的连续阶数证明](%E5%A4%8D%E5%B9%82%E5%92%8C%E4%B8%BA%E4%BB%80%E4%B9%88%E5%9C%A8%E4%BB%BB%E4%BD%95%E8%BF%9E%E7%BB%AD%E9%98%B6%E6%95%B0%E6%AE%B5%E4%B8%AD%E9%83%BD%E6%9C%89%E5%A4%A7%E5%80%BC.md)

## 一、在小区间内找一个离所有模长有足够乘积距离的半径

先证明一个实变量引理。给定带重复的 $n$ 个实数 $t_i$、任意中心 $b\in\mathbb R$ 和 $r>0$，存在 $|\rho-b|\le r$ 使

$$
\prod_i|\rho-t_i|\ge(r/25)^n. \tag{2}
$$

空列成立。若 $n>0$，以 $b-4r/5,b,b+4r/5$ 为中心，各取半径 $2r/5$ 的开区间。三个开区间两两不交，至少一个包含至多 $n/3$ 个带重数的点。记其中心为 $b'$，内部点的个数为 $s$。对这 $s<n$ 个点用归纳假设，在 $|\rho-b'|\le r/5$ 中找 $\rho$，使其距离乘积至少 $(r/125)^s$。对其他点，$|\rho-t_i|\ge2r/5-r/5=r/5$。于是整个乘积至少

$$
(r/125)^s(r/5)^{n-s}=(r/25)^n5^{n-2s}\ge(r/25)^n.
$$

并且 $|\rho-b|\le r/5+4r/5=r$，完成归纳。

用 (2) 对 $t_i=|z_i|$、$r=n/[6(m+n)]$、$b=1-2r$ 选 $\rho$。有 $1-3r\le\rho\le1-r$，故 $0<\rho<1$。写 $P=\prod_i|\rho-|z_i||$，则 $P\ge(r/25)^n>0$。此外，令 $q_0=\lfloor (m+n)/n\rfloor$，有 $m+1\le q_0n\le m+n$。Bernoulli 不等式给出

$$
\rho^{q_0}\ge1-q_0(1-\rho)\ge1-3q_0r\ge\frac12,\qquad
 \rho^{m+1}\ge \rho^{q_0n}\ge2^{-n}.
$$

所以 $\rho^{m+1}P\ge(n/[300(m+n)])^n$。

## 二、若 $n$ 个连续幂和都小，则一个有理函数在圆上处处小

设 $p_k=\sum_i z_i^k$，$B=(n/[1600(m+n)])^n$。反设 (1) 在整个阶数区间失败，即 $|p_{m+b+1}|<B$ 对 $0\le b<n$ 成立。定义

$$
H(w)=\sum_i\frac{(z_iw)^{m+1}}{1-z_iw},\qquad
 Q(w)=\prod_i(1-z_iw)=\sum_{a=0}^n q_a w^a .
$$

由乘积展开，$\sum_a |q_a|\le\prod_i(1+|z_i|)\le2^n$。通分后 $Q(w)H(w)/w^{m+1}$ 是次数至多 $n-1$ 的多项式。在 $|w|<1$ 把每个分式作几何级数展开，便知 $w^b$ 的系数是 $\sum_{a=0}^b q_a p_{m+1+b-a}$。系数比较在小圆内完成，所得多项式恒等式处处成立。这里用到的幂和下标都在 $[m+1,m+n]$ 内。所以在半径 $1/\rho>1$ 的圆周上，

$$
|Q(w)H(w)|\le |w|^{m+1}\,n|w|^n\,2^n B .
\tag{3}
$$

另一方面，反三角不等式给出 $|Q(w)|\ge\rho^{-n} P>0$。除以该界，(3) 给

$$
|H(w)|\le\frac{n2^nB}{\rho^{m+1}P}\le n(3/8)^n <1 .
\tag{4}
$$

末式来自 $(8/3)^n\ge1+(5/3)n>n$。

## 三、沿圆周取单位根平均

置 $u_i=z_i/\rho$。每个 $|u_i|\ne1$，至少有一个 $|u_i|>1$。对整数 $N>m+1$，在圆周上代入 $w=\omega^j/\rho$，其中 $\omega=e^{2\pi i/N}$。对固定的 $u_i$，恒等式

$$
\frac{(u_i\omega^j)^{m+1}}{1-u_i\omega^j}
 =\frac{\sum_{\ell=0}^{N-1}(u_i\omega^j)^{m+1+\ell}}{1-u_i^N}
$$

是有限几何级数。对 $j=0,\ldots,N-1$ 取平均，指数从 $m+1$ 到 $m+N$，只剩其中唯一的 $N$ 倍数 $N$。因此

$$
\frac1N\sum_{j=0}^{N-1}H(\omega^j/\rho)
 =\sum_i \frac{u_i^N}{1-u_i^N}.
$$

当 $N\to\infty$，$|u_i|<1$ 的项趋于 $0$，$|u_i|>1$ 的项趋于 $-1$，后一项可改写为 $1/(u_i^{-N}-1)$。于是平均的极限是负的外部点个数，其模至少为 $1$。这和 (4) 给出的统一严格上界矛盾，完成证明。

## Lean 对照

- [`exists_far_from_points`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/ExistsFarFromPoints.lean#L92) `exists_far_from_points`、[`prodDist`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/ExistsFarFromPoints.lean#L119) `prodDist` 证明 (2)。[区间递归第 92、119 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/ExistsFarFromPoints.lean)
- [`Tbound`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/HDSucc.lean#L28) `Tbound` 给 (3)。源码用翻转后的多项式系数与递推证明同一系数恒等式，正文用几何级数解释它。[`tp_sum_norm`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/TpCoeffNorm.lean#L54) `tp_sum_norm` 给系数绝对值和的界。[通分第 28 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/HDSucc.lean) · [系数第 54 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/TpCoeffNorm.lean)
- [`avgLimit`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/RootNorm.lean#L112) `avgLimit` 用 `rootAvg` 和 `ratioLim` 给出第三节，[`turan2Main`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/Turan2Main.lean#L29) `turan2Main` 合成，[`turan_power_sum_bound`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/TuranPowerSumBound.lean#L12) `turan_power_sum_bound` 给通用常数 $C=1600,A=1$。[取平均第 30、84、112 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/RootNorm.lean) · [合成第 29 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/Turan2Main.lean) · [入口第 12 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/TuranPowerSumBound.lean)

本篇为连续证明及源码对读。无需零点或素数分布假设。本文在 Lean 4.33.1 与既有 Mathlib 环境重放原证明体，通过。选半径、通分、取平均、两条 Turán 入口及其筛项推论共六项的公理列表只含 `propext`、`Classical.choice`、`Quot.sound`，无 `sorryAx` 或项目额外公理。
