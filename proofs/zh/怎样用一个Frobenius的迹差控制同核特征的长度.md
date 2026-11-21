# 怎样用一个 Frobenius 的迹差控制同核特征的长度

I 类最后要用一个整数同时控制许多 $\ell$ 的上同调。这里证明中间的连接：在同一个素处比较 Galois 表示的迹与一个指定的可约迹，就能把每个长度项交给复迹列表所造出的整数。

## 命题和两个输入

设 $K$ 是虚二次数域，$N,e\ge1$，$J\le(\mathbb Z/N\mathbb Z)^\times$，$p$ 是素数且 $p\nmid30N|\operatorname{disc}K|$。取 $K$ 的一个 $p$ 上方的素处 $w$，令 $q=\mathrm Nw$。记 $\mathcal A_{\ell,\iota}$ 为主线允许的秩三 $\ell$ 进 Galois 表示类，参数为 $K,N,e$ 和域同构 $\iota:\overline{\mathbb Q}_\ell\simeq\mathbb C$。源码中同一个允许类在两项输入里都写为 `Adm3U_s` 或 `Adm2A`。前一项是不可约秩三表示，带 $N$ 的惯性界、$(e,0,-e)$ 的旗标条件和分圆扭曲后的自守性及局部见证。后一项是与 $1\oplus W|_{G_K}$ 同构的表示，其中 $W$ 是有秩二新形式和虚二次限制见证的不可约表示，带级 $N|\operatorname{disc}K|$、权 $(e,-e)$ 和行列式条件。下面的推理适用于任意给定的允许类，只用到它在两个输入中一致。[允许类及局部见证](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/NumberU3US.lean) · [秩二类的定义，第 14 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/AutomorphyLifting/AutomorphyDescent/AutNewformW.lean)

对 $O_\ell$ 值模 $N$ 特征 $\psi$，用 $L_\ell(\psi)$ 表示以 $\psi_G^{-1}\varepsilon_\ell^{-e}$ 扭曲的 $\operatorname{Frac}O_\ell/O_\ell$ 的局部限制核的长度。局部条件为所有有限惯性和 $\ell N$ 上方分解群。若长度有限，记 $V_\ell(\psi)=L_\ell(\psi)/v_{O_\ell}(\ell)$。取绝对值 $|\ell|_\ell=1/\ell$，写 $v_\ell(y)=-\log|y|_\ell/\log\ell$ 对 $y\ne0$。

**单特征输入。** 给定任意奇素数 $\ell$、系数整数环 $O_\ell$、特征 $\psi$ 满足 `GD`，以及 $\iota$ 和 $g\in G_K$。令 $b_\psi(g)=\varepsilon_\ell(g)^e\psi_G(g)$，$\tau_\psi(g)=b_\psi(g)+1+b_\psi(g)^{-1}$。如果 $\tau_\psi(g)$ 不等于任何 $\rho\in\mathcal A_{\ell,\iota}$ 的 $\operatorname{tr}\rho(g)$，则 $L_\ell(\psi)$ 有限，并存在一个由两两不同构的允许表示组成的有限集 $X_\psi$，满足

$$
V_\ell(\psi)\le 2\sum_{\rho\in X_\psi}
v_\ell\bigl(\operatorname{tr}\rho(g)-\tau_\psi(g)\bigr).
\tag{1}
$$

这是 `OneCharU_s` 的完整长度与迹比较。`GD` 的全部条件见[宿主的 I 类](%E6%AD%A3%E5%8F%B7%E4%B8%8A%E5%90%8C%E8%B0%83%E7%9A%84%E4%B8%83%E7%A7%8D%E9%95%BF%E5%BA%A6%E4%BC%B0%E8%AE%A1%E6%80%8E%E6%A0%B7%E9%80%89%E7%94%A8.md)，其中只取 $\ell$ 互素部分再去掉模 $\ell$ 幂分量所得到的特征参与固定群条件。

**整数输入。** `NumberU3U_s` 对任意 $K,N,e,p,w$ 如上，以及有限指标集 $A$ 上一个在 Galois 作用下可用置换实现的单位根族 $z_a$，给出 $D_p\in\mathbb Z\setminus\{0\}$ 和只依赖 $K$ 的 $c_5,A_0\ge0$，使

$$
\log|D_p|\le c_5|A|\,[N(e+1)]^{A_0}\log p .
\tag{2}
$$

对任意奇素数 $\ell\ne p$、域同构 $\iota$、$w$ 上方绝对素处的算术 Frobenius $\Phi$，取 $g=\Phi^{-1}$。对每个 $a$，任取两两不同构的有限集 $X_a\subset\mathcal A_{\ell,\iota}$，则 $\operatorname{tr}\rho(g)\ne\iota^{-1}(q^{-e}z_a+1+q^ez_a^{-1})$ 对各 $\rho\in X_a$ 成立，而且

$$
|D_p|_\ell\le
\prod_{a\in A}\prod_{\rho\in X_a}
\big|\operatorname{tr}\rho(g)-\iota^{-1}(q^{-e}z_a+1+q^ez_a^{-1})\big|_\ell.
\tag{3}
$$

这个输入由前一篇的迹列表乘积给出。[迹差整数的构造](%E4%B8%BA%E4%BB%80%E4%B9%88Frobenius%E8%BF%B9%E5%B7%AE%E7%9A%84%E4%B9%98%E7%A7%AF%E6%98%AF%E4%B8%80%E4%B8%AA%E9%9D%9E%E9%9B%B6%E6%95%B4%E6%95%B0.md)

这两项推出 `PropGK`。也就是可把 (2) 的 $|A|$ 换成 $\varphi([G_N:J])$，并且对所有奇 $\ell\ne p$，只要存在一个核为 $J$ 的 $O_\ell$ 值特征满足 `GD`，便有所有同核特征的长度有限，且

$$
\sum_{\ker\psi=J} V_\ell(\psi)\le 2v_\ell(D_p).
\tag{4}
$$

`PropGK` 对一般数域 $K$ 也作全称量化。若 $K$ 不是虚二次域，`GD` 的存在性条件无法满足，可取 $D_p=1$，所要求的长度蕴含自动成立。

## 同核特征可以在两种系数域中对应

取 $A$ 为所有核为 $J$ 的复 Dirichlet 特征 $\chi$，令 $z_\chi=\chi(q)^{-1}$。因为 $p\nmid N$，$q=p^f$ 与 $N$ 互素，故 $z_\chi$ 是单位根。任何复域自同构逐值作用于 $\chi$ 时保留核，因而置换这些下标并对应地变换 $z_\chi$，这验证了整数输入。若有同核特征，$G_N/J$ 通过其取值嵌入有限循环群，因而是循环群。其忠实特征恰有 $\varphi([G_N:J])$ 个；若无，则 $A$ 为空。得到 (2) 所需的指标数。

固定某个 $\ell$ 和一个满足 `GD` 的同核特征 $\psi_0$。其像是 $G_N/J$ 阶数的整个单位根群，且已在 $O_\ell$ 中。因此把系数嵌入 $\overline{\mathbb Q}_\ell$ 再用 $\iota$，能在 $O_\ell$ 值与复值的同核特征之间建立双射。更具体地，每个同核特征都是 $\psi_0$ 的一个幂，指数与 $[G_N:J]$ 互素。这些幂也保留 `GD`。其阶相同，在模 $\ell$ 幂分量上的阶至多二仍成立，$-1$ 处的符号不变。去掉模 $\ell$ 幂分量后的特征也只是取同一个幂，核不变，所以涉及共同固定群的条件不变。

## 迹比较用的是逆算术 Frobenius

对 $w$ 上方的绝对素处取算术 Frobenius $\Phi$。它在 $\mu_N$ 和全部 $\ell$ 幂阶单位根上都取 $q$ 次幂，因为 $p\nmid N\ell$，这些单位根的约化保持阶数，而剩余域作用是 $x\mapsto x^q$。于是

$$
b_\psi(\Phi)=q^e\psi(q),\qquad
\tau_\psi(\Phi^{-1})=q^{-e}\psi(q)^{-1}+1+q^e\psi(q).
$$

在双射下若 $\chi=\iota\circ\psi$，则 $\tau_\psi(\Phi^{-1})=\iota^{-1}(q^{-e}z_\chi+1+q^ez_\chi^{-1})$。对 (3) 使用只含任一个允许表示的单元素子集，先得到这个迹差对所有允许表示非零。这样便可逐个 $\psi$ 使用单特征输入 (1)，得到有限的 $X_\psi$。

最后把这些 $X_\psi$ 当作同一组 $X_\chi$ 送进 (3)。对正实数两边取 $-\log(\cdot)/\log\ell$，不等号反向，得到双重迹差赋值的总和至多 $v_\ell(D_p)$。由 (1) 得到 (4)。非零整数先由复迹族一次选定，$\ell$ 进系数、上同调和其后选出的表示只用于比较。这正解释了为什么 I 类能对许多不同的 $\ell$ 汇总。

## Lean 对照与证明范围

- `OneCharU_s`、`NumberU3U_s` 的陈述在第 49、30 行。[`propGK_of_numberU3U_of_oneCharU`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/FPropGKU.lean#L110) `propGK_of_numberU3U_of_oneCharU` 第 110 行证明上述组合。[两项输入](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/NumberU3US.lean) · [合成证明](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/FPropGKU.lean)
- 主证明的 `frob_val`、`t_eq` 对应两种特征的 Frobenius 求值，`vl_bound` 对应将 (3) 取赋值。[`orbFacts`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/OrbFacts.lean#L17) `orbFacts` 提供同核特征的计数，`gdFacts` 保留同核的局部数据。[同核特征](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/OrbFacts.lean) · [同核的局部条件](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/GdFacts.lean)

本篇为源码对读。单特征输入 (1) 的变形环比较已另文展开，其中注明用到的自守性与刚性。未重新编译或查询传递公理。[单特征不等式](%E4%B8%80%E4%B8%AA%E7%89%B9%E5%BE%81%E7%9A%84%E9%95%BF%E5%BA%A6%E6%80%8E%E6%A0%B7%E7%94%B1%E6%9C%89%E9%99%90%E4%B8%AA%E8%87%AA%E5%AE%88%E8%BF%B9%E5%B7%AE%E6%8E%A7%E5%88%B6.md)
