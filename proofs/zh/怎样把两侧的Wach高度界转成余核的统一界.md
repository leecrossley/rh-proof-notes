# 怎样把两侧的 Wach 高度界转成余核的统一界

## 命题

设 $\ell$ 为素数，$O$ 是混合特征 $(0,\ell)$ 的完备离散赋值环，$R=O[[U]]$，$A=\prod_{i\in\mathbb Z/n\mathbb Z}R$，其中 $n\ge1$。取分圆层 $s\ge1$，$X=(1+U)^{\ell^{s-1}}-1$，$Q=\phi(X)/X$，其中 $\phi(U)=(1+U)^\ell-1$，$\phi$ 固定 $O$。在 $A$ 上的 Frobenius 先循环移动坐标，再对各坐标施加 $\phi$，故它把第 $i-1$ 分量送到第 $i$ 分量。

考虑两个含 Wach 子模 $N_1,N_2$ 的 $A$-模 $D_1,D_2$。给定两边的 Frobenius 半线性算子 $\Phi_1,\Phi_2$ 和一个与它们相容的 $A$-线性映射 $F:D_1\to D_2$，满足 $F(N_1)\subset N_2$。用 $N_{a,i}$ 表示 $N_a$ 的第 $i$ 分量。假定下面的条件：

1. $N_2$ 为有限自由 $A$-模，因而各 $N_{2,i}$ 具有同一有限秩。并且 $N_{2,i}$ 与 $R$-线性张成的 $\Phi_2(N_{2,i-1})$ 在允许除以 $Q$ 后相等。
2. 给定 $M_i,h_i\ge0$。有 $Q^{M_i}\Phi_2(N_{2,i-1})\subset N_{2,i}$，且 $Q^{h_i}N_{1,i}\subset\operatorname{span}_R\Phi_1(N_{1,i-1})$。这是本证明实际用到的两条 Wach 高度不等式。
3. 存在某个 $c\ge0$，使 $U^cN_{2,i}\subset F(N_{1,i})$ 对所有 $i$ 成立。

则取 $H=\max_i(M_i+h_i)$，有

$$
X^HN_{2,i}\subset F(N_{1,i})\qquad\text{对所有 }i.
$$

第 3 条中的 $c$ 可以随格变动。结论的指数只取决于两侧的高度。在工程里 $M_i,h_i$ 分别是 Hodge 过滤跳点窗口的左、右宽度。

## 证明

令

$$
\mathfrak a_i=\{g\in R:gN_{2,i}\subset F(N_{1,i})\}.
$$

这是商模 $N_{2,i}/F(N_{1,i})$ 的零化理想。第 3 条给 $U^c\in\mathfrak a_i$。我们将证明 Frobenius 的理想递推 $Q^H\mathfrak a_i\subset R\phi(\mathfrak a_{i-1})$。

取 $g\in\mathfrak a_i$ 并展开

$$
Q^H g=\sum_{j=0}^{\ell-1}(1+U)^j\phi(z_j).
$$

为证明 $z_j\in\mathfrak a_{i-1}$，任取 $y\in N_{2,i-1}$。由目标端的高度，$Q^{M_i}\Phi_2(y)\in N_{2,i}$。所以 $gQ^{M_i}\Phi_2(y)$ 在 $F(N_{1,i})$ 中，取一个原像 $x\in N_{1,i}$。源端的高度给 $Q^{h_i}x$ 是 $\Phi_1(N_{1,i-1})$ 的 $R$-线性组合。再乘 $Q^{H-M_i-h_i}$ 并施加 $F$，得到

$$
Q^H g\,\Phi_2(y)\in\operatorname{span}_R\Phi_2\bigl(F(N_{1,i-1})\bigr).
\tag{1}
$$

借助 Frobenius 基，把 (1) 右边的每个系数展开成 $\sum_j(1+U)^j\phi(b_j)$。半线性使 $\phi(b_j)$ 移进 $\Phi_2$ 内，故右边可写成 $\sum_j(1+U)^j\Phi_2(y_j)$，而每个 $y_j$ 在 $F(N_{1,i-1})$ 中。左边从 $Q^H g$ 的展开等于 $\sum_j(1+U)^j\Phi_2(z_j y)$。

这个表示对于原向量 $y_j$ 唯一。事实上取 $N_{2,i-1}$ 的基 $b_1,\ldots,b_r$。两格在允许除 $Q$ 后相等，各分量又有相同的秩。在 $R$ 的分式域中，$r$ 个 $\Phi_2(b_a)$ 张成秩 $r$ 的空间，因而线性无关。对每个 $a$ 比较 $\Phi_2(b_a)$ 的系数，再用 $(1+U)^j$ 的 Frobenius 坐标唯一性，就得到 $z_j y=y_j$。于是 $z_j y\in F(N_{1,i-1})$ 对任意 $y$ 成立，得 $z_j\in\mathfrak a_{i-1}$。

现在符合[Frobenius 递推的理想引理](%E6%80%8E%E6%A0%B7%E7%94%A8Frobenius%E9%80%92%E6%8E%A8%E6%8A%8A%E6%9C%AA%E7%9F%A5%E4%BD%99%E6%A0%B8%E6%8C%87%E6%95%B0%E9%99%8D%E5%88%B0%E7%AA%97%E5%8F%A3%E5%AE%BD%E5%BA%A6.md)的全部条件，所以 $X^H\in\mathfrak a_i$。进一步，当 $s=1,\ell\ne2$ 且 $K_w/\mathbb Q_\ell$ 不分歧时，$X=U$，就能[把参数幂零化换为素数幂零化](%E6%80%8E%E6%A0%B7%E6%8A%8AWach%E4%BD%99%E6%A0%B8%E4%B8%AD%E7%9A%84%E5%8F%82%E6%95%B0%E5%B9%82%E6%8D%A2%E6%88%90%E7%B4%A0%E6%95%B0%E5%B9%82.md)。

## Lean 对照

- `p5` 的前两项给两个方向的 Frobenius 控制。`wachLengthLatticeMap` 规定最终 $X^H$ 指数。[DeltaInvariantLattices.lean:146](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/DeltaInvariantLattices.lean#L146) · [同文件:334](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/DeltaInvariantLattices.lean#L334)
- `indep_of_commensurable`、`decomp_unique` 负责比较坐标，`key_inclusion` 就是 (1) 及随后转成 $\mathfrak a_i$ 的递推。[CokernelCrystallineSurjectionKilledByXPow.lean:25](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CokernelCrystallineSurjectionKilledByXPow.lean#L25) · [同文件:85](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CokernelCrystallineSurjectionKilledByXPow.lean#L85) · [同文件:233](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CokernelCrystallineSurjectionKilledByXPow.lean#L233)
- `X_pow_kills_coker` 单独取得定性的 $U^c$ 包含，再取源及目标的高度界。目标可用同一窗口，因为它是源的晶体商表示。[CokernelCrystallineSurjectionKilledByXPow.lean:411](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CokernelCrystallineSurjectionKilledByXPow.lean#L411) · [高度界源码](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeHeightsFromHodgeJumps.lean#L382)

状态为源码级推导。另行未重编译。上游分别见[定性余核](%E4%B8%BA%E4%BB%80%E4%B9%88%E6%99%B6%E4%BD%93%E6%A0%BC%E6%BB%A1%E5%B0%84%E7%9A%84Wach%E4%BD%99%E6%A0%B8%E5%8F%AF%E8%A2%AB%E4%B8%A4%E7%A7%8D%E5%B9%82%E6%9D%80%E6%8E%89.md)与[过滤跳点给出的两侧高度](%E8%BF%87%E6%BB%A4%E8%B7%B3%E7%82%B9%E6%80%8E%E6%A0%B7%E7%BB%99Wach%E6%A8%A1%E7%9A%84%E4%B8%A4%E4%BE%A7Frobenius%E9%AB%98%E5%BA%A6.md)。
