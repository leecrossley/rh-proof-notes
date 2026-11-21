# Bernoulli 值怎样保证消去行列式非零

群环元素可以消去一个上同调类。要从它提取有大小界的整数，关键是证明乘法矩阵的行列式非零。本篇先把行列式分成有限个特征值，再解释每因子为什么非零。

## 命题

给定正整数 $M$，有限阿贝尔群 $\Gamma$ 及群同态 $\phi:(\mathbb Z/M\mathbb Z)^\times\to\Gamma$，要求 $c=\phi(-1)\ne1$。取整数 $a,k\ge2$，且 $(a,M)=1$。设 $\epsilon=(-1)^k$、$h=|\Gamma|/2$，并定义

$$
E_k(b)=\frac{M^{k-1}}{k}B_k([b]_M/M),\qquad
\Theta=-\sum_{b\in(\mathbb Z/M\mathbb Z)^\times}E_k(b)[\phi(b)^{-1}],
\qquad Y=(1-a^k[\phi(a)^{-1}])\Theta\in\mathbb Q[\Gamma].
$$

这里 $B_k(X)$ 是 Bernoulli 多项式，$[b]_M$ 是模 $M$ 的最小非负代表，$[g]$ 是群环的基元。记 $\Delta(Y)$ 为乘以 $Y$ 在 $\mathbb Q[\Gamma]/([c]-\epsilon)$ 上的行列式。令

$$
D=Mk(k+1)!,\qquad U=2a^kM^kk!.
$$

则 $X=D^h\Delta(Y)\in\mathbb Z\setminus\{0\}$，且 $|X|\le (DU)^h$。此结论在负号长度证明里给出 $v_\ell(X)\le\log |X|/\log\ell$，允许 $\ell\mid|\Gamma|$。[消去元与长度的联系](%E4%B8%BA%E4%BB%80%E4%B9%88%E7%BE%A4%E7%8E%AF%E6%B6%88%E5%8E%BB%E7%AE%97%E5%AD%90%E8%83%BD%E7%BB%99%E5%87%BA%E4%B8%80%E4%B8%AA%E7%B4%A0%E6%95%B0%E5%B9%82.md)

## 按复特征分解乘法矩阵

商群环可在每对 $\{g,cg\}$ 的一个代表上取基，因而有秩 $h$。如果 $\chi:\Gamma\to\mathbb C^\times$ 满足 $\chi(c)=\epsilon$，将 $[g]$ 送到 $\chi(g)$ 就给出这个商上的复线性函数 $\operatorname{ev}_\chi$。对任意 $z$ 有

$$
\operatorname{ev}_\chi(Yz)=\operatorname{ev}_\chi(Y)\operatorname{ev}_\chi(z).
$$

恰有 $h$ 个这样的 $\chi$。取 $\epsilon=1$ 时，它们是 $\Gamma/\langle c\rangle$ 的全部特征；一般 $\epsilon$ 时，先选一个有这一符号的特征，再乘上 $\epsilon=1$ 的那些。符号 $-1$ 的特征存在，因为有限阿贝尔群的特征能分离点。这些事实都由有限阿贝尔群分解为循环群得到。在每对选一个代表后，把 $\chi$ 的取值写成行向量。不同的 $\chi,\psi$ 有

$$
\sum_{\{g,cg\}}\chi(g)\overline{\psi(g)}
=\frac12\sum_{g\in\Gamma}\chi(g)\overline{\psi(g)}=0.
$$

这里两个代表给出相同乘积，最后是非平凡特征的求和为零。因此各行非零且正交，正好构成商的对偶基。乘法矩阵在这组坐标中是对角的，于是

$$
\Delta(Y)=\prod_{\chi(c)=\epsilon}\operatorname{ev}_\chi(Y).
\tag{1}
$$

## 特征值的非零性和大小

对给定的 $\chi$，定义模 $M$ 的 Dirichlet 特征 $\psi$，在单位 $b$ 上取 $\chi(\phi(b)^{-1})$，其余取零。用

$$
B_{k,\psi;M}=M^{k-1}\sum_{0\le b<M}\psi(b)B_k(b/M)
$$

表示模 $M$ 层上的广义 Bernoulli 数。逐项求值给出

$$
\operatorname{ev}_\chi(Y)=(1-a^k\psi(a))\,(-B_{k,\psi;M}/k).
\tag{2}
$$

因为 $|\psi(a)|=1$ 且 $a^k>1$，第一因子非零。再看第二因子。令 $\psi^*$ 为诱导 $\psi$ 的本原特征，导子为 $f$。有

$$
B_{k,\psi;M}=
B_{k,\psi^*;f}\prod_{\substack{p\mid M\\p\nmid f}}\bigl(1-\psi^*(p)p^{k-1}\bigr).
\tag{3}
$$

此式可用分布公式和容斥得到。先把 $\psi^*(b)$ 直接延续到模 $M$ 的每个类，按模 $f$ 分组。Bernoulli 多项式满足
$\sum_{j=0}^{m-1}B_k((x+j)/m)=m^{1-k}B_k(x)$，所以所得和乘上 $M^{k-1}$ 后就是 $B_{k,\psi^*;f}$。现在对每个 $p\mid M,\ p\nmid f$ 去掉 $p\mid b$ 的项。如果一组素数的乘积是 $d_0$，令 $b=d_0u$，则限制和经过同样的分组后为 $d_0^{k-1}\psi^*(d_0)B_{k,\psi^*;f}$。容斥给出 (3)。每个 Euler 因子的第二项模长 $p^{k-1}>1$。本原因子非零，因为 $\psi^*(-1)=\psi(-1)=(-1)^k$，Dirichlet 特殊值公式和函数方程把 $|B_{k,\psi^*;f}|$ 写成一个正系数乘 $|L(k,(\psi^*)^{-1})|$，后者在 $k\ge2$ 由绝对收敛的 Euler 乘积非零。这两道解析公式及分布公式已在相邻译稿写明。[Bernoulli 分布和特殊值](%E4%B8%8B%E5%8F%96%E6%95%B4%E7%B3%BB%E6%95%B0%E6%80%8E%E6%A0%B7%E7%BB%99%E5%87%BA%E5%B9%BF%E4%B9%89Bernoulli%E6%95%B0%E7%9A%84%E8%B5%8B%E5%80%BC.md)

为估大小，利用 $k\ge2$ 时 Bernoulli 多项式在 $[0,1]$ 上的 Fourier 级数

$$
B_k(x)=-\frac{k!}{(2\pi i)^k}\sum_{n\ne0}\frac{e^{2\pi i nx}}{n^k}.
$$

对 $n\ne0$，系数由 $B_j'=jB_{j-1}$ 分部积分，$j\ge2$ 时两端值相等，最后由 $B_1(1)-B_1(0)=1$ 算出。常数项由 $B_{k+1}'=(k+1)B_k$ 知为零。级数绝对一致收敛，所得连续周期函数和原多项式有相同 Fourier 系数。用 $\sum_{n\ge1}n^{-k}\le 1+\int_1^\infty x^{-k}\,dx\le2$，得到

$$
|B_k(x)|\le\frac{4k!}{(2\pi)^k}\le k!.
$$

于是 $|B_{k,\psi;M}|\le M^kk!$，而 $|1-a^k\psi(a)|\le 1+a^k\le2a^k$，故 (2) 的模不超过 $U$。

## 清分母并估计整数

写 $B_k(X)=\sum_{j=0}^k\binom kj B_j X^{k-j}$，其中 $B_j=B_j(0)$。偶数 $j\ge2$ 的 Bernoulli 数 $B_j$ 的分母由 von Staudt–Clausen 定理等于所有满足 $p-1\mid j$ 的素数的乘积。$B_0=1$、$B_1=-1/2$，奇数 $j\ge3$ 时 $B_j=0$。所以各分母都整除 $(k+1)!$。从而

$$
DE_k(b)=(k+1)!\sum_{j=0}^k \binom kj B_j M^j[b]_M^{\,k-j}\in\mathbb Z.
$$

群环中的修正因子 $1-a^k[\phi(a)^{-1}]$ 有整数系数，故 $DY$ 有整数系数。它在 $\mathbb Z[\Gamma]/([c]-\epsilon)$ 的自由基上给整矩阵，其行列式是整数。延拓到 $\mathbb Q$ 后，乘法矩阵整体扩大 $D$ 倍，行列式便是 $D^h\Delta(Y)$。按 (1) 和各特征值的非零性、大小界，这个整数非零且模不超过 $(DU)^h$。

## Lean 对照与证明范围

- [`card_signedInvolutionChar_eq_card_involutionQuotient`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/StickelbergerCharacterEval/Chcard.lean#L29) 计数给定符号的特征，[`det_mul_quotientByOrderTwo_eq_prod_charEval`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/StickelbergerCharacterEval/Detprod.lean#L8) 通过特征矩阵证明 (1)。[特征个数，第 29 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/StickelbergerCharacterEval/Chcard.lean) · [行列式分解，第 8 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/StickelbergerCharacterEval/Detprod.lean)
- [`groupRingCharEval_stickelbergerY_eq_euler_mul_genBernoulli`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/StickelbergerCharacterEval/GroupRingCharEvalStickelbergerYNeZeroOfParity.lean#L8)、[`groupRingCharEval_stickelbergerY_ne_zero_of_parity`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/StickelbergerCharacterEval/GroupRingCharEvalStickelbergerYNeZeroOfParity.lean#L14) 证明 (2) 和非零性，[`norm_charEval_higherStickelberger_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/StickelbergerCharacterEval/NormCharEvalHigherStickelbergerLe.lean#L7) 给出 $U$。它们用 [`b_nzC`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/BNzC.lean#L10) `b_nzC`、[`b_upper`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/BUpper.lean#L7) `b_upper` 处理广义 Bernoulli 数。[取值和非零性，第 8、14 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/StickelbergerCharacterEval/GroupRingCharEvalStickelbergerYNeZeroOfParity.lean) · [大小界，第 7 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/StickelbergerCharacterEval/NormCharEvalHigherStickelbergerLe.lean) · [升模，第 7 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/Primlevel.lean)
- [`exists_int_higherStickelbergerDenom_smul`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/StickelbergerCharacterEval/ExistsIntHigherStickelbergerDenomSmul.lean#L25) 清分母，[`higherStickelberger_det_exists_int_bounded`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/StickelbergerCharacterEval/Detint.lean#L9) 合并整数性和大小界。实际分母界通过 [`b_denint`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/Denint.lean#L8) `b_denint` 的素数乘积得到，再用该乘积整除 $(k+1)!$。[清分母，第 25 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/StickelbergerCharacterEval/ExistsIntHigherStickelbergerDenomSmul.lean) · [Bernoulli 分母，第 8 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/Denint.lean) · [主引理，第 9 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/StickelbergerCharacterEval/Detint.lean)

本篇按源码对读。von Staudt–Clausen 定理、Dirichlet 特殊值公式及函数方程作为经典输入。未重跑 Lean 或查询传递公理。
