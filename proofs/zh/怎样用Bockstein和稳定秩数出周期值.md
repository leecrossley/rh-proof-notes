# 怎样用 Bockstein 和稳定秩数出周期值

## 命题

设 $L$ 是全虚数域，$r_2(L)$ 是复处数，$j\ge0$ 为偶数且 $j+1<r_2(L)$。取素数 $\ell$、整数 $\nu\ge0$，令 $q=\ell^\nu$，$B$ 为 $\mathbb Z/q\mathbb Z$-模。记 $G_n=\mathrm{GL}_n(O_L)$。设对每个 $n$ 有 $\mathbb Z/q\mathbb Z$-线性泛函

$$
\Phi_n:C_{j+1}(G_n,\mathbb Z/q\mathbb Z)\to B.
$$

这里 $C_\bullet$ 是群的 bar 链复形，系数的群作用平凡。要求 $\Phi_n$ 杀掉边界。对一个周期 $y$，嵌入左上角、在其余对角线上添单位阵，不改变取值。把整个矩阵块重复 $m\ge1$ 次的群同态在链上送 $y$ 到 $\psi_m y$，取值变成 $m\Phi_n(y)$。取任意由形如 $\ell^j\Phi_n(y)$ 的值组成的有限集合 $S$，其中 $y$ 可来自任意 $n$。令 $n_0=2(j+1)+4$，$T_i=|\operatorname{Tor} H_i(G_{n_0},\mathbb Z)|$。则

$$
|S|\ \le\ q^{r_2(L)}T_{j+1}T_j .
$$

这就是 `SUpper`。在[加权范数的计数证明](%E6%80%8E%E6%A0%B7%E6%8A%8A%E5%8A%A0%E6%9D%83%E8%8C%83%E6%95%B0%E7%9A%84%E5%B9%82%E7%B1%BB%E9%80%81%E8%BF%9B%E7%9F%A9%E9%98%B5%E7%BE%A4%E5%90%8C%E8%B0%83.md)中，每个范数幂类由此类周期值唯一确定。本篇解释底数 $q$ 的幂为什么只由复处数控制，两个扭结因子又分别从哪里来。

## 证明

先把 $S$ 每个元素的一份周期代表移到共同的矩阵大小 $n\ge n_0$。因为 $S$ 有限，只需取原大小的最大值与 $n_0$ 的较大者。左上角稳定化保留值。项目使用的稳定性在这里给出一个具体陈述：对 $i=j,j+1$，当 $N\ge n_0$ 时 $H_i(G_N,\mathbb Z)$ 的扭结子群有限，其阶等于 $T_i$。

取一个模 $q$ 周期 $y$，提升为整数链 $x$。整数 bar 链群自由，模 $q$ 的链群正是系数逐项模 $q$，故 $\partial x=qw$，且由 $q\partial w=0$ 得 $\partial w=0$。所得映射

$$
\beta:Z_{j+1}(G_n,\mathbb Z/q\mathbb Z)\to H_j(G_n,\mathbb Z)[q],\qquad y\mapsto[w]
$$

是加法同态。另一份提升与 $x$ 相差 $qz$，所以 $w$ 只改变一个边界 $\partial z$。若 $\beta(y)=0$，选 $z$ 使 $\partial z=w$，则 $x-qz$ 是一份整数周期提升。反过来，有整数周期提升时 $\beta(y)=0$。这个步骤给出 $T_j$ 个可能的纤维。固定一个纤维中的代表，纤维中其余各值与它的差，都是在 $\ker\beta$ 上取到的值。故只需证明在整数周期约化上至多能取到 $q^{r_2(L)}T_{j+1}$ 个不同的 $\ell^j\Phi_n$ 值。

杀边界的假设使 $\Phi_N$ 在整数周期的模 $q$ 约化上诱导同态 $\phi_N:H_{j+1}(G_N,\mathbb Z)\to B$。写 $n_i=\ell^i n$。对 $x\in H_{j+1}(G_n,\mathbb Z)$，令 $z_0(x)=x$，并在相应的整数同调中递推

$$
z_{i+1}(x)=\psi_\ell z_i(x)-\ell^{i+2}\iota z_i(x),
\qquad
\iota:G_{n_i}\hookrightarrow G_{n_{i+1}}.
$$

$\psi_\ell$ 是重复 $\ell$ 个块，$\iota$ 是补单位阵。两项的取值分别乘 $\ell$ 和保持原值，所以

$$
\phi_{n_j}(z_j(x))
=\ell^j u\,\phi_n(x),\qquad u=\prod_{i=0}^{j-1}(1-\ell^{i+1}).
$$

空乘积取 $1$。每一因子模 $\ell$ 等于 $1$，因而 $u$ 在 $\mathbb Z/q\mathbb Z$ 可逆，乘其逆元可恢复 $\ell^j\phi_n(x)$。

现在用项目的稳定秩命题 `BOdd`。在上述 $L,j,n,\ell$ 的条件下，所有 $z_j(x)$ 张成的整数子群，在张量 $\mathbb Q$ 后维数至多 $r_2(L)$。取需要比较的任意有限多个值，选其所对应的 $z_j(x)$，它们张成一个有限生成交换群 $D$。其自由秩至多 $r_2(L)$，扭结子群包含于 $H_{j+1}(G_{n_j},\mathbb Z)$ 的扭结子群。因此

$$
|D/qD|\le q^{r_2(L)}T_{j+1}.
$$

这是有限生成交换群分解的直接结果：每个自由生成元至多贡献 $q$ 个值，扭结的像至多有源扭结群那么大。由于 $qB=0$，映射 $u^{-1}\phi_{n_j}$ 经 $D/qD$ 分解。这个界适用于每个有限选取，故也控制所考察每个纤维的值数。再乘最多 $T_j$ 个纤维，即得结论。

## 源码对照

- `BOdd`、`SUpper` 的量词在 [LemmaKOfSteps.lean 第 11、100 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/LemmaKOfSteps.lean)。`selmer_upper_bound_of_inputs`、`sUpperOf` 在 [SUpperOf.lean 第 21、64 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/SUpperOf.lean)。
- 整数提升与 Bockstein [BockAbs.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/TorsionRankCounts/BockAbs.lean)。整数同调上的取值与递推 [Descend.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/TorsionRankCounts/Descend.lean)、[PhiZSeq.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/TorsionRankCounts/PhiZSeq.lean)。
- 扭结稳定性 [TorsStab.lean 第 16 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/TorsionRankCounts/TorsStab.lean)，有理秩入口 [BOdd.lean 第 3 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/BOdd.lean)。

本篇与 Lean 源码对读。稳定性使用 Dedekind 环上矩阵群的同调稳定范围。有理秩与扭结阶分别见[高权消去后的秩界](%E4%B8%BA%E4%BB%80%E4%B9%88%E9%87%8D%E5%A4%8D%E7%9F%A9%E9%98%B5%E5%9D%97%E4%BB%A5%E5%90%8E%E5%8F%AA%E5%89%A9%E6%AF%8F%E4%B8%AA%E5%A4%8D%E5%A4%84%E4%B8%80%E4%B8%AA%E6%96%B9%E5%90%91.md)和[按轨道计数的扭结界](Hermitian%E5%BD%A2%E5%BC%8F%E6%80%8E%E6%A0%B7%E7%BB%99%E7%9F%A9%E9%98%B5%E7%BE%A4%E7%9A%84%E6%89%AD%E7%BB%93%E8%AE%BE%E4%B8%8A%E7%95%8C.md)。
