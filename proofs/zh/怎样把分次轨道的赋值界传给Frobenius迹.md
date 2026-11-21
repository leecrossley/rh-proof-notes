# 怎样把分次轨道的赋值界传给 Frobenius 迹

归一化的上同调类给出一个长度下界 $V\le\lambda$，其中 $\lambda$ 是变形模型中一个权 $-1$ 余切商的长度。本篇证明另一方向的估计：由一条迹差函数在有限个轨道代表上的取值控制 $\lambda$。在 I 类计数中，这两步合起来才给出单个特征的长度界。[长度下界](%E5%BD%92%E4%B8%80%E5%8C%96%E4%BD%99%E9%97%AD%E9%93%BE%E6%80%8E%E6%A0%B7%E7%BB%99%E5%87%BA%E5%8F%98%E5%BD%A2%E7%8E%AF%E4%B8%8A%E7%9A%84%E5%AF%BC%E5%AD%90.md) · [同核计数](%E6%80%8E%E6%A0%B7%E7%94%A8%E4%B8%80%E4%B8%AAFrobenius%E7%9A%84%E8%BF%B9%E5%B7%AE%E6%8E%A7%E5%88%B6%E5%90%8C%E6%A0%B8%E7%89%B9%E5%BE%81%E7%9A%84%E9%95%BF%E5%BA%A6.md)

## 命题与假设

令 $\ell$ 为奇素数，$K=\overline{\mathbb Q}_\ell$，$O$ 是其中对 $\mathbb Z_\ell$ 有限的系数离散赋值环，记其绝对分歧指数为 $e_O$。以 $v_\ell(\ell)=1$ 归一化赋值。沿用 `model_lower` 的拓扑群 $G,H$、连续同态 $\iota$、符号 $\eta$、特征 $\Psi$、标记 $c,g_1$、局部条件、变形环 $R$、泛表示 $r$ 和分次模型 $A\xrightarrow q R$。记分次方程理想为 $I_A=\ker q$，且 $x_0:R\to O$ 为基点。令 $f:R\to K$ 为一个 $O$-代数映射，若它把 $\mathfrak m_R$ 中所有元素映进 $\{x:|x|_\ell<1\}$，称 $f$ 为局部点。用 $r_f$ 表示对泛表示条目求值所得的表示。限制至 $\ker\eta$ 后确实是普通的秩三表示。$\mathrm{TwoPt}$ 指局部点中限制 $\left.r_f\right|_{\ker\eta}$ 既非上三角也非下三角的点。

假设 $R$ 中由总权为 $0$ 的泛矩阵条目乘积生成的 $O$-子代数是有限 $O$-模。另假设以下三条表示的刚性性质，源码合称 `PtHyp`。

1. 若局部点的限制同时为上三角和下三角，则它的表示就是基点表示。
2. 在基点，对每个 $j\le0$，任意权 $j$ 的一阶变形是由无穷小共轭给出的。这里“权 $j$”指变形的矩阵余闭链只在 $w_i-w_b=j$ 的 $(i,b)$ 条目上取值。
3. 在每个 `TwoPt`，所有一阶变形均由无穷小共轭给出。

还假设分次长度引理 `LemmaM`。其陈述、余切格的整理和有限轨道的证明见[分次长度引理](%E5%88%86%E6%AC%A1%E9%95%BF%E5%BA%A6%E5%BC%95%E7%90%86%E6%80%8E%E6%A0%B7%E5%8C%96%E6%88%90%E6%9C%89%E9%99%90%E8%BD%A8%E9%81%93%E4%B8%8A%E7%9A%84%E8%B5%8B%E5%80%BC%E4%BC%B0%E8%AE%A1.md)。给定 $\sigma\in\ker\eta$，假设对每个 `TwoPt`，下式不为零：

$$
d(f)=\operatorname{tr}r_f(\sigma)-\operatorname{tr}r_0(\sigma).
$$

则 $\lambda$ 有限。存在有限集合 $T$ 为 `TwoPt` 在 $D(t)=\operatorname{diag}(t,1,t^{-1})$、$t\in K^\times$ 共轭下的轨道各取一个代表，并且

$$
\frac{\lambda}{e_O}\ \le\ 2\sum_{f\in T}v_\ell(d(f)).
\tag{1}
$$

## 泛矩阵如何传递三角性

在分次环的一点 $\xi:A\to K$ 上，$t\in K^\times$ 的作用把每个 $a\in A_j$ 的取值乘以 $t^j$。因为 $r(g)_{ij}$ 有次数 $w_i-w_j$ 的提升，这项作用在矩阵上便是 $D(t)$ 共轭。对 $g\in\ker\eta$ 可以直接从该式读出三角性。对 $g$ 在另一个陪集中，写 $g=g'c$，由 $r(c)$ 的矩阵为单位阵，知 $r(g)$ 的矩阵与 $r(g')$ 相同。

若一侧三角性成立，所有总权同侧的矩阵条目乘积都为零。因为总权是各因子权的和，其中至少有一个因子在那一侧消失。分次模型保证每个齐次 $a\in A_j$ 的 $q(a)$ 都可用总权为 $j$ 的这些乘积的线性组合按 $\mathfrak m_R$-进拓扑逼近。局部点上的求值允许通过该极限。取 $z=\ell\in\mathfrak m_R$，有 $f(z)=\ell\ne0$。若某个 $u\in R$ 满足 $|f(u)|_\ell>1$，则 $|f(u^nz)|_\ell>1$ 对大 $n$ 成立，同 $u^nz\in\mathfrak m_R$ 矛盾。由此 $|f(u)|_\ell\le1$。再取极大理想有限个生成元，它们的像模长均小于 $1$。设其中最大模长为 $b<1$，则 $\mathfrak m_R^n$ 中所有元素的像模长不超过 $b^n$。故齐次逼近给出整侧权的消失。反向只需取各泛条目的齐次提升。用同样的逼近，把两个局部点上的 $D(t)$ 共轭等式从条目乘积延拓到齐次元素。因此一侧权消失等价于相应三角性；两个局部点的表示共轭等式拉回为分次作用的等式。

## 为什么可以使用分次长度引理

记 $B$ 为命题中有限的权零子代数。模型的权零像 $q(A_0)$ 包含在 $B$ 中，因为它可以用 $B$ 中的元素逼近，而 $B$ 在 $R$ 中闭。其闭性可从有限性看出：选有限个 $\mathbb Z_\ell$-模生成元，系数空间 $\mathbb Z_\ell^u$ 紧致，求线性组合到 $R$ 连续且 $R$ 分离。于是 $q(A_0)$ 为有限 $O$-模，从而 $A_0$ 在 $A/I_A$ 中的像为有限 $O$-模。这验证 `M2`。

模型还给出以下两个传递性质。每个满足 $I_A$ 的点，在某个 $t$ 的分次作用后可写成局部点 $f$ 在 $q$ 下的拉回。沿这个拉回点消去 $I_A$ 的导子，来自 $R$ 上沿 $f$ 的导子。用前一个性质，固定点拉到一个两侧都三角的局部点。由刚性条件 1，它拉回至基点。在权零上分次作用不改变取值，在非零权上两点都为零。因此基点是唯一固定点，`M3` 成立。

还需计算哪些无穷小共轭保持归一化。令 $M=r_f(g_1)_{\mathrm{mat}}$，$J$ 为反对角单位阵。因为 $r_f(c)_{\mathrm{mat}}=1$，且 $c,g_1$ 的符号分别为 $-1,+1$，矩阵 $r_f(cg_1^{-1}c)_{\mathrm{mat}}$ 等于 $JM^tJ$。写 $Z=M-JM^tJ$。归一化使 $Z_{12}=Z_{21}=0$，由反对角反对称性，$Z_{23}=Z_{32}=0$、$Z_{13}=Z_{31}=Z_{22}=0$，且 $Z_{33}=-Z_{11}$。因此 $Z=\mathrm{diag}(d,0,-d)$。这里 $d=M_{11}-M_{33}\ne0$，因为在 $R$ 中相应元素模极大理想等于 $\Psi(g_1)-\Psi(g_1)^{-1}$ 的剩余类，故为单位。

由矩阵 $X$ 给出的归一化余边界，在 $c$ 处的条件是 $X=-JX^tJ$，而在 $g_1,cg_1^{-1}c$ 两项的差上，条件是交换子 $XZ-ZX$ 的 $(1,2),(2,1)$ 条目为零。前一条件给 $X_{22}=X_{13}=X_{31}=0$、$X_{33}=-X_{11}$、$X_{23}=-X_{12}$、$X_{32}=-X_{21}$。后一条件给 $-d X_{12}=d X_{21}=0$。所以 $X$ 只能是 $\mathrm{diag}(1,0,-1)$ 的倍数，反向也由这两个条件立即看出。这是 `normCoc_cob_iff`。在基点，该对角矩阵同所有基点矩阵对易，且被符号的线性对偶作用固定，所以产生零余边界。

现在在基点取一个权 $-2,-1,0$ 中的齐次导子，假设它消去这一权的方程。它自动消去其他权的方程，并由模型导子性质传到 $R$。基点矩阵是对角阵，故从导子的泛条目值取出余闭链时保持权。由刚性条件 2，它为余边界；由归一化计算它为零。导子的条目值便全为零，因此导子自身为零。若这三个权中某个权的方程在余切格张量 $K$ 后张成不全，可选一个非零 $K$-线性函数消去这些方程。把它沿分次余切格拉回正好得到刚刚排除的导子。所以三个权的方程分别张成，加上模型的坐标图和维数数据便是 `M1`。

在两侧都有非零权取值的点，先移动并拉到 $R$。由刚性条件 3 和同一归一化计算，所有允许的余闭链都在一个维数至多 $1$ 的空间内，因为它们都来自 $\mathrm{diag}(1,0,-1)$ 的标量倍数。余闭链由泛条目确定导子，再把关系拉回 $A$，并在 $A_j$ 上除去同一个非零因子 $t^j$。因此这些导子的空间也至多一维，验证 `M4`。

## 选迹差作为权零函数

令 $E_i\in A_0$ 提升第 $i$ 个对角条目 $r(\sigma)_{ii}$。设

$$
a=\sum_{i=1}^3 E_i-\operatorname{tr}r_0(\sigma).
$$

那么 $x(a)=0$，且 $f(q(a))=d(f)$。对满足方程的、两侧都有非零权取值的 $\xi$，选上面所述的 $t,f$。因为 $a$ 的权为零，$\xi(a)=f(q(a))$。因为移动点保持零与非零的模式，$f$ 是 `TwoPt`。由命题假设，$\xi(a)\ne0$。这就是长度引理的最后一个假设 `M5`。

对 $K$ 用 $v=e_Ov_\ell$，它在 $O$ 上给均匀化元赋值 $1$。长度引理给出分次点的有限轨道覆盖，从每个代表转成对应的一个局部点，就得到 `TwoPt` 的有限覆盖。删除其中重复的共轭类，取 $T$。它拉回到 $A$ 后仍覆盖分次点的所有轨道，这是因为任意分次点可移动到局部点，且局部点的共轭关系就是在分次点上的作用。不同的 $T$ 中代表不可能拉回到同一个点，因为各泛条目都有原像。将长度引理应用于这个新覆盖，求和的每一项正是 $e_Ov_\ell(d(f))$。于是除以 $e_O>0$ 得到 (1)。

## Lean 对照与证明范围

- [`model_upper`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeGroups/ModelUpper.lean#L103) `model_upper` 第 103 行证明主命题，`PtHyp` 第 16 行给三条刚性，`vl` 是归一化赋值。[主证明](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeGroups/ModelUpper.lean) · [刚性陈述](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeGroups/Rigid0.lean)
- `model_signs` 第 140 行比较三角性和分次作用，`modelIdeal_finiteness_of_weightZero_finite` 第 102 行用有限性保证权零代数的闭性。[权与三角性](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeGroups/ModelSigns.lean) · [权零有限性](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeGroups/ModelIdealFinitenessOfWeightZeroFinite.lean)
- `gradedModel_spansCot_of_rigid_weights` 第 205 行、`gradedModel_pointCondition_of_ptHyp` 第 53 行、`gradedModel_derivationCondition_of_ptHyp` 第 111 行分别给 `M1`、`M3`、`M4`。[基点余切张成](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeGroups/GradedModelSpansCotOfRigidWeights.lean) · [固定点](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeGroups/GradedModelPointConditionOfPtHyp.lean) · [两侧点](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeGroups/GradedModelDerivationConditionOfPtHyp.lean)
- [`normCoc_cob_iff`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeGroups/NormCob.lean#L30) `normCoc_cob_iff` 第 30 行给无穷小共轭的归一化计算。[矩阵计算](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeGroups/NormCob.lean)
- [`main_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CommutativeAlgebra/GradedModulesLength/MainCotSpan.lean#L32) `main_holds` 第 32 行证明此处调用的 `LemmaM`。本篇为源码对读。表示的刚性、模型的两个传递性质和分次长度引理均明示为输入，未重新编译或查询传递公理。[长度引理源码](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CommutativeAlgebra/GradedModulesLength/MainCotSpan.lean)
