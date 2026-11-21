# 怎样从 Wach 模的分次与完备性取得两个算子方程

## 命题

令 $O$ 为交换环，$A$ 为交换 $O$-代数，$N$ 为 $A$-模。取参数 $X,Q\in A$，自然数 $a,k,M$。在工程中 $X$ 是分圆方向的局部参数，$Q$ 是由 Frobenius 作用产生的因子，$M$ 控制允许的 $Q$ 分母。下面两个结论分别用于 Herr 复形的两个差分算子。

1. 设 $\gamma$ 是 $N$ 上的 $O$-线性算子，对 $1\le i\le a$ 及 $n\in N$，满足 $(\gamma-u^i)X^in\in X^{i+1}N$，其中 $u\in O$。则对每个 $n\in N$，存在 $x,z\in N$ 使

$$
C_\gamma Xn=(\gamma-1)Xx+X^{a+1}z,\qquad
   C_\gamma=\prod_{i=1}^a(1-u^i).
$$

   若 $\gamma$ 关于环上的 $\gamma_A$ 半线性、$(\gamma-1)N\subset XN$ 且 $\gamma_A(X)\equiv uX\bmod X^2A$，就满足这里的分次条件。
2. 设 $N$ 包含于 $A$-模 $D$，$\varphi:D\to D$ 对 $A$ 上的 $O$-代数自同态 $\varphi_A$ 半线性。假定 $Q^M\varphi(N)\subset N$，$\varphi_A(X)=XQ^kv$，其中 $v\in A$。设 $I\subset A$ 为理想，$Q\in I,\ \varphi_A(I)\subset I$，且 $N$ 对 $I$-进拓扑完备、分离。若 $k(a+1)\ge M+1$，则 $\varphi(X^{a+1}N)\subset X^{a+1}N$，且对每个 $n\in N$，有 $z\in N$ 满足

$$
X^{a+1}n=(1-\varphi)(X^{a+1}z).
$$

## 证明

先看第一个结论。半线性情形下，$\gamma_A(X)^i\equiv u^iX^i\bmod X^{i+1}A$，且 $\gamma(n)\equiv n\bmod XN$，两式相乘就得到分次条件。在第一条结论中，这意味着在第 $i$ 层 $X^iN/X^{i+1}N$ 上，$\gamma-1$ 成为乘以 $u^i-1$。

记 $C_j=\prod_{i=1}^j(1-u^i)$，从 $C_0Xn=Xn$ 开始。若已得

$$
C_jXn=(\gamma-1)Xx+X^{j+1}m,
$$

由第 $j+1$ 层的条件，可取 $m'\in N$ 满足

$$
(1-u^{j+1})X^{j+1}m
=-(\gamma-1)X^{j+1}m+X^{j+2}m'.
$$

把前一式乘以 $1-u^{j+1}$，代入后得到同一形式，其中 $x$ 更新为 $(1-u^{j+1})x-X^jm$，余项下降到 $X^{j+2}N$。逐层做到 $j=a$ 即完成。整个过程只乘相应的差值，保住了整系数。

第二个结论中设 $b=a+1$，取 $d\ge0$ 使 $kb=M+1+d$。对 $n\in N$，定义

$$
G(n)=Q^{1+d}v^b\bigl(Q^M\varphi(n)\bigr)\in N.
$$

半线性和 $\varphi_A(X)$ 的分解给出

$$
\varphi(X^bn)=X^bG(n).
$$

若 $r\in I^j$，则 $\varphi_A(r)\in I^j$。于是 $G(rn)=\varphi_A(r)G(n)$ 属于 $I^{j+1}N$，因为 $G(n)$ 还有一个因子 $Q\in I$。所以 $G$ 把 $I^jN$ 送到 $I^{j+1}N$。对给定 $n$，级数 $z=\sum_{j\ge0} G^j(n)$ 因完备性收敛。$G$ 由过滤收缩而连续，故

$$
(1-G)z=n.
$$

再乘以 $X^b$，便得到要求的方程。

第一个结论所付的代价是 $C_\gamma$，第二个结论靠过滤收缩消去深层余项。两者在[消去 Herr 复形的二次障碍](%E6%80%8E%E6%A0%B7%E7%94%A8%E5%88%86%E6%AC%A1%E4%B8%8E%E5%A4%9A%E9%A1%B9%E5%BC%8F%E6%B6%88%E5%8E%BBHerr%E5%A4%8D%E5%BD%A2%E7%9A%84%E4%BA%8C%E6%AC%A1%E9%9A%9C%E7%A2%8D.md)中合并。

## Lean 对照

- `gammaGradedStep_holds` 从 $\gamma_A(X)$ 和 $\gamma(N)$ 的一阶形式得到各分次的标量。`gammaImageProduct_holds` 逐层乘以 $1-u^i$。[TorsionKilledCriterionHolds.lean:7](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CoboundaryTransfers/GammaStableTransfers/TorsionKilledCriterionHolds.lean#L7) · [同文件:28](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CoboundaryTransfers/GammaStableTransfers/TorsionKilledCriterionHolds.lean#L28)
- `phi_map_surjective` 把 Frobenius 写成 $X^{a+1}$ 后的收缩算子，源码解 $G(z)-z=-n$。正文直接求等价级数方程。[PhiOnto.lean:10](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/LagrangeExtensionCocycles/ExtensionCocycleProofs/PhiOnto.lean#L10)

状态为源码级推导。另行未重编译。
