# 怎样把 Wach 余核中的参数幂换成素数幂

## 命题

设 $\ell\ge3$ 为素数，$A$ 是交换的 $\mathbb Z_\ell$-代数，$D$ 为 $A$-模，$N'\subset N\subset D$ 是两个 $A$-子模。设 $X\in A$ 在 $D$ 上作用单射。设 $\gamma_A$ 是 $A$ 的 $\mathbb Z_\ell$-代数自同态，$\gamma:D\to D$ 关于它半线性。假设

$$
(\gamma-1)N\subset XN,\quad
(\gamma-1)N'\subset XN',\quad
\gamma_A(X)\equiv uX\bmod X^2A
$$

其中 $u\in\mathbb Z_\ell^\times$ 模 $\ell$ 的阶为 $\ell-1$，且 $v_\ell(u^{\ell-1}-1)=1$。若 $X^sN\subset N'$，则对 $0\le j\le s$，有

$$
\ell^{d_\ell(j,s)}X^j N\subset N',
\quad
d_\ell(j,s)=\sum_{\substack{j<k\le s\\ \ell-1\mid k}}
            \bigl(1+v_\ell(k)\bigr).
$$

特别地，若 $s=H$，就有 $\ell^{e_W}N\subset N'$，其中

$$
e_W=\left\lfloor H\frac{\ell}{(\ell-1)^2}+3+\log_\ell(H+1)\right\rfloor.
$$

在工程的一处，$N$ 是目标 Wach 模的一个系数分量，$N'$ 是源模在该分量的像，$X$ 在这里是原分圆参数 $\pi$。所以末式说明把目标格里的元素乘以 $\ell^{e_W}$ 后就可以提到源格。

## 证明

先证明一次下降。假定 $cX^{i+1}N\subset N'$，其中 $i\ge0$ 且 $c\in\mathbb Z_\ell$。取 $n\in N$，设 $\gamma(n)=n+Xn_1$，$n_1\in N$。由于 $\gamma_A(X)=X(u+Xt)$，展开可写成

$$
(\gamma-1)(cX^{i+1}n)
=cX^{i+1}\bigl((u^{i+1}-1)n+Xn_2\bigr)
$$

其中 $n_2\in N$。另一方面 $cX^{i+1}n\in N'$，所以左边属于 $XN'$。消掉单射的 $X$，得到

$$
cX^i(u^{i+1}-1)n+cX^{i+1}n_2\in N'.
$$

第二项已在 $N'$，从而 $c(u^{i+1}-1)X^iN\subset N'$。从 $i+1=s$ 一路降到 $j$，便知 $\prod_{j<k\le s}(u^k-1)$ 与 $X^j$ 的乘积把 $N$ 送入 $N'$。

若 $k$ 不是 $\ell-1$ 的倍数，$u^k-1$ 模 $\ell$ 非零。若 $k=(\ell-1)b$，则对 $u^{\ell-1}$ 使用[单位幂差的赋值公式](%E4%B8%BA%E4%BB%80%E4%B9%88%E5%9D%97%E9%97%B4%E5%88%86%E6%AF%8D%E7%9A%84%E8%B5%8B%E5%80%BC%E6%98%AF%E5%88%86%E5%9C%86%E5%B1%82%E6%95%B0%E5%8A%A0%E9%98%B6%E4%B9%98%E8%B5%8B%E5%80%BC.md)，得到

$$
v_\ell(u^k-1)=1+v_\ell(b)=1+v_\ell(k).
$$

所以所取乘积是 $\ell^{d_\ell(j,s)}$ 乘以单位，可以消去单位。令 $q=\ell-1,\ b_0=\lfloor j/q\rfloor,\ b_1=\lfloor s/q\rfloor$，还可把指数写成

$$
d_\ell(j,s)=b_1-b_0+v_\ell(b_1!)-v_\ell(b_0!).
$$

若 $j\le s\le H$，按 $q\ell^i$ 的倍数计数给出

$$
d_\ell(j,s)=\sum_{i\ge0}
\left(\left\lfloor\frac{s}{q\ell^i}\right\rfloor-\left\lfloor\frac{j}{q\ell^i}\right\rfloor\right)
<
\frac{(s-j)\ell}{(\ell-1)^2}+1+\log_\ell(H+1).
$$

精确地说，只在 $q\ell^i\le s$ 时有非零计数。每个计数严格小于 $(s-j)/(q\ell^i)+1$，而可能出现的项数至多 $1+\log_\ell(H+1)$。若一个可能的项也没有，左边为零，同一严格不等式立即成立。以 $s=H,j=0$ 代入，由整数取整即可用 $e_W$ 作上界。

## 上下游

Wach 格满射的第一步由 Hodge 跳点给出 $X^HN\subset N'$。本篇展开从这条参数幂包含到 $\ell$ 幂包含的过程。之后在 $\Delta$ 不变量上取原像时，可以先取任意原像，再以 $|\Delta|^{-1}\sum_{\delta\in\Delta}\delta$ 平均，仍得到同一元素的原像。工程中 $|\Delta|=\ell-1$，因而没有新的 $\ell$-进代价。[分裂素处的晶体提升](%E5%88%86%E8%A3%82%E7%B4%A0%E5%A4%84%E7%9A%84%E6%99%B6%E4%BD%93%E6%8F%90%E5%8D%87%E4%B8%BA%E4%BB%80%E4%B9%88%E8%A6%81%E4%BB%98%E4%B8%A4%E4%BB%BDWach%E6%8C%87%E6%95%B0.md)

## Lean 对照

- `descent_reduces_level` 对正好属于像的 $cX^{i+1}n$ 作两次 $\gamma-1$ 分析。 `mem_span_of_frobenius_mem_span` 迭代下降。[MemSpanOfFrobeniusMemSpan.lean:193](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/LagrangeExtensionCocycles/ExtensionCocycleProofs/MemSpanOfFrobeniusMemSpan.lean#L193) · [同文件:221](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/LagrangeExtensionCocycles/ExtensionCocycleProofs/MemSpanOfFrobeniusMemSpan.lean#L221)
- `cost_formula_holds` 按 $\ell-1$ 的倍数得到阶乘差。`cost_bound` 用二项式系数的赋值上界取得不等式。正文直接数各级倍数以得到同一上界。[TotallyRealRoots.lean:7](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/LagrangeExtensionCocycles/ExtensionCocycleProofs/TotallyRealRoots.lean#L7) · [同文件:43](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/LagrangeExtensionCocycles/ExtensionCocycleProofs/TotallyRealRoots.lean#L43)
- `unit_lemma_case_a_unconditional` 组合赋值与整除，`coreWA_of` 将它接到各系数分量和 Wach 余核的上界。[TotallyRealRoots.lean:121](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/LagrangeExtensionCocycles/ExtensionCocycleProofs/TotallyRealRoots.lean#L121) · [FrobeniusPowUniformizerFactorisation.lean:3486](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/FrobeniusPowUniformizerFactorisation.lean#L3486)

状态为源码级推导。另行未重新编译。
