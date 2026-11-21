# 怎样按过滤跳点选择算子因子来消去 Laurent 极点

## 命题

设 $L$ 为域，$V$ 为 $L$-线性空间，$\operatorname{Fil}^{a}V$ 为整数编号的递减过滤。令 $Y,y'$ 为非负整数，$u\in L^\times$，$P(t)\in L[[t]]$ 且 $P(0)\ne0$。对每个 $x\in\mathbb Z$，定义

$$
c(x)=\frac{u^{-x}-1}{P(0)}.
$$

在下方有界的 $V$ 值 Laurent 级数上定义

$$
D\left(\sum_k f_k t^k\right)=P(t)^{-1}\sum_k (u^k-1)f_k t^k .
$$

系数下方有界保证每个乘法系数是有限和。设有限表 $S$ 包含所有 $a+j$，其中

$$
\operatorname{Fil}^{a}V\ne\operatorname{Fil}^{a+1}V,\qquad y'<j\le Y .
$$

那么对任意 $f=\sum_k f_k t^k$，若 $f_k\in\operatorname{Fil}^{-k-Y}V$ 对所有 $k$ 成立，则

$$
g=\prod_{x\in S}(D-c(x))f
\qquad\text{满足}\qquad
g_k\in\operatorname{Fil}^{-k-y'}V
\quad\text{对所有 }k .
$$

这是工程里只乘选出的算子因子，就能减少允许极点阶数的线性代数步骤。

## 证明

先看标量级数的阶数。若 $h(t)$ 从次数 $b$ 开始，则 $Dh$ 的次数也至少为 $b$。它在 $t^b$ 的系数是 $h_b(u^b-1)/P(0)$，因为 $P^{-1}$ 的常数项是 $P(0)^{-1}$。所以 $D-c(-b)$ 将这种级数的次数至少抬到 $b+1$。其余因子 $D-c(x)$ 总能保持已有的阶数下界。所有因子都是 $D$ 的一次多项式，可以交换次序。

固定一个 $k$，取任意线性泛函 $\lambda:V\to L$，使它消去 $\operatorname{Fil}^{-k-y'}V$。令 $\lambda$ 作用于级数每一项；它与 $D$ 交换。若 $\lambda$ 消去所有过滤层，它已经消去 $f$ 的每个系数，也就消去 $g$ 的每个系数。

否则，存在最大的 $a$ 使 $\lambda$ 在 $\operatorname{Fil}^{a}V$ 上还有非零值，因为这样的整数集合非空，并且上界是 $-k-y'-1$。它在下一层上为零，因此 $a$ 是一个实际跳点。由 $f_b\in\operatorname{Fil}^{-b-Y}V$ 得知，$\lambda(f)$ 的次数至少是 $-a-Y$。若 $y'\le Y$，我们要依次消去次数

$$
-a-Y,\ -a-Y+1,\ \ldots,\ -a-y'-1 .
$$

每个次数 $b$ 所需的根指标为 $-b=a+j$，其中 $y'<j\le Y$，故在 $S$ 中。对这一串次数，指标彼此不同，每个只需从表中取出一次。先按次数递增顺序应用这些因子，再应用余下的因子，便得到 $\lambda(g)$ 的次数至少为 $-a-y'$。若 $y'>Y$，初始阶数下界已经足够，只要保持它。两种情形都推出 $\lambda(g_k)=0$，因为 $k<-a-y'$。一切消去目标子空间的线性泛函都消去 $g_k$，因此 $g_k$ 在目标子空间中。

## 对 Wach 模极点的含义

在一级分圆处，用对数参数 $t$ 展开某个带 $Q^Y$ 分母的 Wach 元素。源码的展开规则给 $\gamma(t^k)=u^k t^k$，加法及系数乘法按通常的 Laurent 卷积。温和不变量参数 $\pi_0$ 的展开 $P(t)$ 的常数项为 $-\ell$。所以 $\pi_0^{-1}(\gamma-1)$ 对应这里的 $D$，公式里 $c(x)=(1-u^{-x})/\ell$。

在同一展开中，$Q=\pi_0+\ell$ 等于 $t$ 乘以一个幂级数单位。因过滤递减，若 $f_j\in\operatorname{Fil}^{-j-Y}V$，乘任一无负幂的幂级数仍保住这个逐次包含。对一项的系数 $j\le k$，有 $\operatorname{Fil}^{-j-Y}\subseteq\operatorname{Fil}^{-k-Y}$，故卷积留在目标层。乘单位及其逆都保住包含，所以乘 $Q^Y$ 与把过滤线平移 $Y$ 的效果相同。工程的展开判据把属于原 Wach 格转换为平移 $0$ 的条件。用上面的结论取 $y'=0$，便将 $\delta=\pi_0^{-1}(\gamma-1)$ 的指定因子积送回原 Wach 格。各系数分量按这一规则分别处理，最后求和。

## Lean 对照

- `filtLaurent_triangular` 计算分次的标量，`filtLaurent_prod_raises` 逐次抬升阶数，`filtLaurent_shift_line` 用一个消去目标过滤层的泛函完成证明。[FiltLaurentProdPreserves.lean:26](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/FiltLaurentProdPreserves.lean#L26) · [同文件:52](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/FiltLaurentProdPreserves.lean#L52) · [同文件:77](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/FiltLaurentProdPreserves.lean#L77)
- `wachExp_mem_iff` 用 $Q$ 的一级展开平移过滤线，`wachShift_mem_of_exp` 代入算子。`dss_semisimple_of_used` 在各系数分量分别应用，再用分量投影和为 $1$ 还原。[WachShiftMemOfExpansions.lean:58](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachShiftMemOfExpansions.lean#L58) · [同文件:79](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachShiftMemOfExpansions.lean#L79) · [GammaOperatorSemisimpleOfConclusions.lean:72](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/GammaOperatorSemisimpleOfConclusions.lean#L72)
- 左乘 $\pi_0^{-1}$ 后的递推等于多项式作用，这是 `lifta_seq` 和 `lifta_semiO`。用该积补足包含于 $T R(T)$ 的其余因子，即得二次障碍证明里的整化输入。[BaseChangePreservesUnitaryOf.lean:978](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/BaseChangePreservesUnitaryOf.lean#L978) · [同文件:1005](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/BaseChangePreservesUnitaryOf.lean#L1005) · [二次障碍的证明](%E6%80%8E%E6%A0%B7%E7%94%A8%E5%88%86%E6%AC%A1%E4%B8%8E%E5%A4%9A%E9%A1%B9%E5%BC%8F%E6%B6%88%E5%8E%BBHerr%E5%A4%8D%E5%BD%A2%E7%9A%84%E4%BA%8C%E6%AC%A1%E9%9A%9C%E7%A2%8D.md)

状态为源码级推导。另行未重新编译。应用部分明确使用了工程的一级分圆展开判据。
