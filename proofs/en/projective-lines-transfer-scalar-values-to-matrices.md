# Projective lines transfer scalar values to matrices

[Chinese proof](../zh/%E5%B0%84%E5%BD%B1%E7%9B%B4%E7%BA%BF%E6%80%8E%E6%A0%B7%E6%8A%8A%E6%A0%87%E9%87%8F%E5%8F%96%E5%80%BC%E4%BC%A0%E7%BB%99%E7%9F%A9%E9%98%B5.md)

## Statement

Let $K$ be finite, $A$ a commutative ring with $|K|=1$ in $A$, and $t:C_m(K^\times,A)\to A$ an $A$-linear functional killing bar boundaries with trivial coefficients, $m\ge1$. For each finite-dimensional $K$-space $V$ there is a linear $\theta_V:C_m(\mathrm{GL}(V),A)\to A$ killing boundaries and preserving cycle values under change of basis. For representations $\rho,\sigma$ of the same group on $V,W$, it adds the two values on every degree-$m$ cycle for $\rho\oplus\sigma$. In dimension one it gives $t$ on cycles under $\mathrm{GL}(K)=K^\times$. This is `STrans`. The construction below also yields `STheta` from the [scalar functional](discrete-logarithms-read-finite-field-prism-values.md).

## Transfer along lines

Choose a nonzero representative on every line and let $s(v)$ be the scalar expressing $v\ne0$ in its representative. For $\rho:G\to\mathrm{GL}(V)$, define $x\cdot g=[\rho(g)^{-1}v]$ and $b(g,x)=s(v)/s(\rho(g)^{-1}v)$ for $x=[v]$. This is independent of the vector on the line. On a tuple $g_1,\ldots,g_m$, take these factors successively starting from $x,x\cdot g_1,\ldots,x\cdot(g_1\cdots g_{m-1})$, giving a scalar bar tuple. Sum it over all lines to get $\mathcal T_\rho$. Dropping the first factor permutes starting lines, merging adjacent factors uses $b(gh,x)=b(g,x)b(h,x\cdot g)$, and dropping the last leaves the earlier factors unchanged. Thus $\mathcal T_\rho$ commutes with the boundary. Set $\theta_V=t\circ\mathcal T_{\rm id}$.

Changing representatives gives $b'(g,x)=u(x)^{-1}b(g,x)u(x\cdot g)$ for a function $u$ on the lines. The map $g\mapsto(b(g,\cdot),g)$ is a homomorphism into the semidirect product $(K^\times)^{\mathbb P(V)}\rtimes G$ with first coordinate product $f(x)h(x\cdot g)$. The change is conjugation there. The [prism identity](combining-conjugation-prisms-inside-a-subgroup.md) gives a difference by boundaries on cycles. The line sum on this semidirect product from first coordinates is again a chain map, so $t$ gives the same value. Transport of representatives across an isomorphism permutes lines, giving basis invariance.

For $V\oplus W$, use $s_V(v)$ if $v\ne0$ and $s_W(w)$ otherwise. There are $|K|^{\dim W}$ lines over each line with nonzero $V$ projection, each given by an arbitrary $w$ after fixing the representative of $v$. Lines contained in $W$ occur once. The ratios only use the corresponding component, so the sum is $|K|^{\dim W}\theta_V(\rho_*z)+\theta_W(\sigma_*z)$, giving additivity since $|K|=1$ in $A$. The zero-dimensional space has no lines. For $V=K$ there is one line and the assigned scalar of $g$ is $g$, yielding $t$.

## Reading the determinant

Now take $A=\mathbb Z/q\mathbb Z$, a primitive $q$th root $\zeta\in K$, $E=e+1$, $m=2E+1$, and $v:K^\times\to A$. Here $q\mid |K^\times|$ gives $|K|=1$ in $A$. Transfer the functional of the scalar proof. For scalar cyclic action $\rho_x$ by $\zeta^x$ and the standard cycle $z$, define $F_V(g)=\theta_V(\mathcal P_g((\rho_x)_*z))$. The prism is a cycle by commutation, and prism composition and vanishing on boundaries give $F_V(gg')=F_V(g)+F_V(g')$. It is invariant under basis change and adds on block diagonals. For the latter assertion the prism can be taken in the product group and then pushed under the projections and direct sum, so all use the same source cycle.

The one-dimensional value is $x^Ev(g)$, hence the value on diagonal matrices is $x^E v(\det g)$. For $q>1$, take $\lambda=\zeta\ne1$. Conjugation by the diagonal with $\lambda$ at coordinate $i$ takes $I+\frac{c}{\lambda-1}E_{ij}$ to its product with $I+cE_{ij}$. Conjugation invariance and additivity give zero on these elementary matrices, which together with invertible diagonals generate by elimination. Thus $F_V(g)=x^E v(\det g)$ for every $g$. For $q=1$ both values are zero. This gives `HasVal` and the earlier properties give `IsAdd`, together `STheta`. Reduction of integral matrices then gives `SPhi`.

## Lean correspondence

- [`STrans`, `STheta` and `SPhi`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/LemmaKOfSteps.lean#L45) specify the conclusions.
- [`tr`, `tr_bd`, `tr_cob`, `lc`, `indep` and `theta_add`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/STrans.lean) give line transfer, invariance, and the direct sum formula.
- [`fam_det` and `sThetaOf`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/SThetaOf.lean), and [`sPhi`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/PiRepApply.lean) give the prism and reduction results.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
