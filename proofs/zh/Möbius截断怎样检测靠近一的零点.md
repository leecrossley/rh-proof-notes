# Möbius 截断怎样检测靠近一的零点

这条证明链把 $L(\rho,\chi)=0$ 转化成有限多项式在 $\rho$ 处的大值。后续混合大筛计数只需要这个大值条件。证明中有两个尺度，逆函数截断于 $D=Q^3$，卷积截断于 $X=Q^6$。

## 一、两个检测命题

记 $\mu$ 为 Möbius 函数。给定整数 $Q\ge2$，令

$$
b_Q(n)=\sum_{\substack{d\mid n\\d\le Q^3}}\mu(d),\qquad
F_{Q,\chi}(s)=\sum_{Q^3<n\le Q^6} b_Q(n)\chi(n)n^{-s}.
$$

这里 $\chi$ 为狄利克雷特征，$n^{-s}=\exp(-s\log n)$。模 $1$ 的唯一特征恒为 $1$，其 $L$ 函数等于 $\zeta$。

- **[`zero_detect`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SumTruncConv.lean#L108)。** 存在整数 $Q_0$，使对任意整数 $Q\ge Q_0$、$1\le q\le Q$、任意模 $q$ 的非主特征 $\chi$ 和复数 $\rho=\beta+i\gamma$，若 $\beta\ge1-1/400$、$|\gamma|\le Q$ 且 $L(\rho,\chi)=0$，则 $|F_{Q,\chi}(\rho)|\ge1/2$。源码取 $Q_0=1024$。
- **[`zeta_zero_detect`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ZetaZeroDetect.lean#L38)。** 存在整数 $Q_0$，使每个整数 $Q\ge Q_0$ 和复数 $\rho=\beta+i\gamma$ 满足 $1-1/400\le\beta<1$、$Q^{1/20}\le|\gamma|\le Q$ 及 $\zeta(\rho)=0$ 时，都有 $|F_{Q,1}(\rho)|\ge1/2$。

## 二、两个有限恒等式

设 $a_n,f(n)$ 是复系数，$f$ 在正整数上完全乘法，即 $f(dm)=f(d)f(m)$。对非负整数 $D,X$，沿双下标 $d\mid n,\ n\le X,\ d\le D$ 重排有限和，令 $n=dm$，得到

$$
\sum_{1\le n\le X}\left(\sum_{\substack{d\mid n\\d\le D}}a_d\right)f(n)
=\sum_{1\le d\le D}a_d f(d)\sum_{1\le m\le\lfloor X/d\rfloor}f(m).
\tag{1}
$$

取 $a_d=\mu(d)$。若 $1\le n\le D$，所有 $d\mid n$ 自动不超过 $D$。对每个正整数 $n$，$\sum_{d\mid n}\mu(d)=\prod_{p\mid n}(1-1)$，因为有贡献的 $d$ 只需决定是否选每个素因子。故该和在 $n=1$ 时为 $1$，在 $1<n\le D$ 时为零。特别地，以 $D=Q^3,X=Q^6$，取 $f(n)=\chi(n)n^{-s}$，便有

$$
1+F_{Q,\chi}(s)
=\sum_{d\le Q^3}\mu(d)\chi(d)d^{-s}
  \sum_{m\le\lfloor Q^6/d\rfloor}\chi(m)m^{-s}.
\tag{2}
$$

要使右边小，关键是每个内和都截到很远，而且是在 $L$ 函数的零点处计算。

## 三、非主特征内和的误差

**尾项引理（[`norm_LFunction_sub_sum_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LFunctionEqTsumOfOneLt.lean#L226)）。** 设 $\chi\bmod q$ 非主，$\sigma=\Re s>0$，$M\ge1$ 为整数，则

$$
\left|L(s,\chi)-\sum_{1\le n\le M}\chi(n)n^{-s}\right|
\le 2q(1+|s|/\sigma)M^{-\sigma}.
\tag{3}
$$

**证明。** 设 $A(m)=\sum_{1\le n\le m}\chi(n)$。由于 $\chi$ 非主，有单位 $u$ 使 $\chi(u)\ne1$。乘以 $u$ 在模 $q$ 的剩余类上做置换，所以一整周期的和乘以 $\chi(u)$ 后不变，该和必为零。将前 $m$ 项分成完整周期和余下少于 $q$ 项，得 $|A(m)|\le q$。

把 $\chi(n)=A(n)-A(n-1)$ 代入有限和，得到

$$
\sum_{1\le n\le M}\chi(n)n^{-s}
=\sum_{n=1}^M A(n)\bigl(n^{-s}-(n+1)^{-s}\bigr)+A(M)(M+1)^{-s}.
\tag{4}
$$

由 $d(t^{-s})/dt=-s t^{-s-1}$，有

$$
|n^{-s}-(n+1)^{-s}|
\le |s|\int_n^{n+1}t^{-\sigma-1}\,dt
=\frac{|s|}{\sigma}\bigl(n^{-\sigma}-(n+1)^{-\sigma}\bigr).
$$

这个比较在任意紧集 $\Re s\ge\delta>0,\ |s|\le R$ 上还可用 $|s|t^{-\sigma-1}\le R t^{-\delta-1}$ 一致控制。因此 (4) 中带差分的无限级数在 $\Re s>0$ 局部一致收敛，定义全纯函数。边界项趋于零。在 $\Re s>1$ 它等于通常的狄利克雷级数 $L(s,\chi)$，故由恒等定理，在 $\Re s>0$ 等于 $L$ 的解析延拓。

望远镜求和给差分级数从 $n=M+1$ 起的尾项上界 $q(|s|/\sigma)(M+1)^{-\sigma}$。减去 (4) 还多一个边界项，至多 $q(M+1)^{-\sigma}$。所以误差至多 $q(1+|s|/\sigma)(M+1)^{-\sigma}$，已蕴含 (3)。

**应用到零点。** 设 [`zero_detect`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SumTruncConv.lean#L108) 的假设成立且 $Q\ge1024$。因 $\beta>1/2$ 且 $|\rho|\le\beta+Q$，有 $2q(1+|\rho|/\beta)\le8Q^2$。再设 $M_d=\lfloor Q^6/d\rfloor$。对每个 $1\le d\le Q^3$，

$$
Q^6/2\le Q^6-d\le dM_d\le Q^6 .
\tag{5}
$$

因为 $\beta\ge11/12$，故

$$
(dM_d)^\beta\ge(Q^6/2)^{11/12}
=Q^{11/2}/2^{11/12}\ge16 Q^5.
\tag{6}
$$

最后一步由 $Q^{1/2}\ge32$ 得到。将 (3) 用于 $L(\rho,\chi)=0$，就知道 (2) 中每个 $d$ 项的模至多

$$
d^{-\beta}\,8Q^2 M_d^{-\beta}
=8Q^2(dM_d)^{-\beta}\le\frac1{2Q^3}.
$$

这里用到 $|\mu(d)|,|\chi(d)|\le1$。对 $Q^3$ 个 $d$ 求和，得 $|1+F_{Q,\chi}(\rho)|\le1/2$，所以 $|F_{Q,\chi}(\rho)|\ge1/2$。

## 四、有极点的 ζ 情形

**尾项引理（[`norm_zeta_sub_sum_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/NormRiemannZetaSubPartialSumLe.lean#L103)）。** 对 $\sigma=\Re s>0$、$s\ne1$ 和整数 $M\ge1$，

$$
\left|\zeta(s)-\sum_{n=1}^{M}n^{-s}-\frac{M^{1-s}}{s-1}\right|
\le\frac{|s|}{\sigma}M^{-\sigma}.
\tag{7}
$$

**证明。** 先令 $\Re s>1$，写 $n^{-s}=s\int_n^\infty t^{-s-1}\,dt$。绝对收敛允许将 $n>M$ 的求和换入积分。数出满足 $M<n\le t$ 的整数得

$$
\begin{aligned}
\zeta(s)-\sum_{n=1}^M n^{-s}
&=s\int_M^\infty (\lfloor t\rfloor-M)t^{-s-1}\,dt\\
&=\frac{M^{1-s}}{s-1}-s\int_M^\infty \{t\}\,t^{-s-1}\,dt ,
\end{aligned}
\tag{8}
$$

其中 $\{t\}=t-\lfloor t\rfloor$。最后等号将 $\lfloor t\rfloor-M$ 写为 $t-M-\{t\}$ 并积分。由 $0\le\{t\}<1$，右端的小数部分积分在 $\Re s>0$ 收敛。它在该半平面全纯，因为在 $\Re s\ge\delta>0$ 的紧集上，被积函数及其 $s$ 导数分别由 $t^{-1-\delta}$ 和 $(\log t)t^{-1-\delta}$ 控制。用恒等定理将 (8) 延拓到 $\Re s>0,\ s\ne1$，再用 $\int_M^\infty t^{-\sigma-1}dt=M^{-\sigma}/\sigma$ 得 (7)。

源码先在 $M=1$ 建立 (8) 的延拓，然后逐个单位区间积分到一般 $M$。上述直接截在 $M$ 的论证给出同一恒等式和同一个误差常数。

**应用到零点。** 在 [`zeta_zero_detect`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ZetaZeroDetect.lean#L38) 的假设下，将 (7) 用到 $s=\rho$，并用 $|\rho|/\beta\le4Q$、$|\rho-1|\ge|\gamma|\ge Q^{1/20}$，得到

$$
\left|\sum_{m\le M_d}m^{-\rho}\right|
\le4Q M_d^{-\beta}+\frac{M_d^{1-\beta}}{Q^{1/20}}.
$$

将它代入 (2) 的模 $1$ 情形。第一项乘以 $d^{-\beta}$ 后，由 (6) 至多为 $4Q/(16Q^5)\le1/(4Q^3)$，故总和至多 $1/4$。第二项乘以 $d^{-\beta}$ 后等于 $d^{-1}(dM_d)^{1-\beta}/Q^{1/20}$。因为 $0<1-\beta\le1/400$ 且 $dM_d\le Q^6$，求和后至多为

$$
\bigl(1+\log(Q^3)\bigr)Q^{6/400-1/20}
=(1+3\log Q)\,Q^{-7/200}.
\tag{9}
$$

这里使用 $\sum_{1\le d\le D}1/d\le1+\log D$。式 (9) 随 $Q\to\infty$ 趋于零，故可取统一的 $Q_0\ge1024$，使它至多 $1/4$。Lean 的 `pole_small` 用 $\log Q\le100Q^{1/100}$ 将 (9) 压到 $301Q^{-1/40}$，给出同一存在阈值。于是 $|1+F_{Q,1}(\rho)|\le1/2$，证得所需的大值界。

## 源码对照

- (1)、常数项的消去、(6)、非主特征检测分别为 [`sum_trunc_conv`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SumTruncConv.lean#L9)、[`sum_initial`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SumTruncConv.lean#L55)、[`rpow_bound`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SumTruncConv.lean#L74)、[`zero_detect`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SumTruncConv.lean#L108)。[第 9、55、74、108 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SumTruncConv.lean#L9)
- (4) 对应 [`abel`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LFunctionEqTsumOfOneLt.lean#L127) `abel`。全纯性与相等由 [`LFunction_eq_tsum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LFunctionEqTsumOfOneLt.lean#L194) `LFunction_eq_tsum` 处理，(3) 是 [`norm_LFunction_sub_sum_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LFunctionEqTsumOfOneLt.lean#L226)。[第 127、194、226 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LFunctionEqTsumOfOneLt.lean#L127)
- (8)、(7) 分别是 [`zeta_eq_sum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/NormRiemannZetaSubPartialSumLe.lean#L78)、[`norm_zeta_sub_sum_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/NormRiemannZetaSubPartialSumLe.lean#L103)，建立在小数部分积分的延拓上。ζ 检测与极点项估计是 [`zeta_zero_detect`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ZetaZeroDetect.lean#L38)、[`pole_small`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ZetaZeroDetect.lean#L8)。[尾项第 78、103 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/NormRiemannZetaSubPartialSumLe.lean) · [检测第 8、38 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ZetaZeroDetect.lean)
- 下游把这个有限和的大值条件送入[混合大筛的检测点计数](%E6%B7%B7%E5%90%88%E5%A4%A7%E7%AD%9B%E6%80%8E%E6%A0%B7%E6%95%B0%E5%87%BA%E5%88%86%E7%A6%BB%E7%9A%84%E6%A3%80%E6%B5%8B%E7%82%B9.md)。
