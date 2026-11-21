# 为什么两个 Wach 格反演参数后相同

## 命题

设 $A=\prod_{i=1}^n O[[U]]$ 为分圆系数环，$E$ 为其 étale 系数环，即 $A[1/U]$ 的 $\ell$-进完备化。设 $T$ 为秩 $r$ 的晶体 $O$-格，$D$ 为其 étale 模，有同名 Frobenius $\varphi$。设 $X,Q\in A$ 满足 $\varphi(X)=XQ$。项目中 $X$ 是 $(1+U)^{\ell^{s-1}}-1$，$Q$ 为第 $\ell^s$ 分圆多项式在 $1+U$ 的值。取两个秩 $r$ 的自由 $A$-格 $S_1,S_2\subset D$，都满足 $E\otimes_A S_i=D$。对 $i=1,2$ 假定：

- 对每个 $z\in S_i$，某个 $Q$ 幂乘 $\varphi(z)$ 后属于 $S_i$。
- 对每个 $z\in S_i$，某个 $Q$ 幂乘 $z$ 后属于 $A\varphi(S_i)$，即这些 Frobenius 像的 $A$-线性张成。

使用下列共同周期比较数据。取 $B^+=O\otimes_{\mathbb Z_\ell}W(\mathcal O_{\mathbb C_\ell^\flat})\subset B=O\otimes_{\mathbb Z_\ell}W(\mathbb C_\ell^\flat)$，其中 $\mathbb C_\ell^\flat$ 为倾斜域。系数映射把 $A$ 送入 $B^+$，把 $E$ 送入 $B$，与 Frobenius 相容，且 $E\cap B^+=A$。有 $D\to B\otimes_O T$ 的相容比较映射 $J$，它经 $E\to B$ 半线性、与 Frobenius 相容，且 $J(D)$ 在 $B$ 上张成 $B\otimes_O T$。在这些条件下，有 $a\ge0$ 满足

$$
X^a S_1\subset S_2,\qquad X^a S_2\subset S_1 .
\tag{1}
$$

## 证明

对其中一个格 $S$ 作比较。取 $S$ 的基 $b_1,\ldots,b_r$ 和 $T$ 的 $O$-基。用 $C$ 的第 $i$ 行表示 $J(b_i)$ 在后一个基中的坐标。因为 $b_i$ 也是 $D$ 的 $E$-基，$J(b_i)$ 在 $B$ 上生成整个 $B\otimes_O T$。有 $r$ 个生成元，故它们是基，$C$ 可逆。

两侧 Frobenius 性质各用在有限个 $b_i$ 上，共取同一个指数 $m$。半线性说明 $A\varphi(S)$ 由 $\varphi(b_1),\ldots,\varphi(b_r)$ 张成。因此存在 $A$ 系数矩阵 $F,H$ 使

$$
Q^m\Phi(C)=F C,\qquad Q^m C=H\Phi(C)
\tag{2}
$$

在周期比较中成立。式中 $F,H,Q,X$ 都用它们在 $B^+$ 的像表示。$\Phi$ 逐系数作用。由于 $\Phi(X)=XQ$，第一个式子化为 $\Phi(X^mC)=F(X^mC)$。由[Witt 系数整性](%E4%B8%BA%E4%BB%80%E4%B9%88Frobenius%E7%9F%A9%E9%98%B5%E6%96%B9%E7%A8%8B%E8%BF%AB%E4%BD%BFWitt%E7%B3%BB%E6%95%B0%E6%95%B4%E5%8C%96.md)，$X^mC$ 的全部系数都在 $B^+$。因此

$$
J(X^m S)\subset B^+\otimes_O T.
\tag{3}
$$

第二个式子用于逆矩阵。左乘 $C^{-1}$，右乘 $\Phi(C^{-1})$，得 $Q^m\Phi(C^{-1})=C^{-1}H$。于是 $\Phi(X^m C^{-1})=(X^m C^{-1})H$，同一整性引理说明 $X^mC^{-1}$ 的系数都在 $B^+$。现在若 $w\in D$ 且 $J(w)\in B^+\otimes_O T$，用 $J(b_i)$ 作基来写 $J(X^m w)$。其坐标向量等于 $J(w)$ 在 $T$ 的基下的坐标右乘 $X^m C^{-1}$，故每项都在 $B^+$。但 $X^m w$ 在 $b_i$ 之下的坐标在 $E$，由半线性，两组坐标在 $B$ 中一样。利用 $E\cap B^+=A$，这些坐标全在 $A$，于是

$$
w\in D,\ J(w)\in B^+\otimes_O T\quad\Longrightarrow\quad X^m w\in S .
\tag{4}
$$

分别对 $S_1,S_2$ 取这样的 $m_1,m_2$。给 $z\in S_1$，先用 (3) 使 $J(X^{m_1}z)$ 到整周期格，再用 $S_2$ 的 (4) 得 $X^{m_1+m_2}z\in S_2$。交换两格得另一方向。这给出 (1)。下一步用[分圆根处的矩阵整除](%E4%B8%BA%E4%BB%80%E4%B9%88%E4%B8%A4%E4%B8%AAWach%E6%A0%BC%E5%9C%A8%E6%B6%88%E5%8E%BB%E5%88%86%E6%AF%8D%E5%90%8E%E5%BF%85%E9%A1%BB%E7%9B%B8%E7%AD%89.md)把这两份参数幂都去掉。

## Lean 对照

- `upper` 检查坐标矩阵，`lower` 检查其逆矩阵，从两个不同的 Frobenius 关系得到 (3) 和周期环上的 (4)。[WachLatticeSandwichAinf.lean:39](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeSandwichAinf.lean#L39) · [同文件:71](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeSandwichAinf.lean#L71)
- `sand_of` 用系数交式把 (4) 降回 $A$。`compare` 用同一个整周期格比较两个自由格，最后入口为 `main`。[WachFreeLatticeEqWachLatticeInvertX.lean:74](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachFreeLatticeEqWachLatticeInvertX.lean#L74) · [同文件:207](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachFreeLatticeEqWachLatticeInvertX.lean#L207) · [同文件:235](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachFreeLatticeEqWachLatticeInvertX.lean#L235)
- Frobenius 标量相容性和 $E\cap B^+=A$ 从系数环的嵌入得到。[WachInclusionXQFrobenius.lean:233](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachInclusionXQFrobenius.lean#L233)

状态为源码级推导。另行未重新编译。Witt 矩阵整性已另篇展开。这里用到工程的 étale 比较 $J$。[系数环交式](%E4%B8%BA%E4%BB%80%E4%B9%88%E6%95%B4%E5%91%A8%E6%9C%9F%E5%9D%90%E6%A0%87%E8%90%BD%E5%9B%9E%E5%88%86%E5%9C%86%E5%B9%82%E7%BA%A7%E6%95%B0%E7%8E%AF.md)另篇展开。
