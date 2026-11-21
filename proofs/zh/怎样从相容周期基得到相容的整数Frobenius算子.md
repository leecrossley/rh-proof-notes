# 怎样从相容周期基得到相容的整数 Frobenius 算子

## 命题

设 $A\hookrightarrow B$ 为交换环的单射，$\varphi$ 为两环上相容的环自同态或环自同构作用中的给定幂，固定 $\mathbb Z_\ell$ 的像。令 $\tau\in A$ 在 $B$ 中为单位，$N,k\ge0$。固定非负整数 $n_1,n_2$，记 $\varphi_i=\varphi^{n_i}$，并假定每个 $\varphi_i(\tau)$ 和 $\ell$ 在 $B$ 中可逆。设 $U\in\mathrm{GL}_d(B)$，$Z,Z^*\in M_d(A)$ 满足

$$
Z=\tau^N U,\qquad
ZZ^*=Z^*Z=cI,\qquad c=\tau^{2N}\ell^{2k}.
$$

令

$$
V=\varphi_2(c)\,\varphi_1(Z)\varphi_2(Z^*),\qquad
s=\varphi_2(\tau)^{3N}\ell^{4k}\varphi_1(\tau)^N .
$$

则 $V\in M_d(A)$，$s\in A$ 在 $B$ 中为单位，且 $V\varphi_2(U)=s\varphi_1(U)$。对另一组相同 $N,k,\tau$ 的矩阵 $Z_1,Z_1^*,U_1$，定义 $V_1$ 同理。设 $P,R$ 是相应的长方矩阵，$P$ 取 $\mathbb Z_\ell$ 系数，$\varphi_i(R)=R$，且 $PZ_1-ZR$ 各项都在 $\ell^M A$。则 $VP-PV_1$ 各项也在 $\ell^M A$。算子可以在所有近似层共用同一分母 $s$。

在项目中 $A=A_{\rm cris}$、$B=B_{\rm cris}$。$U$ 是解 Galois 不变等式的周期基，$Z$ 及其整数倍逆来自有界极点的晶体框架。两个非负幂描述同一个 Weil 元素的 Frobenius 指数之差。下面展开的证明从这些已备好的周期基出发，框架存在性保留为上游输入。

## 证明

在 $B$ 中，$Z^*=cZ^{-1}$。因此

$$
V=\varphi_2(c)^2\,\varphi_1(Z)\varphi_2(Z)^{-1}.
$$

将 $Z=\tau^N U$ 代入右端，乘上 $\varphi_2(U)$ 得

$$
V\varphi_2(U)=
\varphi_2(c)^2\,\frac{\varphi_1(\tau)^N}{\varphi_2(\tau)^N}\,
\varphi_1(U)=s\varphi_1(U).
$$

最后一步用 $\varphi_2(\ell)=\ell$。$V$ 的定义只用 $A$ 中的乘法，因此在整数环内成立。整个逆运算只用于验证等式。在工程里 $Z=YQ$，$Z^*=Q'Y'$，先由 $YY'=\tau^{2N}I$、$QQ'=\ell^{2k}I$ 得 $ZZ^*=cI$。在 $B$ 中 $c$ 是单位，故 $Z^*Z=cI$ 也成立，再用单射传回 $A$。

为了比较层，记 $W=\varphi_1(Z)$、$D=\varphi_2(Z)$、$D^*=\varphi_2(Z^*)$，另一层的 $W_1,D_1,D_1^*$ 类似。记 $b=\varphi_2(c)$。Frobenius 固定 $P,R$ 并保持 $\ell$ 幂整除，所以有 $PD_1-DR\equiv0$ 与 $PW_1-WR\equiv0\pmod{\ell^M A}$。同时 $D^*D=DD^*=bI$ 且 $D_1D_1^*=bI$。用这些关系展开便有

$$
VP-PV_1=WD^*(PD_1-DR)D_1^*-b(PW_1-WR)D_1^* .
$$

两项分别含一个已经整除的矩阵，因此整个差都整除。选任意要求的 $M$，应用框架比较给相应层，便为 [晶体迹闭性](%E4%B8%BA%E4%BB%80%E4%B9%88%E4%BB%BB%E6%84%8F%E7%B2%BE%E5%BA%A6%E7%9A%84%E6%99%B6%E4%BD%93%E8%BF%B9%E8%AF%AF%E5%B7%AE%E5%BF%85%E9%A1%BB%E4%B8%BA%E9%9B%B6.md) 提供矩阵同余。

## Lean 对照

- [`OpOne2`、`LinkOp2`、`OpEx2`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/IsOp2One.lean#L23) 写出相关整数算子的接口。
- [`opOne_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/OpOneHolds.lean) 给单层算子与共同分母，[`linkOp_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/LinkOp.lean#L8) 给最后的矩阵恒等式。
- [`opEx_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/OpExHolds.lean#L72) 从整格塔的周期基相容和不分歧系数的固定性给出各层同余。本篇按发布版源码对读。
