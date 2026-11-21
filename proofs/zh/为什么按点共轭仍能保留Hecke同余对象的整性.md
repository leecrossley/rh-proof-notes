# 为什么按点共轭仍能保留 Hecke 同余对象的整性

## 命题

设 $O$ 为离散赋值环，$k={\rm Frac}(O)$。令 $X$ 为有限评价点集，$T\subset O^X$ 为 Hecke 系数函数环，$\pi\in X$ 是好点。取两族整表示 $r_x,r'_x:G\to{\rm GL}_n(O)$。假定 $r_x,r'_x$ 在 $k$ 上按点由 $P_x\in{\rm GL}_n(k)$ 共轭。另取同一组字符 $\chi_1,\ldots,\chi_t$ 以及 $r_\pi,r'_\pi$ 的补表示 $\rho,\rho'$，两补表示由 $Q\in{\rm GL}_{n-t}(k)$ 共轭。若 $r,\rho$ 在 $\pi$ 处具有工程的同余对象 `GoodCongruenceObjects`，则 $r',\rho'$ 也有同余对象，且保留同一个惯性元素 $g_0$。

这里的同余对象包含：整系数张成中的两个正交投影 $e_B,e_1$，秩分别为 $t,1$。角块元素 $X_0=e_BX_0e_B$，在好点作用为一串字符值。有限根排序空间 $p:X'\to X$，它的系数代数 $T'\subset O^{X'}$、按点的根函数 $r_j$ 与指定点 $\pi'$。还要求根的乘积多项式、余差乘积和由它定义的秩一投影关系，以及在 $\pi'$ 取补块的满射。最后，每个一般矩阵行列式的系数函数和每个分块行列式都应落在 $T'$。这些条件的精确定义在所列 Lean 结构中，正文说明它们怎样逐项传递。[QuotientHomNonvanishingBound.lean:444](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/QuotientHomNonvanishingBound.lean#L444) · [同文件:493](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/QuotientHomNonvanishingBound.lean#L473)

## 整矩阵如何传过去

对整矩阵函数 $a(x)=\sum_j f_j(x)r_x(g_j)$，其中 $f_j\in T$，用同一组 $f_j,g_j$ 写出

$$
a'(x)=\sum_j f_j(x)r'_x(g_j).
$$

它的系数在 $O$，且在分式域中等于 $P_xa(x)P_x^{-1}$。因此它只依赖原矩阵 $a$ 与 $P_x$，不依赖选了哪组和式。这个过程可逆，给出两族的整张成之间的代数同构。把系数拉到 $T'$ 后相同。特别地，$e_B,e_1,X_0$ 都能传过去，保留它们的乘积关系与秩。

若旧的好点分解由 $e:k^n\to k^{n-t}\oplus k^t$ 实现，新的分解取 $e'=(Q\oplus I)eP_\pi^{-1}$。对每个整张成里的矩阵，新补块仍是整矩阵，因为任意这样的矩阵是若干群作用的整系数线性组合。在好点用这个公式读，补块正是同样系数对 $\rho'(g_j)$ 的线性组合。字符块也保留相同的标量。

还必须证明新取补块仍覆盖 $M_{n-t}(O)$。旧映射满射，所以每个 $C\in M_{n-t}(O)$ 都由一个旧的整张成元素取得。将它传过去后，新的补块为 $QCQ^{-1}$，已经知道它是整的。由此可把逆向也降回整数环。确切地，令 $E_{ab}$ 为矩阵单位。因为 $QE_{ab}Q^{-1}$ 的每个条目在 $O$，所以所有乘积 $Q_{ia}(Q^{-1})_{bj}$ 都在 $O$。对任意 $C'\in M_{n-t}(O)$，在 $Q^{-1}C'Q$ 的每个条目中，$C'$ 的每个系数都与这种乘积相乘。因此 $Q^{-1}C'Q\in M_{n-t}(O)$。先用旧满射取到这个矩阵，再传到新族，便取得原来指定的 $C'$。这一论证解释了只在分式域上共轭却仍有整满射的原因。

## 根排序、行列式与长度怎样保留

取相同的 $X',p,T',r_j,\pi'$，以及同一个 $g_0$。角块特征多项式用整个 $n$ 阶矩阵

$$
Y e_B-X_0+I-e_B
$$

的行列式表示。它与新角块相应矩阵在 $k[Y]$ 中共轭，因此行列式相同，因为 $O[Y]\hookrightarrow k[Y]$，相等已经在 $O[Y]$ 中。故原根函数仍给出新角块的排序和分裂，$T'$ 的生成与秩条件也原样成立。

由根做出的算子 $E=\prod_{j=2}^t(X_0-r_j e_B)$ 仍逐点共轭，因此 $E^2=dE$ 与秩一条件保留，其中 $d=\prod_{j=2}^t(r_1-r_j)$。在好点它的分块表达沿 $e'$ 保留，标量 $d(\pi')$ 没有变，所以用 $O/(d(\pi'))$ 计算的长度也保留。

最后，若 $a_1,\ldots,a_m$ 是整张成元素，$\det(\sum_j Z_ja_j(x'))$ 是关于形式变量 $Z_j$ 的多项式。引入这些变量后同一个 $P_{p(x')}$ 仍可作共轭，故多项式和每一系数函数相同。若把若干 $a_{jk}$ 拼成大分块矩阵，只需用对角矩阵 ${\rm diag}(P_{p(x')},\ldots,P_{p(x')})$ 共轭，就得其行列式也相同。因为在旧族这些系数函数属于 $T'$，在新族同样成立。这样保留了整体格指数证明真正用于下降的整系数行列式条件。

## Lean 对照

- `BlockDeterminant.main` 用同组系数传递整矩阵函数，`det_generic_eq`、`det_block_eq` 保留一般系数与分块行列式。[BlockDeterminant.lean:32](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/BlockDeterminant.lean#L32) · [同文件:49](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/BlockDeterminant.lean#L49) · [同文件:63](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/BlockDeterminant.lean#L63)
- `exists_cj_of_forall` 用矩阵单位检查共轭的反向整性，`Act.conj` 转移好点分块，`main` 逐项保留同余对象与同一个 $g_0$。[PointObjectsTransportAlongConjugationOverFractio.lean:107](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/PointObjectsTransportAlongConjugationOverFractio.lean#L107) · [同文件:154](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/PointObjectsTransportAlongConjugationOverFractio.lean#L154) · [同文件:210](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/PointObjectsTransportAlongConjugationOverFractio.lean#L210)

状态为源码级推导。另行未重新编译。
