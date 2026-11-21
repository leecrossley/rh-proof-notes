# Column relations bound the kernel in three types of blocks

[Chinese proof](../zh/%E5%88%97%E5%85%B3%E7%B3%BB%E6%80%8E%E6%A0%B7%E6%8E%A7%E5%88%B6%E4%B8%89%E7%B1%BB%E5%9D%97%E4%B8%8A%E7%9C%8B%E4%B8%8D%E8%A7%81%E7%9A%84%E5%90%8C%E6%80%81.md)

Take the [column relation module](column-dimension-detects-outside-representations.md) $N$ with its left ideal $Y$. Let $\mathcal O$ be a DVR with fraction field $K$ and $\ell$ nonzero and noninvertible, and take a left $A$-module $M\simeq(K/\mathcal O)^d$ over $\mathcal O$. Suppose $\delta$ acts as a nonzero $\Delta\in\mathcal O$. Set $D=\operatorname{ord}_{\mathcal O}(\Delta)$ and $e=\operatorname{ord}_{\mathcal O}(\ell)$. The module to estimate is
$$
\mathcal K=\{\phi\in\operatorname{Hom}_A(N,M):\phi|_Y=0\},
$$
where the restriction is along $Y\to N$. Let $C$ be the finite column set and $U_w=M^{D_w}$ for the twist $u(g)=\chi(g)^{-1}r(g)$, with length $b_w$. The images $a_w,b_{wj},c_w$ of $n_w,s_{wj},z_w$ determine each $\phi\in\mathcal K$ uniquely. They satisfy
$$
Ea_w=0,\quad (1-e_1)b_{wj}=0,\quad(\Delta-E)c_w=0,\qquad
(u(g)-1)a_w=\Delta\bigl(\sum_j K_{wj}(g)b_{wj}+K^*_{w0}(g)c_w\bigr)\quad(g\in D_w).
\tag{1}
$$
For $a\in\mathcal O$ nonzero, each copy of $(K/\mathcal O)[a]$ has length $\operatorname{ord}(a)$ by multiplication by $a$ and the uniformizer filtration.

## Zero block

Suppose $E=0$ on $M$, $e_1M\simeq K/\mathcal O$, and $K^*_{w0}(g)\in AE$. At each $w$ assume a lifting bound $e'_w\ge0$: if $x_j\in e_1M$ and $\sum_j K_{wj}(g)x_j$ is a twisted coboundary on $D_w$, then every $x_j$ is killed by $\ell^{e'_w}$. In (1), $\Delta c_w=0$ and the $K^*_{w0}$ term vanishes. The coboundary with coefficients $\Delta b_{wj}$ thus gives $\ell^{e'_w}\Delta b_{wj}=0$. Record the $b_{wj}$ and $c_w$. The images have length at most $j_w(ee'_w+D)+dD$ per column. In the kernel all these coordinates vanish and (1) gives $a_w\in U_w$. These $a_w$ inject the kernel into the product of the invariant modules. Hence
$$
\operatorname{length}\mathcal K\le\sum_{w\in C}\bigl(j_w(ee'_w+D)+b_w\bigr)+|C|dD.
$$

## Higher blocks

If $E=e_1=0$ on $M$ and $K^*_{w0}(g)\in AE$, then (1) gives $b_{wj}=0$, $\Delta c_w=0$, and $a_w\in U_w$. The $a_w,c_w$ give an injection into $\prod_{w\in C}(U_w\times M[\Delta])$, so the length is at most $\sum_w b_w+|C|dD$. In the application $d=1$ and the $b_w$ are bounded by the [maximum of the negative cyclotomic invariant lengths](cyclotomic-inertia-annihilates-higher-block-invariants.md).

## Block one

Suppose $u(g)=1$, $e_1=0$, $E=\Delta$ on $M$. At each $w$ assume some $g_w\in D_w$ makes $K^*_{w0}(g_w)$ act by $\ell^{e'_w}\Delta\epsilon_w$, with $\epsilon_w$ a unit. Then (1) gives $b_{wj}=0$, $\Delta a_w=0$, and at $g_w$, $\ell^{e'_w}\Delta^2\epsilon_w c_w=0$. Recording $a_w,c_w$ therefore bounds the length by $\sum_w d(ee'_w+2D)+|C|dD$. In the application $d=1$, and the unramified generator has value $1$, supplying the unit.

## Lean correspondence

- `colKer`, `colKerChiC` and `colKerChiOne` give the three bounds. [Zero block](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/ColKer.lean#L93) · [Higher blocks](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/ColKerChiOne.lean#L29) · [Block one](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/ColKerChiOne.lean#L92)
- `liftBound` proves the lifting input for the zero block from the finite local cohomology basis. [Lifting](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/CoprimeLiftBounds/CoprimeLiftProofs/LiftBound.lean#L37)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
