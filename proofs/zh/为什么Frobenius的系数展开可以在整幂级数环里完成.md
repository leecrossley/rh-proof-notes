# 为什么 Frobenius 的系数展开可以在整幂级数环里完成

## 命题

设 $\ell$ 为素数，$O$ 是完备离散赋值环，$0\ne\ell\in\mathfrak m_O$，其极大理想由 $\varpi$ 生成。令 $R=O[[U]]$。定义固定 $O$ 的环自同态 $\phi$，把 $U$ 送到 $(1+U)^\ell-1$。那么每个 $f\in R$ 都能唯一写成

$$
f(U)=\sum_{j=0}^{\ell-1}(1+U)^j\phi(f_j)(U),\qquad f_j\in R.
$$

即 $R$ 作为 $\phi(R)$-模有显式的基。这一事实后面用来分别检测一个 Frobenius 伸展理想内的各个系数。

## 证明

先用 $U^j$ 作基来证明。定义两个 $O$-线性映射 $S,T:R^\ell\to R$，

$$
S((h_j))=\sum_{j=0}^{\ell-1} U^j h_j(U^\ell),\qquad
T((h_j))=\sum_{j=0}^{\ell-1} U^j \phi(h_j)(U).
$$

对 $S$，按次数模 $\ell$ 读回第 $j$ 个序列，$h_j$ 的第 $m$ 项就是原序列第 $\ell m+j$ 项。故 $S$ 是同构。

模 $\varpi$ 时，$(1+U)^\ell-1=U^\ell$ 因特征为 $\ell$ 成立，故 $T-S$ 的像包含于 $\varpi R$。$R$ 及 $R^\ell$ 对 $\varpi$-进拓扑完备、分离，因为可逐系数取极限，并且「模 $\varpi^n$ 的所有系数固定」正是模 $\varpi^nR$。令 $P=S^{-1}(T-S)$。它把 $\varpi^nR^\ell$ 送到 $\varpi^{n+1}R^\ell$。因此

$$
1+P\quad\text{的逆是}\quad \sum_{n\ge0}(-P)^n,
$$

逐次相乘的有限和余项在每一级 $\varpi$ 过滤中消失。由 $T=S(1+P)$，$T$ 也是同构。最后 $(1+U)^j$ 到 $U^j$ 的换基矩阵是对角为 $1$ 的三角矩阵，系数都在 $O$，换基保持上述唯一表示。特别地，$\phi$ 本身单射。

## Lean 对照

- `bijective_expand` 按次数模 $\ell$ 取系数，`bijective_of_congr` 逐级提升并使用分离性。`phi_free` 组合模 $\varpi$ 的比较和换基。[PhiFree.lean:13](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/PhiFree.lean#L13) · [同文件:123](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/PhiFree.lean#L123)
- `exists_coords_mem` 把这个基用于 Frobenius 伸展后的理想。[XXPowMemOfQQPowMulMemMapPhi.lean:9](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/XXPowMemOfQQPowMulMemMapPhi.lean#L9)

状态为源码级推导。另行未重新编译。
