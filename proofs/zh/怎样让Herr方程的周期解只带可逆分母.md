# 怎样让 Herr 方程的周期解只带可逆分母

## 命题

沿用[两侧 Wach 格比较](%E4%B8%BA%E4%BB%80%E4%B9%88%E4%B8%A4%E4%B8%AAWach%E6%A0%BC%E5%8F%8D%E6%BC%94%E5%8F%82%E6%95%B0%E5%90%8E%E7%9B%B8%E5%90%8C.md)的 $A$、$B^+\subset B$、$X,Q,\varphi$、Wach 格 $N=N(T)$ 及 $J$。记 $P^+=B^+\otimes_O T\subset P=B\otimes_O T$。假定 $X,Q$ 的周期像在 $B$ 中可逆，$\varphi(X)=XQ$。设存在 $M\ge0$ 使 $X^M J(N)\subset P^+$。给有限多重集 $I$ 的非负整数，令

$$
\Lambda=\prod_{j\in I}\varphi^j(Q).
$$

取 $y\in D(T)$ 使 $\Lambda y\in N$。若 $b\in P$ 满足 $(\varphi-1)b=J(y)$，则令 $m\ge0$ 为 $I$ 各项的一个上界（空集时取 $m=0$），

$$
X_*=\prod_{j=0}^m\varphi^j(X),\qquad
 a=M+|I|
$$

满足 $X_*^a b\in P^+$。若工程的晶体周期比较 $\beta:B^+\to L\otimes B_{\rm cris}$ 中 $\beta(X)$ 及其 Frobenius 迭代均为单位，则 $b$ 可以在晶体周期模中取比较值。

## 证明

令 $L_*=\prod_{j=0}^m\varphi^j(Q)$。用 $\varphi(X)=XQ$ 对各因子逐一作用，得 $\varphi(X_*)=X_*L_*$。因为 $X\mid X_*$，且 $I$ 的每项都被 $0,\ldots,m$ 覆盖，$\Lambda\mid L_*^{|I|}$。故

$$
X^M\Lambda\mid (X_*L_*)^{M+|I|}.
\tag{1}
$$

所有整除均在 $A$ 中成立，即使 $I$ 为空也一样。

设 $v=X_*^a b$。由半线性和 $(\varphi-1)b=J(y)$，

$$
\varphi(v)=L_*^a v+(X_*L_*)^a J(y).
\tag{2}
$$

最后一项在 $P^+$ 中。理由是 $X^M\Lambda J(y)=X^MJ(\Lambda y)\in P^+$，而 (1) 的商来自 $A\subset B^+$。在 $T$ 的基下，(2) 是[Witt Frobenius 矩阵整性](%E4%B8%BA%E4%BB%80%E4%B9%88Frobenius%E7%9F%A9%E9%98%B5%E6%96%B9%E7%A8%8B%E8%BF%AB%E4%BD%BFWitt%E7%B3%BB%E6%95%B0%E6%95%B4%E5%8C%96.md)的一个列矩阵情形。第一项只含整系数 $L_*^a$，第二项是整余项，故 $v\in P^+$。

此时可以把 $v$ 逐系数用 $\beta$ 送到晶体周期模，再除以单位 $\beta(X_*^a)$。这样得到 $b$ 的比较值。同一个元素若另有可用分母，将两式交叉相乘后使用 $B^+\hookrightarrow B$ 的单射可知比较值相同。工程的 $X$ 对应分圆周期 $[\epsilon_1]-1$，其比较像可逆是项目周期环的条件。Frobenius 相容性使这些像的迭代也可逆。

## Lean 对照

- `φ_prod` 计算 $X_*$ 的 Frobenius，`multiset_dvd` 按重数处理分母。`of_sand` 对 $X_*^a b$ 写出 (2) 并使用 Witt 整性。主入口 `main` 代入实际的 Wach 格周期包含。[MemRangeOfFrob.lean:72](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/MemRangeOfFrob.lean#L72) · [同文件:79](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/MemRangeOfFrob.lean#L79) · [同文件:114](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/MemRangeOfFrob.lean#L114) · [同文件:163](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/MemRangeOfFrob.lean#L163)
- `isUnit_prod` 用晶体周期比较的 Frobenius 相容性，使各分母像可逆。[HerrCocyclePolesFrobeniusQCrystalline.lean:406](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/HerrCocyclePolesFrobeniusQCrystalline.lean#L406)

状态为源码级推导。另行未重新编译。
