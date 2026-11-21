# 怎样由非负 Dirichlet 系数得到 Siegel 间隙

**命题（[`siegelLower`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/FinalSiegel.lean#L17)）。** 对每个实数 $\epsilon>0$，存在 $c(\epsilon)>0$，使对任意正整数 $q$ 和模 $q$ 的非主实狄利克雷特征 $\chi$，即 $\chi\ne\chi_0,\ \chi^2=\chi_0$，

$$
|L(1,\chi)|\ge c(\epsilon)q^{-\epsilon}.
 \tag{1}
$$

进而对每个 $\epsilon>0$，存在 $d(\epsilon)>0$，使对任意这样的 $q,\chi$ 及其任一实零点 $\beta$，都有 $1-\beta\ge d(\epsilon)q^{-\epsilon}$。

## 一、四个函数的乘积有非负系数

先取两个非主实特征 $\chi_1,\chi_2$，模数为 $q_1,q_2$。令 $Q=q_1q_2$，在模 $Q$ 的单位上定义 $\psi=\chi_1\chi_2$，在其他整数上补零。假设 $\psi$ 也非主。设

$$
F(s)=\zeta(s)L(s,\chi_1)L(s,\chi_2)L(s,\psi),\qquad
 \lambda=L(1,\chi_1)L(1,\chi_2)L(1,\psi).
$$

展开 $\Re s>1$ 的 Euler 乘积，有 $F(s)=\sum_{n\ge1}a_n n^{-s}$，所有 $a_n\ge0,\ a_1=1$。对 $p\nmid Q$，三特征值为 $a,b,ab$，其中 $a,b\in\{\pm1\}$。写 $X=p^{-s}$，局部因子要么为 $(1-X)^{-4}$，要么为 $(1-X^2)^{-2}$。对 $p\mid Q$，$\psi(p)=0$，两个 $\chi_i$ 至少一个为零，所以局部因子为 $(1-X)^{-1},(1-X)^{-2},(1-X^2)^{-1}$ 三种之一。每种幂级数的系数都非负。

非主 $L$ 函数全纯，$\zeta$ 在 $1$ 处有留数 $1$，故 $G(s)=F(s)-\lambda/(s-1)$ 在 $|s-2|\le3/2$ 全纯。并且在边界有 $|G(s)|\le C Q^K$，其中 $C,K$ 为绝对常数。这个粗界可以直接由周期和得到。对任意非主模 $m$ 特征，其整周期和为零，任意末尾不完整周期的部分和绝对值至多 $m$。在 $\Re s\ge1/2,\ |s|\le4$ 的区域分开 $n\le m$ 的和与 $n>m$ 的尾，用分部求和，得尾项 $O(m|s|\,m^{-\Re s}/\Re s)=O(m)$，前段也为 $O(m)$。因而三个模数 $q_1,q_2,Q$ 的 $L$ 函数乘积为 $O(Q^2)$。$\zeta$ 在这个圆周上有界，且 $|s-1|\ge1/2$。同一个周期估计在 $s=1$ 时将前段控制为 $O(\log(3m))$，尾项为 $O(1)$，所以还得到

$$
|L(1,\chi)|\ll\log(3m)\quad(\chi\ne\chi_0\bmod m).
 \tag{2}
$$

## 二、在靠近 $1$ 的实点截断 Taylor 级数

对 $|z|<1$，写 $F(2-z)=\sum_{j\ge0}b_jz^j$。由于 $n^{z}=e^{z\log n}$，有 $b_j=\sum_n a_n n^{-2}(\log n)^j/j!\ge0$，且 $b_0\ge1$。交换求和由 $|z|<1$ 时的绝对收敛保证。另一方面，极点项 $\lambda/(1-z)$ 的每个系数都等于 $\lambda$。因此 $G(2-z)$ 的系数是 $b_j-\lambda$。

设 $7/8\le\sigma<1$，令 $w=2-\sigma\in(1,9/8]$。Cauchy 估计把 $G(2-z)$ 在 $w$ 处截到第 $N-1$ 次后的尾项控制为 $4C Q^K(3/4)^N$。取 $N=1+\lceil\log(8C Q^K)/\log(4/3)\rceil$，并可先增大 $C$ 至至少 $1$，则尾项至多 $1/2$，且 $N=O(1+\log Q)$。从 $G$ 恢复极点项，得

$$
\begin{aligned}
 F(\sigma)
 &\ge 1-\tfrac12-|\lambda|\sum_{j=0}^{N-1}w^j-\frac{|\lambda|}{w-1}
   =\tfrac12-\frac{|\lambda|w^N}{1-\sigma}.
 \end{aligned}
$$

所有量在此处是实数。由 $w^N\le \exp(N(1-\sigma))$，存在绝对 $C_*,K_*>0$，使得对上述任意两特征及非主乘积特征，

$$
F(\sigma)\ge\tfrac12-C_*\frac{|\lambda| Q^{K_*(1-\sigma)}}{1-\sigma}.
 \tag{3}
$$

这一步只使用靠近 $1$ 的实区间，拉近 $\sigma$ 就能令 $Q$ 的指数变小。

## 三、固定一个参考特征，将 (3) 用于所有模数

令 $\sigma_0=\max(7/8,1-\epsilon/[2(K_*+1)])<1$。若某个非主实 $\chi_1$ 有零点 $\beta\in[\sigma_0,1)$，选定这样一对 $\chi_1,\sigma=\beta$。它们此后固定。于是对任何另一个非主实 $\chi_2$ 且乘积特征非主时，有 $F(\sigma)=0$。若所有非主实特征在 $[\sigma_0,1)$ 都无零点，则固定任意非主实特征 $\chi_1$（例如模 $3$），取 $\sigma=\sigma_0$。这时三个 $L$ 因子在 $\sigma$ 均为正。它们在实轴上取实值，$s>1$ 时由 Euler 乘积为正，从 $s>1$ 连续走到 $\sigma_0$ 都无零点。又 $\zeta(\sigma)<0$。可用交错级数 $\sum_{n\ge1}(-1)^{n-1}n^{-\sigma}=(1-2^{1-\sigma})\zeta(\sigma)$ 看出，左边按相邻两项配对是正数，右边系数为负。故此时 $F(\sigma)<0$。

两种选法都保证 $F(\sigma)\le0$ 且 $K_*(1-\sigma)\le\epsilon/2$。因此由 (3)，再用 $|L(1,\psi)|\ll\log(3Q)\ll_\epsilon Q^{\epsilon/2}$，得到

$$
1\ll_{\epsilon,\chi_1,\sigma} Q^\epsilon |L(1,\chi_2)|.
$$

把固定 $q_1^\epsilon$ 并入常数，即得到 (1) 对所有此类 $\chi_2$ 成立。

若乘积特征为主，则 $\chi_1,\chi_2$ 在模 $Q$ 的单位上相等，因为两者取 $\pm1$。把两者都提升到模 $Q$，得到相同的特征。在 $s=1$，提升只添加 $p\mid Q$ 的 Euler 因子 $1-\chi_i(p)/p$，其绝对值介于 $1-1/p$ 和 $1+1/p$ 之间。将 $Q$ 的不同素因子从小到大列作 $p_j$（$1\le j\le r$），有 $p_j\ge j+1$，故 $\prod(1-1/p_j)\ge1/(r+1)$，且 $\prod(1+1/p_j)\le r+1$。比较两者提升后的 $L(1)$，得

$$
|L(1,\chi_2)|\ge |L(1,\chi_1)|/(r+1)^2.
$$

因为 $2^r\le Q$，所以 $(r+1)^2\ll_\epsilon Q^\epsilon$，同样得到 (1)。此时常数仍可依赖于前面选定的参考特征。第一种选法的常数依赖是否存在及所选的例外零点，证明给出的是每个 $\epsilon$ 的存在性。

## 四、把 $1$ 处的下界传给任意实零点

若 $\beta\le1-1/\log(3q)$，已有 $1-\beta\ge1/\log(3q)\gg_\epsilon q^{-\epsilon}$。若 $\beta$ 在更靠近 $1$ 的区间，源码使用 $|L'(s,\chi)|\ll\log^2(3q)$ 对 $1-1/\log(3q)\le s\le1$ 成立。这也可对级数分部求和看出。$n\le q$ 时 $n^{-s}\le e/n$，所以 $\sum\log n\,n^{-s}\ll\log^2(3q)$。在尾项用 $\sum_{q<n\le t}\chi(n)=O(q)$，将 $t^{-s}\log t$ 微分后积分，得到 $O(q^{1-s}(\log q+1/s))=O(\log(3q))$，因为 $q^{1-s}\le e$ 且这里 $s$ 有正的绝对下界。导数级数在 $\Re s>0$ 局部一致收敛，此法确实估计 $L'$。

因为 $L(\beta,\chi)=0$，沿实段积分后有 $|L(1,\chi)|\ll(1-\beta)\log^2(3q)$。用 (1) 的 $\epsilon/3$，又有 $\log(3q)\ll_\epsilon q^{\epsilon/3}$，所以 $1-\beta\gg_\epsilon q^{-\epsilon}$。在选素数对的相对误差里取 $\epsilon=1$，这一步给出归一化例外因子 $\eta\gg 1/M$。[相对素数定理中的使用位置](%E7%AD%9B%E9%80%89%E6%89%80%E7%94%A8%E7%9A%84%E7%9B%B8%E5%AF%B9%E7%B4%A0%E6%95%B0%E5%AE%9A%E7%90%86%E6%80%8E%E6%A0%B7%E5%90%88%E5%B9%B6%E4%B8%A4%E4%B8%AA%E6%A8%A1%E6%95%B0%E8%8C%83%E5%9B%B4.md)

在另一篇中可接着看这里用到的 $L'$ 上界。它由周期和截断和 Cauchy 估计给出。[导数界的证明](%E5%8F%8C%E6%9B%B2%E7%BA%BF%E5%88%86%E5%89%B2%E6%80%8E%E6%A0%B7%E6%8E%A7%E5%88%B6%E5%B8%A6%E6%AD%A3%E7%B3%BB%E6%95%B0%E7%9A%84%E7%B4%A0%E6%95%B0%E5%B9%82%E5%92%8C.md)

## Lean 对照

- `dirichlet_product_coefficients`、`dirichlet_product_entire`、`product_lfunction_growth_bound` 给第一节。源码的增长证明使用较细的模数幂界，正文使用足够的粗界。[系数第 34 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/ExceptionalZeroBounds/BqCoeff.lean) · [解析第 31 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/ExceptionalZeroBounds/BqEntire.lean) · [增长第 48 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/ExceptionalZeroBounds/BqGrowth.lean)
- `product_lfunction_key_inequality` 给 (3)。`siegel_product_character_inequality` 与 `siegel_theorem_of` 用参考特征完成 (1)，`lfunction_one_same_character` 处理乘积为主的情形。[Taylor 估计第 60 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/ExceptionalZeroBounds/BqKeyOf.lean) · [选参考特征第 9 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/ExceptionalZeroBounds/SiegelOf.lean) · [同源特征第 98 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/ExceptionalZeroBounds/SameCharacterLFunctionOne.lean)
- [`siegelLower`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/FinalSiegel.lean#L17) `siegelLower` 将上游输入合成，`exceptional_zero_bound_of` 给第四节的间隙。[合成第 17 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/FinalSiegel.lean) · [间隙第 26 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/ExceptionalZeroBounds/ExcBoundOf.lean)

本篇为源码对读，使用 $\zeta$ 和非主狄利克雷 $L$ 函数的延拓、非主特征 $L(1,\chi)\ne0$ 及 Cauchy 估计。正文用周期和构造粗增长界，并以有限 Euler 因子对照同源特征。相关声明的内核重放及传递公理状态未查。
