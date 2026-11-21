# 为什么 II 类和 III 类的长度可以合用秩四方法

## 命题

固定本原复 Dirichlet 特征 $\chi$，模数为 $Q$，阶为 $o$。取 [宿主参数 $h$](%E6%AD%A3%E5%8F%B7%E4%B8%8A%E5%90%8C%E8%B0%83%E7%9A%84%E4%B8%83%E7%A7%8D%E9%95%BF%E5%BA%A6%E4%BC%B0%E8%AE%A1%E6%80%8E%E6%A0%B7%E9%80%89%E7%94%A8.md)，其基础特征为 $\chi$，模数记 $N$。对整数 $t$ 要求 $h.\mathrm{Big}(t)$，即宿主的两枚辅助素数均大于 $2t+1,Q,o,p_K,h_K,p_1$，其余记号见该篇。任取一份 $\mathbb Q$ 的代数闭包、奇素数 $\ell$、项目允许的有限 $\ell$-进整数系数环 $O$、整数 $0<e<t$。取在宿主子群 $H\subset(\mathbb Z/N\mathbb Z)^\times$ 上平凡的 $O$-值 Dirichlet 特征 $\psi$，且 $\psi(-1)=(-1)^e$。

记 $V_{\ell,e}(\psi)$ 为 $H^1(G_{\mathbb Q}, (K/O)(\varepsilon_\ell^{-e}\psi_G^{-1}))$ 中在所有有限处惯性群上限制为零，并在 $\ell N$ 的每个素因子处分解群上限制为零的子群，$K=\operatorname{Frac}O$，$\psi_G$ 是复合 $G_{\mathbb Q}$ 在 $N$ 次单位根的作用所得的特征。记 $v_{\ell,e}(\psi)$ 为其 $O$-长度除以分歧指数 $v_O(\ell)$。

**结论。** 在下面列出的秩四变形和自守输入下，存在只依赖 $\chi$ 及这些输入的整数 $C$，使对所有上述数据，只要 $(\ell,e,\psi)$ 属于 II 或 III 类，$V_{\ell,e}(\psi)$ 的长度有限且

$$
v_{\ell,e}(\psi)\log\ell\le(\ell Ne)^C.
$$

II 类要求 $e\ge2$、去掉特征的 $\ell$-幂阶部分和模 $\ell$ 幂分量以后所得特征的阶为偶数，且 $\ell\in B_\chi$ 或 $\ell-1\mid2e$。III 类要求 $\ell\notin B_\chi$、$\ell-1\mid2e$，且 $\psi$ 非平凡并有奇数阶。$B_\chi$ 为上篇定义的有限素数集。III 类自动有 $e\ge2$，因为 $\ell\ge5$。

## 证明

令 $n_2,n_3$ 分别为项目用 $n_0(\ell,\psi)$ 和模二幂导子指数 $c_2(\psi)$ 算出的两种二进层数，见[二进层数的高度界](%E4%B8%BA%E4%BB%80%E4%B9%88II%E7%B1%BB%E5%92%8CIII%E7%B1%BB%E4%BD%BF%E7%94%A8%E7%9A%84%E4%BA%8C%E8%BF%9B%E5%B1%82%E6%95%B0%E6%9C%89%E5%A4%9A%E9%A1%B9%E5%BC%8F%E9%AB%98%E5%BA%A6.md)。先假定 $O$ 包含 $2^{n_2}$ 次和 $2^{n_3}$ 次单位根。对 II 类取 $n'=n_2$、$P=1$；对 III 类取 $n'=n_3$、$P=p_1$。两类填入的第二种辅助 Dirichlet 特征不同，III 类额外使用模 $p_1$ 的奇阶特征。过了这一步，两类使用相同的变形论证。

精确说，[`dataEx`](%E6%80%8E%E6%A0%B7%E4%B8%BAII%E7%B1%BB%E5%92%8CIII%E7%B1%BB%E6%9E%84%E9%80%A0%E7%A7%A9%E5%9B%9B%E5%8F%82%E8%80%83%E6%95%B0%E6%8D%AE.md) 按此分支产生秩四辛相似变形数据 $D$，其中包含参考表示 $r_0$、剩余表示 $\bar r_0$、辛相似因子及三个有限阶 Galois 特征 $\psi_G,\xi,\omega$。它还给一个分歧集合 $S=\{p:p\mid2\ell NP\}$，以及关于 $D$ 的 `Good` 和 `OfChar` 条件。将 $\psi,e$ 固定，把零分解群限制条件的素数集改成 $S$，保留所有惯性群上的零限制，所得 $O$-长度记 $D.\mathrm{sha}$。在新添的素数 $p\nmid\ell N$ 处，惯性群上的零限制已经自动推出分解群上的零限制，所以原长度至多这个长度，见[局部化条件的比较](%E4%B8%BA%E4%BB%80%E4%B9%88%E6%83%AF%E6%80%A7%E7%BE%A4%E4%B8%8A%E7%9A%84%E6%B6%88%E5%A4%B1%E8%83%BD%E4%BC%A0%E5%88%B0%E6%96%B0%E7%9A%84%E5%88%86%E8%A7%A3%E7%BE%A4.md)。

秩四输入如下。`SymplecticFourImageDense` 给出 $D$ 的不可约变形点的自守性以及有限性、排除整表示保持两块的条件。`RigiditySymplecticFour` 给出在这些点的无穷小变形都来自辛李代数的共轭。`CohomologyHyp`、`LemmaP` 构造带两级分次的形式变形模型。`LemmaM`、`LemmaM'` 和 `SoV`、`SoFin` 将局部化核的长度注入次数 $-1$ 的余切长度，再用分次特征零点的迹差控制。`NumberSp4Alt` 提供数值形式的迹分离，即对同一重量、级和合法局部条件下的不可约成分，用一个非零整数统一控制 Frobenius 迹差乘积。`CorX` 是用于构造 $D$ 的导子与剩余 Bernoulli 条件。这里按 `sp4Main_alt` 的假设列出各项，后续各篇给具体要用的结论。

由[三个特征的级和阶](%E4%B8%89%E4%B8%AA%E8%BE%9B%E7%9B%B8%E4%BC%BC%E7%89%B9%E5%BE%81%E6%80%8E%E6%A0%B7%E5%85%B1%E7%94%A8%E4%B8%80%E7%BB%84%E7%BA%A7%E4%B8%8E%E9%98%B6.md)，取

$$
M=\ell\,2^{n'}NP,\qquad k=(\ell-1)2^{n'}(2o).
$$

三个特征均在 $G_{\mathbb Q(\mu_M)}$ 上平凡，且阶均整除 $k$。令 $p$ 为最小的满足 $p\ge5$ 且 $p\nmid\ell NP$ 的素数。它既不整除 $M$，也不在 $S$ 中。迹分离在 $p$ 上给一个统一的 Frobenius $\sigma$，使每个不可约变形点的迹与 $r_0$ 的迹有非零差值。分次余切估计和迹差乘积控制合用，给出 $s=D.\mathrm{sha}<\infty$ 且

$$
\frac{s}{v_O(\ell)}\log\ell
\le 2C_0\,k\,[M(e+1)]^A\log p .
$$

右边使用的 $C_0,A$ 来自 `NumberSp4Alt`，对整族数据通用。把 $M,k,p$ 的定义代入，[二进层数与各项大小](%E4%B8%BA%E4%BB%80%E4%B9%88II%E7%B1%BB%E5%92%8CIII%E7%B1%BB%E4%BD%BF%E7%94%A8%E7%9A%84%E4%BA%8C%E8%BF%9B%E5%B1%82%E6%95%B0%E6%9C%89%E5%A4%9A%E9%A1%B9%E5%BC%8F%E9%AB%98%E5%BA%A6.md) 表明右边不超过 $(\ell Ne)^C$，其中 $C$ 可预先按 $\chi,C_0,A$ 选择。这就处理了有足够单位根的 $O$。

对任意原系数环 $O$，在同一个 $\overline{\mathbb Q}_\ell$ 内取包含 $O$ 及原始 $2^{n_2+n_3}$ 次单位根的允许系数环 $O'$，把 $\psi$ 的值映入 $O'$。注入性保持特征的群核，故其导子保持不变；它也保持阶、各素数分量和奇偶性等式。因而 $n_2,n_3$、II 或 III 的归类、在 $H$ 上平凡等条件在换环后均保持。最后，平坦换环将有限长度乘上 $v_{O'}(\pi_O)$，而分歧指数 $v_O(\ell)$ 乘上同一个数。因此有限性和归一化长度都可搬回原 $O$。这完成两类断言。

## Lean 对照

- [`countII_and_countIII_of_printsH_of_sp4In`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/AdjointLiftingOfCohomology.lean#L33) [`countII_and_countIII_of_printsH_of_sp4In`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/AdjointLiftingOfCohomology.lean#L33) 是 RH 主窗口实际调用的入口。它还要求 `HypothesesH'`、`LemmaK` 和 `SymplecticFourImageDense`。
- [`sp4Main_alt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/ConductorAtMapInjectiveCoeff.lean#L131) [`sp4Main_alt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/ConductorAtMapInjectiveCoeff.lean#L131) 应用该文件第 74 行的 `main_big`，并用注入换环移除单位根假设。
- [`dataEx`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/DataEx.lean#L366) [`dataEx`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/DataEx.lean#L366)，[`shaEq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/ValProd.lean#L95) [`shaEq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/ValProd.lean#L95)，[`levOf`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/DirGPowOne.lean#L55) [`levOf`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/DirGPowOne.lean#L55)。
- [`exists_frob_nonvanishing_with_sha_bound`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/CountS.lean#L14) [Frobenius 迹非消失与整数上界](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/CountS.lean#L14)，[`galoisRep_ineq_of_allIrreducible_nonvanishing`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/GaloisRepIneqOfAllIrreducibleNonvanishing.lean#L152) [分次轨道的迹差比较](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/GaloisRepIneqOfAllIrreducibleNonvanishing.lean#L152)，[`arith`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/TwoPowClogLe.lean#L172) [右边的参数估计](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/SymplecticGSp4/TwoPowClogLe.lean#L172)，[`coefIndep`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/CoefIndep.lean#L68) [`coefIndep`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HeightAndVanishing/CoefIndep.lean#L68)。本篇为发布版源码对照。
