# 为什么两个 Wach 格在消去分母后必须相等

## 命题

沿用[矩阵逐根整除](%E6%80%8E%E6%A0%B7%E6%B2%BF%E5%88%86%E5%9C%86%E5%B1%82%E9%80%90%E6%A0%B9%E6%B6%88%E5%8E%BB%E7%9F%A9%E9%98%B5%E4%B8%AD%E7%9A%84%E5%88%86%E6%AF%8D.md)的系数环 $A$、算子 $\gamma,\varphi$ 和元素 $U,X,Q$，所以 $\varphi(X)=XQ$。设 $\mathcal D$ 是 $A$-模，上有同名半线性算子 $\gamma,\varphi$，且乘 $X$ 在 $\mathcal D$ 上单射。设 $M,M_1\subset\mathcal D$ 为同一有限秩 $r$ 的自由 $A$-模。假定对 $N=M,M_1$ 均有：

- $(\gamma-1)N\subset UN$。
- 对每个 $v\in N$ 存在 $k\ge0$ 使 $Q^k\varphi(v)\in N$，且存在 $j\ge0$ 使 $Q^j v\in A\varphi(N)$。这里 $A\varphi(N)$ 是全部 $\varphi$ 像的 $A$-线性张成。

若存在 $a\ge0$ 使 $X^a M_1\subset M$ 及 $X^a M\subset M_1$，则 $M=M_1$。在项目里，这个先在反演 $X$ 后比较两格的条件来自另一个晶体周期比较，正文最后标出接口。

## 证明

取两格的基为行向量 $b=(b_1,\ldots,b_r)$ 和 $b_1=(b_{1,1},\ldots,b_{1,r})$。用 $M$ 的基写出矩阵 $B$ 满足 $X^ab_1=bB$。利用半线性和模 $U$ 的条件，存在矩阵 $G,G_1$ 满足

$$
\gamma(b)=bG,\qquad \gamma(b_1)=b_1G_1,\qquad G\equiv G_1\equiv I\bmod U.
$$

分别对 $X^ab_1=bB$ 作用 $\gamma$，然后额外乘 $X^a$，使两边能用 $b$ 作坐标。得到

$$
X^aG\gamma(B)=\gamma(X)^aBG_1 .
\tag{1}
$$

因为只有有限个基向量，可以把第一方向的 Frobenius 指数分别取成同一个 $h$ 和同一个 $h_1$。于是可写

$$
Q^h\varphi(b)=bF,\qquad Q^{h_1}\varphi(b_1)=b_1F_1 .
$$

相反方向，取一个共同的 $e$ 使 $Q^e$ 乘 $M_1$ 的每个基向量都进入 $A\varphi(M_1)$。半线性说明 $A\varphi(M_1)$ 就由 $\varphi(b_1)$ 张成。因此存在矩阵 $F_1'$ 满足 $\varphi(b_1)F_1'=Q^e b_1$，给出

$$
F_1F_1'=Q^{h_1+e}I.
\tag{2}
$$

再对 $X^ab_1=bB$ 作用 $\varphi$，乘 $Q^{h+h_1}X^a$。代入 $\varphi(X)=XQ$ 及基坐标，并利用乘 $X^a$ 单射，得到

$$
(Q^{h_1}F)\varphi(B)=Q^{a+h}BF_1 .
\tag{3}
$$

把 (1)–(3) 送入[矩阵逐根整除](%E6%80%8E%E6%A0%B7%E6%B2%BF%E5%88%86%E5%9C%86%E5%B1%82%E9%80%90%E6%A0%B9%E6%B6%88%E5%8E%BB%E7%9F%A9%E9%98%B5%E4%B8%AD%E7%9A%84%E5%88%86%E6%AF%8D.md)，可写 $B=X^aB_0$，其中 $B_0$ 的系数都在 $A$。由乘 $X^a$ 单射及 $X^ab_1=bX^aB_0$ 得 $b_1=bB_0$。所以 $M_1\subset M$。交换两格，利用另一方向的 $X^a$ 包含关系，可得 $M\subset M_1$。

特别地，若两格扩大到一个公共系数环 $E$ 后都给出 $\mathcal D$ 的基，且 $E\ne0$，则同秩条件自动成立。在定性余核证明中，$M$ 是目标 Wach 格，$M_1$ 是源像的双重饱和。把它们视为同一格，才能从每个向量允许不同分母得到全格的统一指数。

## Lean 对照

- `le_of_X_pow_smul_le` 从两组基写出 (1)–(3)，用各系数的整除取消 $X^a$。`main` 验证同秩并在两个方向使用这个论证。[WachModuleUniquenessCharacterisation.lean:162](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachModuleUniquenessCharacterisation.lean#L162) · [同文件:247](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachModuleUniquenessCharacterisation.lean#L247)
- 两个 $X^a$ 包含关系由 `WachFreeLatticeEqWachLatticeInvertX.main` 提供。它使用[整周期环内的晶体比较](%E4%B8%BA%E4%BB%80%E4%B9%88%E4%B8%A4%E4%B8%AAWach%E6%A0%BC%E5%8F%8D%E6%BC%94%E5%8F%82%E6%95%B0%E5%90%8E%E7%9B%B8%E5%90%8C.md)。正文展开从该条件到格相等的全部矩阵推论。[WachFreeLatticeEqWachLatticeInvertX.lean:235](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachFreeLatticeEqWachLatticeInvertX.lean#L235)

状态为源码级推导。另行未重新编译。
