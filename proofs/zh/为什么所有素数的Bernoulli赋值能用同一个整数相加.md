# 为什么所有素数的 Bernoulli 赋值能用同一个整数相加

每个 $\ell$ 的分量估计都在自己的 $\ell$ 进域里求值。要对许多不同的 $\ell$ 求和，项目把这些取值包在一个共同的非零整数中。

## 命题

给定正整数 $N$、$k\ge1$，令 $G=(\mathbb Z/N\mathbb Z)^\times$。取 $G$ 的一族子群 $\mathcal P$，要求对每个 $J\in\mathcal P$，$-1\in J$ 当且仅当 $k$ 为偶数。设 $A$ 是特征零且含有 $G$ 的指数阶的本原单位根的域。令 $\mathcal X_A$ 为所有取值在 $A$、且其限制到 $G$ 的核属于 $\mathcal P$ 的模 $N$ Dirichlet 特征。记 $\chi^*$ 为诱导 $\chi$ 的本原特征，$f_\chi$ 为其导子，并定义

$$
A_k(\chi)
=N\!\left(\prod_{p\le k+1}p\right) B_{k,\chi^*; f_\chi},
\qquad U=16N^{k+1}k!,
$$

其中 $p$ 遍历素数，且 $B_{k,\psi;f}=f^{k-1}\sum_{b=1}^f\psi(b)B_k(b/f)$。则存在一个整数 $D\ne0$，使对所有这样的 $A$ 都有

$$
D=\prod_{\chi\in\mathcal X_A}A_k(\chi)\ \text{在 }A\text{ 中成立},
\qquad \log|D|\le|\mathcal X_{\mathbb C}|\log U.
\tag{1}
$$

对任意素数 $\ell$，在 $\overline{\mathbb Q}_\ell$ 上用 $|\ell|_\ell=1/\ell$ 的绝对值。则对任何 $T_\ell\subseteq\mathcal X_{\overline{\mathbb Q}_\ell}$，

$$
\sum_{\chi\in T_\ell}-\log|A_k(\chi)|_\ell\le v_\ell(D)\log\ell.
\tag{2}
$$

所以再对任意有限素数集求和，(2) 的右边之和至多 $\log|D|$。

项目取的 $\mathcal P$ 是同时包含固定分圆子域的子群并满足上面奇偶性的那些子群；$\mathcal X$ 就是相应子域的给定符号的特征。由于 $[E:\mathbb Q]$ 界定其个数，(1) 也得到总和只线性依赖于该次数的一项。[负号长度的合并](%E8%B4%9F%E5%8F%B7%E4%B8%8A%E5%90%8C%E8%B0%83%E9%95%BF%E5%BA%A6%E6%80%8E%E6%A0%B7%E7%94%B1%E8%B5%8B%E5%80%BC%E5%92%8C%E6%B6%88%E5%8E%BB%E5%85%83%E6%8E%A7%E5%88%B6.md)

## 为什么乘积是同一个有理数

设 $h$ 为 $G$ 的指数。所有 $\chi$ 的值是 $\mu_h$ 中的元素或 $0$，故先在 $K=\mathbb Q(\mu_h)$ 中算这个乘积。对任意 $K/\mathbb Q$ 的 Galois 元素 $\sigma$，把每个 $\chi$ 的值施加 $\sigma$，得到的特征的核不变，因为 $\sigma$ 是单射且固定 $1$。导子和本原特征的诱导关系也保持，因为这些都由特征在相应约化核上的平凡性决定。于是 $\sigma$ 置换 $\mathcal X_K$，并把每个 $A_k(\chi)$ 送到 $A_k(\sigma\circ\chi)$。这是由于 Bernoulli 多项式有有理系数。因此整个乘积被全部 Galois 元素固定，属于 $\mathbb Q$。

任意 $A$ 含有本原 $h$ 次根，故有 $K\hookrightarrow A$。嵌入把 $\mu_h$ 双射到 $A$ 的 $h$ 次根集合，所有特征和选取条件因而对应。由刚才的有理性，得到的是相同的有理数，与嵌入选择无关。

## 整性、非零性和大小

令 $P_k=\prod_{p\le k+1}p$。由 Bernoulli 数的分母界及多项式展开，

$$
f_\chi P_k\, f_\chi^{k-1} B_k(b/f_\chi)\in\mathbb Z
\qquad(b\in\mathbb Z).
$$

这里 $P_k$ 清掉 $B_0,\ldots,B_k$ 的分母，$f_\chi$ 清掉最高幂项余下的一个分母。因 $f_\chi\mid N$，换成 $NP_k$ 仍可。所有特征值是代数整数，所以每个 $A_k(\chi)$ 是代数整数。有理的乘积也因此是整数。

我们的核条件等价于 $\chi(-1)=(-1)^k$，因为 $\chi(-1)\in\{1,-1\}$。本原特征保持该符号。用特殊值公式和函数方程，$B_{k,\chi^*;f_\chi}\ne0$。对于 $k\ge2$，所需的 $L(k,(\chi^*)^{-1})\ne0$ 来自 Euler 乘积；若 $k=1$，符号为奇，$\chi^*$ 非主，因此用经典的非主狄利克雷 $L$ 函数在 $1$ 点的非零性。于是乘积非零。空乘积 $D=1$ 也满足这些结论。[Bernoulli 特殊值和函数方程](%E4%B8%8B%E5%8F%96%E6%95%B4%E7%B3%BB%E6%95%B0%E6%80%8E%E6%A0%B7%E7%BB%99%E5%87%BA%E5%B9%BF%E4%B9%89Bernoulli%E6%95%B0%E7%9A%84%E8%B5%8B%E5%80%BC.md)

在 $\mathbb C$ 中，由 Bernoulli 多项式的 Fourier 界，

$$
|B_{k,\chi^*;f_\chi}|
\le \frac{4 f_\chi^k k!}{(2\pi)^k}\qquad(k\ge2).
$$

理由是 $|\chi^*(b)|\le1$ 且 $|B_k(x)|\le4k!/(2\pi)^k$ 对 $0\le x\le1$ 成立。$k=1$ 也满足此界，因为 $|B_1(x)|\le1/2\le4/(2\pi)$。此外 $\prod_{p\le m}p\le4^m$。可对 $m$ 归纳：对偶数 $m\ge4$，和 $m-1$ 的乘积相同。若 $m=2j+1$，区间 $j+1<p\le2j+1$ 的每个素数都整除 $\binom{2j+1}{j}$，而这个二项式系数不超过 $2^{2j}$，因为同一行还有一个同样大的系数。乘上 $\prod_{p\le j+1}p\le4^{j+1}$ 即得上界，$m\le2$ 直接成立。由 $f_\chi\le N$ 及 $4\le 2\pi$，

$$
|A_k(\chi)|\le 4^{k+1}N\frac{4N^kk!}{(2\pi)^k}
\le 16N^{k+1}k!.
$$

对所有特征取积再取对数，得到 (1) 的大小界。[Bernoulli 多项式的 Fourier 界](Bernoulli%E5%80%BC%E6%80%8E%E6%A0%B7%E4%BF%9D%E8%AF%81%E6%B6%88%E5%8E%BB%E8%A1%8C%E5%88%97%E5%BC%8F%E9%9D%9E%E9%9B%B6.md)

## 在不同的素数处相加

在 $\overline{\mathbb Q}_\ell$ 中，一个代数整数的 $\ell$ 进绝对值至多 $1$。否则在它的首一整系数方程中，最高次项的模严格大于其余每项，与非阿基米德三角不等式矛盾。于是每个 $-\log|A_k(\chi)|_\ell\ge0$，可以把 $T_\ell$ 扩至全族再求和。由 (1)，全族之和恰为

$$
-\log|D|_\ell=v_\ell(D)\log\ell,
$$

得到 (2)。最后 $\sum_\ell v_\ell(D)\log\ell=\log|D|$ 来自整数的素因子分解。这个论证无须让不同 $\ell$ 的子集 $T_\ell$ 相同。

## Lean 对照与证明范围

- [`b_ratprod`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/Ratprod.lean#L7) `b_ratprod` 第 7 行用分圆值域和 Galois 置换得到共同有理数。[`b_primmem`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/Primmem.lean#L17) `b_primmem` 给整性，[`b_denupper`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/Denupper.lean#L28) `b_denupper` 第 28 行给单个因子的复大小。[`b_prodint`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/Prodint.lean#L12) `b_prodint` 第 12 行合成 (1)。[有理性](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/Ratprod.lean) · [整性](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/Primmem.lean) · [大小](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/Denupper.lean) · [整数乘积](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/Prodint.lean)
- [`prodVal`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/ProdVal.lean#L10) `prodVal` 第 10 行把 (1) 转成 (2) 和对素数的总界。[赋值求和](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/ProdVal.lean)

本篇按源码对读。复特征在 $k=1$ 时用 $L(1,\chi)\ne0$ 的经典输入，项目长度的应用实际取 $k=e+1\ge2$。未重新编译或查询传递公理。
