# Fejér权怎样从幂和找出靠近单位圆的项

**命题。** 固定有限集合 $I$、复数 $z_i$ 和非负整数权 $b_i$（$i\in I$）。设实数 $L\ge1,\ \delta>0,\ 0\le x\le1/2$，并存在 $i_0\in I$ 使 $b_{i_0}\ge1,\ |z_{i_0}|\ge1/(1+x)$。假设 $\sum_i b_i\le L$，且对每个整数 $j\ge1$ 都有

$$
\Re\sum_{i\in I} b_i z_i^j\ \le\ 2j\delta+L\,2^{-j}.
 \tag{1}
$$

则取绝对常数 $C=2080$ 有

$$
x\ \ge\ \frac{\log(1/(CL\delta))}{CL}.
 \tag{2}
$$

对一个带重数的有限序列，只须令 $b_i$ 等于重数。项目用它来比较例外零点距离 $1$ 的差 $\delta$ 和其他零点实部距离 $1$ 的差 $x$。

## 一、让最大的项在一批幂中贡献正量

对整数 $J\ge0$，设 $a_j=1-j/(J+1)$（$1\le j\le J$），令

$$
P_J(w)=\sum_{j=1}^J a_j\Re(w^j).
$$

先证明在 $|w|\le1$ 时 $P_J(w)\ge-1/2$。令 $S_J=\sum_{j=0}^J w^j$。由 $S_{J+1}=1+wS_J$ 得

$$
|S_{J+1}|^2=|w|^2|S_J|^2+2\Re S_{J+1}-1
 \le |S_J|^2+1+2\sum_{j=1}^{J+1}\Re(w^j).
$$

从 $|S_0|^2=1$ 逐步相加，便得

$$
0\le |S_J|^2\le J+1+2\sum_{j=1}^J(J+1-j)\Re(w^j).
$$

除以 $2(J+1)$ 即证。又因 $\sum_{j=1}^J j=J(J+1)/2$，有 $P_J(1)=J/2$。

我们希望增强圆周上一点 $w=e^{i\vartheta}$ 的贡献，同时保留对全圆盘的下界。取新权 $c_j=a_j(1+\cos(j\vartheta))$，于是 $0\le c_j\le2$，且

$$
F(w):=\sum_{j=1}^J c_j\Re(w^j)
  =P_J(w)+\tfrac12 P_J(we^{i\vartheta})+\tfrac12 P_J(we^{-i\vartheta}).
$$

因此在 $|w|\le1$ 时 $F(w)\ge-1$。在 $w=e^{i\vartheta}$ 处，第三个 $P_J$ 的自变量是 $1$，从而 $F(e^{i\vartheta})\ge J/4-3/4$。

## 二、把这个贡献同已知的幂和上界比较

只考虑 $b_i\ge1$ 的项，在其中选 $i_1$ 使 $R=|z_{i_1}|$ 最大。由条件 $R\ge|z_{i_0}|\ge1/(1+x)>0$。设 $w_i=z_i/R$，并取 $\vartheta=\arg z_{i_1}$。每个带正权的 $w_i$ 都在闭单位圆盘，且 $w_{i_1}=e^{i\vartheta}$。所有 $b_i(F(w_i)+1)$ 非负，$i_1$ 的一项至少为 $J/4+1/4$，所以

$$
\sum_i b_i F(w_i)\ge J/4-L.
 \tag{3}
$$

另一方面，将 $F$ 展开并先按 $j$ 求和。因乘子 $c_jR^{-j}\ge0$，可用 (1)。对 $1\le j\le J$，用 $R^{-1}\le1+x\le3/2$ 得

$$
c_jR^{-j}\Re\sum_i b_i z_i^j
 \le 4J\delta(1+x)^J+2L(3/4)^j.
$$

求和并用 $\sum_{j\ge1}(3/4)^j=3$，与 (3) 合得

$$
J/4-7L\le4J^2\delta(1+x)^J.
 \tag{4}
$$

现在选 $J=\lceil64L\rceil$。因 $L\ge1$，有 $64L\le J\le65L$，且 $J/4-7L\ge J/8$。由 (4) 及 $1+x\le e^x$ 可知

$$
1\le32J\delta(1+x)^J\le2080 L\delta\, e^{xJ}.
$$

取对数，得到 $\log(1/(2080L\delta))\le xJ\le2080L x$，这就是 (2)。这里 $\delta L$ 很小时对数才给正下界，正是例外零点排斥需要的范围。

## Lean 对照

- [`normSq_geomSum_le_fejer`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/WeightedFejerPositivity.lean#L6)、[`fejer_re_ge`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/WeightedFejerPositivity.lean#L51)、[`sum_fejer_weights`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/WeightedFejerPositivity.lean#L64)、[`weighted_fejer_split`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/WeightedFejerPositivity.lean#L79)、[`weighted_fejer_positivity`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/WeightedFejerPositivity.lean#L97) 给出几何和平方界、$P_J$ 下界、权和、三项分解及 $F(e^{i\vartheta})$。[`neg_one_le_sum_fejer_cos_re_pow_and_lower_bound`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/WeightedFejerPositivityStatement.lean#L6) `GlobalTheory.T.neg_one_le_sum_fejer_cos_re_pow_and_lower_bound` 是同一组不等式。[第 6、51、64、79、97 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/WeightedFejerPositivity.lean#L6) · [转发第 6 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/WeightedFejerPositivityStatement.lean)
- [`sum_Icc_three_quarters_pow_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SumIccThreeQuartersPowLe.lean#L7)、[`powerSum_weighted_ineq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SumIccThreeQuartersPowLe.lean#L16)、[`powerSum_repulsion`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SumIccThreeQuartersPowLe.lean#L129) `sum_Icc_three_quarters_pow_le`、`powerSum_weighted_ineq`、`powerSum_repulsion` 对应几何级数、(4) 和 (2)。本稿为源码对读。[第 7、16、129 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SumIccThreeQuartersPowLe.lean#L7)
