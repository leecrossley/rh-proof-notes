# 为什么 Teichmüller 参数在各分圆层有指数展开

## 命题

令 $\ell$ 为素数，固定工程的相容周期模型 `LocTied`。记 $\varepsilon=(1,\zeta_1,\zeta_2,\ldots)$ 为相容的分圆倾斜元，$\zeta_s$ 为第 $s$ 层单位根，$[\cdot]$ 表示 Teichmüller 提升。把 $[\varepsilon^{1/\ell^s}]$ 和晶体周期 $\mathbf t=\log[\varepsilon]$ 通过比较映射都看作 $B_{\rm dR}$ 中的元素。对任意 $s,h,M\in\mathbb Z_{\ge0}$ 有

$$
[\varepsilon^{1/\ell^s}]^h
-
\zeta_s^h\sum_{j=0}^{M-1}
 \frac{(h/\ell^s)^j}{j!}\mathbf t^j
\in {\rm Fil}^M B_{\rm dR}.
\tag{1}
$$

此处 $\mathbf t\in{\rm Fil}^1$，而 ${\rm Fil}^M$ 是 ${\rm Fil}^0=B_{\rm dR}^+$ 的理想。[TeichmullerEpsilonRootPowSubZetaExpMemFiltration.lean:128](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TeichmullerEpsilonRootPowSubZetaExpMemFiltration.lean#L128)

## 证明

$M=0$ 时两项都属于 ${\rm Fil}^0$，结论成立。以下在 $\mathbb Q_\ell$-代数 $R_M={\rm Fil}^0/{\rm Fil}^M$ 中计算。写 $I$ 为 ${\rm Fil}^1$ 的像，则 $I^M=0$。所以 $I$ 上的 $\exp$ 和 $1+I$ 上的 $\log$ 都是有限和，两者互逆。由特征零的形式恒等式，$\exp(x+y)=\exp(x)\exp(y)$。也可对多项式截断逐次求导，比较常数项和从第一项到第 $M-1$ 项的系数，得到这些等式。特别是，对任意正整数 $d$，在 $1+I$ 上取 $d$ 次幂是双射，因为取对数后就是乘可逆标量 $d$。

在零层，$\mu_0=[\varepsilon]-1\in{\rm Fil}^1$。晶体对数的比较告诉我们

$$
\mathbf t\equiv \sum_{j=1}^{M-1}\frac{(-1)^{j+1}}{j}\mu_0^j
 \pmod{{\rm Fil}^M}.
$$

这里使用的是周期的具体定义：在第 $M$ 个 de Rham 商中，$\mu_0$ 幂零，对数的比较可用该截断计算。Lean 先乘 $M!$ 对截断作整比较，再除回这一非零的 $\mathbb Q_\ell$ 标量。这样在 $R_M$ 中 $[\varepsilon]=\exp(\mathbf t)$。[TeichmullerEpsilonSubExpMemHodgeFiltration.lean:117](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TeichmullerEpsilonSubExpMemHodgeFiltration.lean#L117) · [同文件:150](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TeichmullerEpsilonSubExpMemHodgeFiltration.lean#L150)

令 $a=[\varepsilon^{1/\ell^s}]$ 及 $d=\ell^s$。在模 ${\rm Fil}^1$ 的 Fontaine 特化下，$a$ 的像是 $\zeta_s$，所以 $a/\zeta_s\in1+I$。又因为 Teichmüller 提升保乘法，有 $a^d=[\varepsilon]$，并有 $\zeta_s^d=1$。因此在 $R_M$ 中

$$
(a/\zeta_s)^d=\exp(\mathbf t)
=\exp(\mathbf t/d)^d.
$$

由 $1+I$ 上取 $d$ 次幂的唯一性，得到 $a=\zeta_s\exp(\mathbf t/d)$。再取第 $h$ 次幂并把指数还原为有限和，即 (1)。

现在设 $L/\mathbb Q_\ell$ 为系数域，$\iota:L\to B_{\rm dR}$ 使 $\iota(\zeta)=\zeta_s$，且令 $f\in L[U]$。将 $U=a-1$ 代入 $f$，可在 $R_M$ 中把 $a-1$ 换成 $\iota(\zeta)\exp(\mathbf t/d)-1$。这是因为 $\iota(L)\subseteq{\rm Fil}^0$，而 ${\rm Fil}^M$ 是其中的理想。因此得到任意多项式的 Taylor 同余，系数来自 $f(\zeta e^Z-1)$，其中 $Z$ 最后换成 $\mathbf t/d$。[PolynomialTeichmullerRootTaylorModFil.lean:64](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/PolynomialTeichmullerRootTaylorModFil.lean#L64)

## Lean 对照

- `epsT_sub_mem` 用 Fontaine 特化识别 $\zeta_s$。`eq_of_pow_eq_of_nilpotent` 对乘积差作几何和分解，因几何和与可逆元只差幂零元而推出唯一性。正文在 $1+I$ 上以截断对数给出同一唯一性结论。[TeichmullerEpsilonRootPowSubZetaExpMemFiltration.lean:19](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TeichmullerEpsilonRootPowSubZetaExpMemFiltration.lean#L19) · [同文件:120](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TeichmullerEpsilonRootPowSubZetaExpMemFiltration.lean#L120)
- `epsT_pow_taylor` 证明 (1)，`poly_taylor` 应用到任意多项式。多项式结果通过[开圆盘取值中的闭性](%E6%80%8E%E6%A0%B7%E6%8A%8A%E5%BC%80%E5%9C%86%E7%9B%98%E7%BA%A7%E6%95%B0%E5%8F%96%E5%80%BC%E5%88%B0%E6%99%B6%E4%BD%93%E5%91%A8%E6%9C%9F%E7%8E%AF.md)传给收敛级数。[同文件:128](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TeichmullerEpsilonRootPowSubZetaExpMemFiltration.lean#L128)

状态为源码对读。另行未重新编译。
