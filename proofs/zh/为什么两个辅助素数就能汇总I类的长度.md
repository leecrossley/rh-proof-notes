# 为什么两个辅助素数就能汇总 I 类的长度

I 类允许的系数素数 $\ell$ 没有随 $e$ 变化的大小上界。项目用两个非零整数控制所有这些 $\ell$ 的长度，再按 Dirichlet 特征的核分组。这里证明从整数界到 I 类总和的两道推理。

## 要估计的量和命题

固定本原复 Dirichlet 特征 $\chi$，模 $Q\ge1$。对任意满足[宿主条件](%E6%AD%A3%E5%8F%B7%E4%B8%8A%E5%90%8C%E8%B0%83%E7%9A%84%E4%B8%83%E7%A7%8D%E9%95%BF%E5%BA%A6%E4%BC%B0%E8%AE%A1%E6%80%8E%E6%A0%B7%E9%80%89%E7%94%A8.md)的 $u,q_1,d,t$，记 $N=\operatorname{lcm}(2^{u+2},Q)q_1d$，$H_{\rm host}\subset G_N=(\mathbb Z/N\mathbb Z)^\times$ 为由模 $2^{u+2}$ 的 $\pm1$、模 $Q$ 的 $\ker\chi$ 与模 $q_1,d$ 的平方条件给出的子群。这里宿主还要求 $q_1,d>2t+1,Q,o,p_K,h_K,p_1$，其中 $o=\operatorname{ord}\chi$，$K=\mathbb Q(\sqrt{-p_K})$，$p_K,h_K,p_1,B_\chi$ 如相邻译稿所定义。取 $1\le e<t$。I 类是 $\ell$ 为奇素数、$\ell\notin B_\chi$ 且 $\ell-1\nmid2e$。

对每个系数素数 $\ell$，任取一个有限 $\ell$ 进扩张的整数环 $O_\ell$，令 $r_\ell=v_{O_\ell}(\ell)$。$\mathcal X_\ell$ 是取值在 $O_\ell$ 中、在 $H_{\rm host}$ 上平凡且 $\psi(-1)=(-1)^e$ 的模 $N$ 特征。令 $L_\ell(\psi)$ 为下面的 $O_\ell$-长度。从

$$
H^1\bigl(G_{\mathbb Q},(\operatorname{Frac}O_\ell/O_\ell)(\psi_G^{-1}\varepsilon_\ell^{-e})\bigr)
$$

取在每个有限惯性群上限制为零、且在每个除 $\ell N$ 的素处的分解群上限制为零的子模。这里 $\psi_G$ 是借 $\mu_N$ 上的作用拉回的特征。若 $L_\ell(\psi)$ 有限，置 $V_\ell(\psi)=L_\ell(\psi)/r_\ell$。这两个量分别对应 `Vlen` 与 `Vn`。

在下文的整数输入 `PropGK` 成立时，存在只依赖 $\chi$ 的整数 $C\ge0$ 和素数 $p,p'$，使只要 $q_1,d>p,p'$，对任意有限的 I 类素数集 $\mathcal L$，上述长度都有限，并有

$$
\sum_{\ell\in\mathcal L}\log\ell\sum_{\psi\in\mathcal X_\ell}V_\ell(\psi)
\le(Nt)^C .
\tag{1}
$$

这是源码 `CountI` 的结论，$C,p,p'$ 对 $t,e$、两个宿主素数和系数环的变化一致。

## 整数输入的陈述

对任意数域 $K$，存在非负整数 $c_5,A$。对每个 $e\ge1,N\ge1,J\le G_N$ 及素数 $p\nmid30N|\operatorname{disc}K|$，存在非零整数 $D_p$ 满足

$$
\log|D_p|\le c_5\varphi([G_N:J])\bigl(N(e+1)\bigr)^A\log p .
\tag{2}
$$

这个整数同时控制系数素数 $\ell$。具体说，记 $\operatorname{Orb}_{O_\ell}(J)$ 为 $O_\ell$ 值模 $N$ 特征中核恰为 $J$ 的一族。如果 $\ell\ne p$ 且该族至少有一个 $\psi$ 满足 `GD`，则该族所有长度均有限，且

$$
\sum_{\psi\in\operatorname{Orb}_{O_\ell}(J)}V_\ell(\psi)\le2v_\ell(D_p).
\tag{3}
$$

`GD` 是 I 类验证过的数据：$\ell\ne2$、$e\ge1$、$N$ 偶、$\ell\nmid\operatorname{ord}\psi$、模 $\ell$ 幂分量的平方为 $1$、$\psi(-1)=(-1)^e$、$K$ 虚二次、$\ell\nmid|\operatorname{disc}K|h_K$、$(N,|\operatorname{disc}K|)=1$、$\ell-1\nmid2e$，并且固定 $\mu_\ell$ 与去 $\ell$ 分量特征的共同固定群没有包含于 $G_K$。最后的条件在相邻译稿的式 (2) 中写成绝对 Galois 群上的核。[I 类的虚二次域条件](%E6%AD%A3%E5%8F%B7%E4%B8%8A%E5%90%8C%E8%B0%83%E7%9A%84%E4%B8%83%E7%A7%8D%E9%95%BF%E5%BA%A6%E4%BC%B0%E8%AE%A1%E6%80%8E%E6%A0%B7%E9%80%89%E7%94%A8.md)

## 两个整数补上例外系数素数

固定 $K,e,N,J$，取互异素数 $p,p'$ 均不整除 $30N|\operatorname{disc}K|$，分别得到 $D_p,D_{p'}$。若 $\ell\ne p$，用 $D_p$ 的 (3)。若 $\ell=p$，则 $\ell\ne p'$，可以用 $D_{p'}$。两种情况均有

$$
\sum_{\psi\in\operatorname{Orb}_{O_\ell}(J)}V_\ell(\psi)
\le 2v_\ell(D_p)+2v_\ell(D_{p'}).
$$

因此对任意满足 `GD` 存在性条件的有限素数集求和，乘上 $\log\ell$ 后总和至多 $2(\log|D_p|+\log|D_{p'}|)$。这里用从任意非零整数 $D$ 的素因子分解得到的 $\sum_\ell v_\ell(D)\log\ell=\log|D|$，且每项为非负。结合 (2)，得到固定 $J$ 的界

$$
2c_5\varphi([G_N:J])\bigl(N(e+1)\bigr)^A(\log p+\log p').
\tag{4}
$$

这一步正是 `corGK`。即使 $p$ 自己也在要估计的系数素数集中，第二个整数仍给出其所需的上界。

## 按特征的核计数

现在固定 $K=\mathbb Q(\sqrt{-p_K})$。选 $p,p'$ 为大于 $30Qp_K$ 的两个不同素数。由于 $|\operatorname{disc}K|=p_K$，且 $q_1,d>p,p'$，两个素数都不整除 $30N|\operatorname{disc}K|$。所以它们可以在所有这些宿主上用。

令 $\mathcal J$ 为在某个 $\ell\in\mathcal L$ 的 $\mathcal X_\ell$ 中出现的全部特征的核。对每个 $J\in\mathcal J$，只取那些在 $\mathcal X_\ell$ 中有一个核为 $J$ 的特征的 $\ell$。该特征满足 `GD`，因为我们在 I 类。于是可把这些 $\ell$ 上具有核 $J$ 的 $\mathcal X_\ell$ 特征包入整个 $\operatorname{Orb}_{O_\ell}(J)$，用 (4) 给上界。长度有限性也由这同一次应用得到。

对每个出现的 $J$，商 $G_N/J$ 为循环群。理由是它同构于有限的乘法子群，可嵌入系数环的分式域。循环商阶为 $s=[G_N:J]$ 时，核为 $J$ 的复特征恰有 $\varphi(s)$ 个，因为一个生成元须映到本原 $s$ 次根。不同 $J$ 的这些复特征集合不交。因此

$$
\sum_{J\in\mathcal J}\varphi([G_N:J])\le |\widehat{G_N}|=|G_N|\le N.
$$

把 (4) 对 $J$ 相加，原和至多 $2c_5(\log p+\log p')N(N(e+1))^A$。前面的常数只依赖 $\chi$，取 $b\ge0$ 使其不超过 $16^b$。由于 $16\mid N$ 且 $e+1\le t$，所得界至多 $(Nt)^{b+1+A}$。取 $C=b+1+A$，得 (1)。

## Lean 对照与证明范围

- `PropGK`、`CorGK` 的完整量词和系数素数排除在第 36、44 行。[`corGK`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeGroups/CorGSumLog.lean#L37) `corGK` 第 37 行给出 (4)。[整数和长度接口](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeGroups/KatoUse.lean) · [两个整数](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeGroups/CorGSumLog.lean)
- [`countI`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeGroups/CountI.lean#L22) `UpperTheory.V.U3.countI` 第 22 行由 `CorGK` 推出 (1)。[`orbFacts`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/OrbFacts.lean#L17)、[`orbSum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/OrbSum.lean#L44) 即 `orbFacts`、`orbSum`，给定核的循环商及按核求和的上界。[I 类总和](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeGroups/CountI.lean) · [核与循环商](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/OrbFacts.lean) · [按核计数](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/OrbSum.lean)
- 当前 RH 调用用的是此处的 `UpperTheory.V.U3.countI`。在 `LinkedUnlE.lean` 第 49 行的 `count_i_of_printed_bound_k_kato_automorphy` 中，先用秩三同余数及单特征输入构造 `PropGK`，再依次调用本篇的两个定理。[主线调用](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/LinkedUnlE.lean)

本篇为源码对读。$D_p$ 的构造和它与长度的比较已另文展开。未重新编译或查询传递公理。[构造整数 $D_p$](%E4%B8%BA%E4%BB%80%E4%B9%88Frobenius%E8%BF%B9%E5%B7%AE%E7%9A%84%E4%B9%98%E7%A7%AF%E6%98%AF%E4%B8%80%E4%B8%AA%E9%9D%9E%E9%9B%B6%E6%95%B4%E6%95%B0.md) · [用迹差控制长度](%E6%80%8E%E6%A0%B7%E7%94%A8%E4%B8%80%E4%B8%AAFrobenius%E7%9A%84%E8%BF%B9%E5%B7%AE%E6%8E%A7%E5%88%B6%E5%90%8C%E6%A0%B8%E7%89%B9%E5%BE%81%E7%9A%84%E9%95%BF%E5%BA%A6.md)
