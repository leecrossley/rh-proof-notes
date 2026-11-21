# 缺类大筛怎样给出 Brun–Titchmarsh 界

记 $e(u)=\exp(2\pi i u)$，$\varphi(d)$ 为 Euler 函数，即模 $d$ 可逆类的数目。取 $\varphi(1)=1$。正整数称为平方自由的，如果它的每个素因子的指数都是 $1$。这一篇补齐固定模数素数二阶矩所需的计数引理。前置的 [单个素数的缺类下界](%E7%BC%BA%E4%B8%80%E4%B8%AA%E5%89%A9%E4%BD%99%E7%B1%BB%E8%87%B3%E5%B0%91%E9%9C%80%E8%A6%81%E5%A4%9A%E5%B0%91%E9%A2%91%E7%8E%87%E8%83%BD%E9%87%8F.md) 和 [加法大筛](%E6%8C%89%E5%AE%9E%E9%99%85%E9%A2%91%E7%8E%87%E9%97%B4%E8%B7%9D%E8%AE%A1%E8%B4%B9%E7%9A%84%E5%8A%A0%E6%B3%95%E5%A4%A7%E7%AD%9B.md) 各有完整证明。

## 一、把各素因子的缺类条件合起来

设 $d\ge1$ 平方自由，$S\subseteq\mathbb N$ 有限，$b_m\in\mathbb C$。对每个素数 $\ell\mid d$，假设存在一个模 $\ell$ 剩余类不含 $S$ 的任何元素。则

$$
\left|\sum_{m\in S} b_m\right|^2
\le\varphi(d)\sum_{\substack{0\le a<d\\\gcd(a,d)=1}}
\left|\sum_{m\in S} b_m e(ma/d)\right|^2.
\tag{1}
$$

对 $d$ 的素因子数作归纳。$d=1$ 时右边只有 $a=0$，等式成立。设 $d=d'\ell$，其中 $\ell$ 为素数，$(d',\ell)=1$。先对 $d'$ 用归纳假设，再对右边每个 $a'$ 把单个素数的缺类下界用到系数 $b_m e(ma'/d')$。支撑集仍是 $S$，所以缺类假设照样成立。得到

$$
\left|\sum_{m\in S} b_m\right|^2
\le\varphi(d')(\ell-1)
\sum_{\substack{0\le a'<d'\\\gcd(a',d')=1}}\ \sum_{a''=1}^{\ell-1}
\left|\sum_{m\in S}b_m e\left(m(a'/d'+a''/\ell)\right)\right|^2.
$$

将 $\ell a'+d'a''$ 化为模 $d$ 的标准代表元 $a$。因为 $\ell$ 在模 $d'$ 下可逆，$d'$ 在模 $\ell$ 下可逆，所以给定 $a$ 可以分别求回唯一的一对 $(a',a'')$。而 $a$ 可逆恰好要求两边的剩余类分别可逆。该对应也给出 $\varphi(d)=\varphi(d')(\ell-1)$，归纳完成。

## 二、由缺类条件限制集合的大小

设 $M,L$ 为非负整数，$Q,q\ge1$ 为整数，$S\subseteq\{M+1,\ldots,M+L\}$。若每个不整除 $q$ 且不超过 $Q$ 的素数，都有一个剩余类不含 $S$ 的元素，则

$$
|S|\,\frac{\varphi(q)}q\log Q\le Q^2+2\pi L.
\tag{2}
$$

记 $D=\{1\le d\le Q:d\text{ 平方自由},\ (d,q)=1\}$，并令 $F(t)=\sum_{m\in S}e(mt)$。对每个 $d\in D$，其素因子都满足 (1) 所需条件。取 $b_m=1$，得 $|S|^2/\varphi(d)\le\sum_{(a,d)=1,\,0\le a<d}|F(a/d)|^2$。这些约分后的分数互不相同，且都在 $[0,1)$。两个不同分数 $a/d,b/f$ 的差减去任意整数仍非零，乘以 $df$ 后为非零整数，故模 $1$ 间距至少 $1/(df)\ge1/Q^2$。对系数 $\mathbf 1_{m\in S}$ 用加法大筛，得到

$$
|S|^2\sum_{d\in D}\frac1{\varphi(d)}\le(Q^2+2\pi L)|S|.
\tag{3}
$$

为估计左边的和，对每个 $1\le u\le Q$ 取出所有整除 $u$ 而不整除 $q$ 的素数，各乘一次，记其乘积为 $d$。有 $d\in D$，且 $u$ 可唯一写成

$$
u=\prod_{\ell\mid d}\ell^{a_\ell}\prod_{\ell\mid q}\ell^{b_\ell},
\qquad a_\ell\ge1,\quad b_\ell\ge0,
$$

这里的两个乘积均只遍历素数。把同一 $d$ 对应的 $1/u$ 相加，放宽 $u\le Q$，就可把每个指数各自求成几何级数。所得上界为

$$
\prod_{\ell\mid d}\frac1{\ell-1}\prod_{\ell\mid q}\frac1{1-1/\ell}
=\frac1{\varphi(d)}\frac q{\varphi(q)}.
$$

最后一个等号可由模素数幂的可逆类计数 $\varphi(\ell^b)=\ell^b-\ell^{b-1}$ 和互素模数的中国剩余定理得到。对 $d$ 求和，并用 $\sum_{1\le u\le Q}1/u\ge\int_1^Q dt/t=\log Q$，得 $\sum_{d\in D}1/\varphi(d)\ge(\varphi(q)/q)\log Q$。将它代入 (3)，约去 $|S|$ 就得到 (2)。若 $S$ 为空，(2) 直接成立。

## 三、应用于一个等差数列中的素数

**Brun–Titchmarsh 界。** 设 $q\ge1$、$a\ge0$ 为整数且 $(a,q)=1$，实数 $x\ge0$、$y\ge2q$。则

$$
\#\{p\text{ 为素数}:x<p\le x+y,\ p\equiv a\pmod q\}
\le\frac{48y}{\varphi(q)\log(y/q)}.
\tag{4}
$$

**证明。** 写 $z=y/q\ge2$，令 $s=\lfloor\sqrt{\lfloor z\rfloor}\rfloor$、$Q=s+1$、$M=\lfloor x/q\rfloor$、$L=\lfloor z\rfloor+2$。由于 $s^2\le\lfloor z\rfloor<Q^2$ 且 $s\ge1$，有 $z<Q^2\le4z$ 和 $L\le2z$。记 $B$ 为待数素数中满足 $p>Q$ 的个数。

令 $r=a\bmod q$。每个这样的 $p$ 可唯一写为 $p=qj+r$，其中 $j=\lfloor p/q\rfloor$。由 $x<p\le x+y$ 得 $M\le j<M+L$，因为 $p/q\le x/q+z<M+1+z<M+L$。把 $m=j+1$ 放入集合 $S$，得到 $|S|=B$ 且 $M<m\le M+L$。若 $\ell\le Q$ 是不整除 $q$ 的素数，则同余式 $q(m-1)+r\equiv0\pmod\ell$ 有唯一的解类。该类中的 $m$ 会使 $\ell\mid p$，与 $p$ 是大于 $Q$ 的素数矛盾。于是 $S$ 满足 (2) 的缺类条件。

由 (2)、$Q^2\le4z$、$L\le2z$ 及 $\pi<4$，得

$$
B\frac{\varphi(q)}q\log Q\le Q^2+2\pi L\le20z.
$$

由于 $\log z\le2\log Q$，所以 $B\varphi(q)\log z\le40y$。另有至多 $Q$ 个不超过 $Q$ 的素数可计入，而

$$
Q\varphi(q)\log z\le2q Q\log Q\le2q Q^2\le8y.
$$

这里用了 $\varphi(q)\le q$ 和 $\log Q\le Q$。两部分相加，再除以正数 $\varphi(q)\log z$，得到 (4)。

## 源码对照

- 推广到平方自由模数对应 `norm_sum_sq_le_totient_mul_of_avoids_classes`，其分数配对由 `sum_coprime_range_mul_eq_sum_sum` 与 `cexp_crt_combination_eq_mul` 实现。几何级数估计对应 `sum_inv_le_mul_sum_squarefree_inv_totient`，正文直接对各素因子的指数求和。式 (2) 对应 `GlobalTheory.arithmetic_large_sieve_one_class`。[源码第 78、162、217、378、427 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ArithmeticLargeSieveOneResidueClassPerPrime.lean#L78)
- (3) 的约分分数间距与唯一性分别由 `GlobalTheory.MultSieve.farey_spaced`、`reduced_inj` 提供。此处使用该模块里的两个有理数引理。[源码第 98、131 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MultiplicativeLargeSieve.lean#L98)
- (4) 对应 `GlobalTheory.Lin.brun_titchmarsh_const`，引用 `card_large_primes_class_le` 处理大于 $Q$ 的素数，再单独计小素数。Lean 源码取的常数也是 $48$。[源码第 18、48 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/BrunTitchmarshExistsConst.lean#L18)
- 固定模数的素数二阶矩通过同陈述转发定理 `GlobalTheory.T.brunTitchmarsh_exists_const` 使用 (4)。[转发源码](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/BrunTitchmarshExistsConstStatement.lean) · [该二阶矩的证明](%E5%9B%BA%E5%AE%9A%E6%A8%A1%E6%95%B0%E7%9A%84%E7%B4%A0%E6%95%B0%E5%A4%9A%E9%A1%B9%E5%BC%8F%E4%BA%8C%E9%98%B6%E7%9F%A9.md)
