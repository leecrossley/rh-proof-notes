# 为什么晶体扩张的两个 Herr 坐标有指定分母

## 命题

设 $0\to T\xrightarrow{\iota}T'\xrightarrow{q}O\to0$ 为晶体 $O$-格的短正合列，商为平凡格。用[Wach 核格比较](%E4%B8%BA%E4%BB%80%E4%B9%88%E5%9C%A8%C3%A9tale%E6%A0%B8%E9%87%8C%E5%8F%96%E4%BA%A4%E6%81%B0%E5%A5%BD%E5%BE%97%E5%88%B0Wach%E6%A0%B8%E6%A0%BC.md)的分圆记号 $A=\prod_iO[[U]]$、$X,Q$。对第 $i$ 个系数分量，设 $T[1/\ell]$ 在该分量所对应的全部 de Rham 过滤跳点属于 $[-M_i,h_i]$，其中 $M_i,h_i\ge0$，令 $M=\max_i M_i$。取 $e\in N(O)$ 被 $\gamma,\varphi$ 固定，$x\in N(T')$ 满足 $D(q)x=a e$，其中 $a\in O$。

假定 $(\gamma-1)N(T')\subset XN(T')$。此处 $X$ 是有效分圆层参数，较一般 Wach 条件中的 $U$ 可以有更高的次数。它在 étale 环中可逆。则 [扩张类公式](%E4%B8%BA%E4%BB%80%E4%B9%88Herr%E5%AF%B9%E7%9A%84%E4%B8%A4%E4%B8%AA%E7%AE%97%E5%AD%90%E5%B7%AE%E7%BB%99%E5%87%BA%E5%90%8C%E4%B8%80%E4%B8%AA%E6%89%A9%E5%BC%A0%E7%B1%BB.md)所给的两个坐标 $y,z\in D(T)$ 满足

$$
Q^M y\in N(T),\qquad z\in XN(T).
\tag{1}
$$

在工程的 $\Delta$ 不变量版本，也可保留该固定性，并在不变量系数环中用相差单位的对应高度参数。

## 证明

平凡表示的唯一跳点为 $0$。晶体扩张在 de Rham 侧给严格正合列，故 $T'[1/\ell]$ 的每个分量的跳点来自 $T[1/\ell]$ 或 $0$。因为所有窗口都含 $0$，同一 $[-M_i,h_i]$ 控制 $T'[1/\ell]$。由[过滤跳点给 Wach 高度](%E8%BF%87%E6%BB%A4%E8%B7%B3%E7%82%B9%E6%80%8E%E6%A0%B7%E7%BB%99Wach%E6%A8%A1%E7%9A%84%E4%B8%A4%E4%BE%A7Frobenius%E9%AB%98%E5%BA%A6.md)，第 $i-1$ 分量的 $\varphi$ 像乘 $Q^{M_i}$ 后进入第 $i$ 分量的整格。任取 $x\in N(T')$，把它按分量拆开，各项再乘 $Q^{M-M_i}$，求和得 $Q^M\varphi(x)\in N(T')$。因此 $Q^M(\varphi-1)x\in N(T')$。

两算子差都投到零，因为 $a e$ 被两算子固定。于是可由 étale 正合性写 $D(\iota)y=(\varphi-1)x$。故 $D(\iota)(Q^M y)\in N(T')$，由 Wach 核格比较得 $Q^M y\in N(T)$。

对另一个坐标，先写 $(\gamma-1)x=X w$，其中 $w\in N(T')$。投到商得 $X D(q)w=0$。因为 $X$ 在 étale 环中可逆，$D(q)w=0$，所以 $w=D(\iota)w_0$ 对某个 $w_0\in D(T)$ 成立。由核格比较又有 $w_0\in N(T)$。于是 $z=Xw_0\in XN(T)$，证得 (1)。

若 $x$ 已对 $\Delta$ 固定，两坐标也固定，因为两算子与有限子群交换且 $D(\iota)$ 单射。项目在分裂素处再用整不变量环的参数理想相交和单位比较，得到其 Herr 复形采用的同一分母条件。

## Lean 对照

- `Q_pow_φ_mem` 用所有分量指数的最大值，`core` 把两个算子差经 étale 正合性及 Wach 核格识别传回 $T$。总入口调用晶体短正合列的跳点、Wach 高度和有效参数上的分圆平凡性。[CrystallineExtensionIntegralCocycleAllPlaces.lean:61](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CrystallineExtensionIntegralCocycleAllPlaces.lean#L61) · [同文件:76](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CrystallineExtensionIntegralCocycleAllPlaces.lean#L76) · [同文件:114](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CrystallineExtensionIntegralCocycleAllPlaces.lean#L114)
- `wachLattice_galois_trivial_mod_uniformizer` 给 $(\gamma-1)N(T')\subset XN(T')$。使用它及核格比较后，带分母的扩张类可以进入[分裂素处的提升证明](%E5%88%86%E8%A3%82%E7%B4%A0%E5%A4%84%E7%9A%84%E6%99%B6%E4%BD%93%E6%8F%90%E5%8D%87%E4%B8%BA%E4%BB%80%E4%B9%88%E8%A6%81%E4%BB%98%E4%B8%A4%E4%BB%BDWach%E6%8C%87%E6%95%B0.md)。[WachLatticeGaloisTrivialModUniformizer.lean:12](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeGaloisTrivialModUniformizer.lean#L12)

状态为源码级推导。另行未重新编译。有效参数上的分圆平凡性和晶体周期的严格正合性在此作为已标明的上游。
